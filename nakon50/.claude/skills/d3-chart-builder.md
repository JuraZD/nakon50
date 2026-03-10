# Skill: D3 Chart Builder

## Zadatak
Generiraj kompletan D3.js grafikon s Hugo shortcodeom, podacima i stilovima.
Output mora biti spreman za umetanje u post bez ikakvih dodatnih izmjena.

## Input (dobivam od /build-d3-chart)
- `chart_type`, `title`, `context`, `target_post_path`
- `data_inline` ili `data_csv_path`
- `color_scheme`, `caption`, `interactive`, `responsive`

## Nakon50 Color Palette

```css
:root {
  --n50-primary:   #2C5F8A;  /* bar fill, linije, aktivni elementi */
  --n50-secondary: #E8913A;  /* hover, accent, highlight */
  --n50-neutral:   #6B7280;  /* osi, tick labelovi, grid */
  --n50-bg:        #F7F5F0;  /* pozadina grafikona */
  --n50-text:      #1F2937;  /* naslovi, labeli */
  --n50-grid:      #E5E7EB;  /* grid linije */
  --n50-white:     #FFFFFF;  /* tooltip pozadina */
}
```

## Generiranje po chart_type

---

### BAR chart (horizontalni za dulje labele, vertikalni za kraće)

```javascript
// chart.js — bar
const N50 = {
  primary: '#2C5F8A', secondary: '#E8913A',
  neutral: '#6B7280', bg: '#F7F5F0',
  text: '#1F2937', grid: '#E5E7EB'
};

async function renderChart(containerId, dataPath) {
  const data = await d3.json(dataPath);
  const container = document.getElementById(containerId);
  const margin = {top: 20, right: 30, bottom: 60, left: 120};
  const width = container.clientWidth - margin.left - margin.right;
  const height = Math.max(300, data.length * 45) - margin.top - margin.bottom;

  const svg = d3.select(`#${containerId}`)
    .append('svg')
    .attr('width', width + margin.left + margin.right)
    .attr('height', height + margin.top + margin.bottom)
    .append('g')
    .attr('transform', `translate(${margin.left},${margin.top})`);

  // Background
  svg.append('rect')
    .attr('width', width).attr('height', height)
    .attr('fill', N50.bg).attr('rx', 4);

  // Skale
  const x = d3.scaleLinear()
    .domain([0, d3.max(data, d => d.value) * 1.1])
    .range([0, width]);

  const y = d3.scaleBand()
    .domain(data.map(d => d.label))
    .range([0, height])
    .padding(0.3);

  // Grid linije
  svg.append('g').attr('class', 'grid')
    .call(d3.axisBottom(x).tickSize(height).tickFormat(''))
    .attr('stroke', N50.grid).attr('stroke-opacity', 0.7)
    .select('.domain').remove();

  // Bars
  const bars = svg.selectAll('.bar')
    .data(data).enter().append('rect')
    .attr('class', 'bar')
    .attr('x', 0).attr('y', d => y(d.label))
    .attr('width', d => x(d.value))
    .attr('height', y.bandwidth())
    .attr('fill', N50.primary)
    .attr('rx', 3);

  // Hover efekt
  if ({interactive}) {
    const tooltip = d3.select('body').append('div')
      .attr('class', 'n50-tooltip')
      .style('opacity', 0);

    bars
      .on('mouseover', (event, d) => {
        d3.select(event.currentTarget).attr('fill', N50.secondary);
        tooltip.transition().duration(200).style('opacity', 1);
        tooltip.html(`<strong>${d.label}</strong><br>${d.value}${d.unit || ''}`)
          .style('left', (event.pageX + 10) + 'px')
          .style('top', (event.pageY - 28) + 'px');
      })
      .on('mouseout', (event) => {
        d3.select(event.currentTarget).attr('fill', N50.primary);
        tooltip.transition().duration(200).style('opacity', 0);
      });
  }

  // Value labeli
  svg.selectAll('.label')
    .data(data).enter().append('text')
    .attr('class', 'label')
    .attr('x', d => x(d.value) + 5)
    .attr('y', d => y(d.label) + y.bandwidth() / 2)
    .attr('dy', '0.35em')
    .attr('fill', N50.text)
    .style('font-size', '13px')
    .text(d => `${d.value}${d.unit || '%'}`);

  // Y osa (labeli)
  svg.append('g')
    .call(d3.axisLeft(y))
    .select('.domain').remove();

  svg.selectAll('.tick line').remove();
  svg.selectAll('.tick text')
    .attr('fill', N50.text)
    .style('font-size', '13px');
}
```

---

### LINE chart

```javascript
// chart.js — line (trend kroz vrijeme)
async function renderChart(containerId, dataPath) {
  const data = await d3.json(dataPath);
  // data format: [{date: "2026-01", value: 45}, ...]

  const container = document.getElementById(containerId);
  const margin = {top: 20, right: 40, bottom: 50, left: 60};
  const width = container.clientWidth - margin.left - margin.right;
  const height = 300 - margin.top - margin.bottom;

  const svg = d3.select(`#${containerId}`)
    .append('svg')
    .attr('width', width + margin.left + margin.right)
    .attr('height', height + margin.top + margin.bottom)
    .append('g')
    .attr('transform', `translate(${margin.left},${margin.top})`);

  const parseDate = d3.timeParse('%Y-%m');

  const x = d3.scaleTime()
    .domain(d3.extent(data, d => parseDate(d.date)))
    .range([0, width]);

  const y = d3.scaleLinear()
    .domain([0, d3.max(data, d => d.value) * 1.1])
    .range([height, 0]);

  // Gradient ispod linije
  const gradient = svg.append('defs').append('linearGradient')
    .attr('id', 'area-gradient')
    .attr('gradientUnits', 'userSpaceOnUse')
    .attr('x1', 0).attr('y1', y(0))
    .attr('x2', 0).attr('y2', y(d3.max(data, d => d.value)));

  gradient.append('stop')
    .attr('offset', '0%').attr('stop-color', '#2C5F8A').attr('stop-opacity', 0);
  gradient.append('stop')
    .attr('offset', '100%').attr('stop-color', '#2C5F8A').attr('stop-opacity', 0.15);

  // Area
  const area = d3.area()
    .x(d => x(parseDate(d.date)))
    .y0(height).y1(d => y(d.value))
    .curve(d3.curveCatmullRom);

  svg.append('path').datum(data)
    .attr('fill', 'url(#area-gradient)')
    .attr('d', area);

  // Linija
  const line = d3.line()
    .x(d => x(parseDate(d.date)))
    .y(d => y(d.value))
    .curve(d3.curveCatmullRom);

  svg.append('path').datum(data)
    .attr('fill', 'none')
    .attr('stroke', '#2C5F8A')
    .attr('stroke-width', 2.5)
    .attr('d', line);

  // Točke
  svg.selectAll('.dot')
    .data(data).enter().append('circle')
    .attr('cx', d => x(parseDate(d.date)))
    .attr('cy', d => y(d.value))
    .attr('r', 5)
    .attr('fill', '#2C5F8A')
    .on('mouseover', (event, d) => {
      d3.select(event.currentTarget).attr('fill', '#E8913A').attr('r', 7);
    })
    .on('mouseout', (event) => {
      d3.select(event.currentTarget).attr('fill', '#2C5F8A').attr('r', 5);
    });

  // Osi
  svg.append('g').attr('transform', `translate(0,${height})`).call(d3.axisBottom(x));
  svg.append('g').call(d3.axisLeft(y));
}
```

---

## CSS (style.css — jednaki za sve tipove)

```css
.n50-chart-wrapper {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  background: #F7F5F0;
  border-radius: 8px;
  padding: 24px;
  margin: 32px 0;
}

.n50-chart-title {
  font-size: 16px;
  font-weight: 600;
  color: #1F2937;
  margin: 0 0 4px;
}

.n50-chart-caption {
  font-size: 12px;
  color: #9CA3AF;
  margin: 8px 0 0;
  font-style: italic;
}

.n50-tooltip {
  position: absolute;
  padding: 8px 12px;
  background: #ffffff;
  border: 1px solid #E5E7EB;
  border-radius: 6px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
  font-size: 13px;
  color: #1F2937;
  pointer-events: none;
}

/* Responsive */
@media (max-width: 600px) {
  .n50-chart-wrapper { padding: 16px; }
}
```

---

## Hugo Shortcode (layouts/shortcodes/d3chart.html)

```html
{{- $id := .Get "id" | default (printf "chart-%d" (now.UnixNano)) -}}
{{- $src := .Get "src" -}}
{{- $title := .Get "title" -}}
{{- $caption := .Get "caption" | default "" -}}

<div class="n50-chart-wrapper">
  {{- with $title }}
  <p class="n50-chart-title">{{ . }}</p>
  {{- end }}
  <div id="{{ $id }}"></div>
  {{- with $caption }}
  <p class="n50-chart-caption">{{ . }}</p>
  {{- end }}
</div>

<link rel="stylesheet" href="{{ $src }}style.css">
<script src="https://cdn.jsdelivr.net/npm/d3@7/dist/d3.min.js"></script>
<script>
  (function() {
    const src = '{{ $src }}';
    const id = '{{ $id }}';
    const script = document.createElement('script');
    script.src = src + 'chart.js';
    script.onload = () => renderChart(id, src + 'data.json');
    document.head.appendChild(script);
  })();
</script>
```

## Output fajlovi

Generira u `{target_post_path}charts/{auto-slug}/`:
- `chart.js` — D3 logika za odabrani chart_type
- `data.json` — podaci (konvertirani iz data_inline ili data_csv_path)
- `style.css` — Nakon50 stilovi

Generira ako ne postoji: `layouts/shortcodes/d3chart.html`

U terminal ispiše gotov shortcode poziv za umetanje u post.
