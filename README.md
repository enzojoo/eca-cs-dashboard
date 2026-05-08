# CS Operations Dashboard (Demo)

A static, single-page CS operations dashboard built with vanilla HTML + Chart.js.
All numbers in `data.json` are synthetic — this repo demonstrates layout, chart
types, and interaction patterns only.

## Live

https://enzojoo.github.io/eca-cs-dashboard/

## Layout

- **KPI cards** — IB / OB ticket totals, agent NPS, latest chatbot NPS
- **Tab: 인입 현황** — daily stacked bar (IB/OB filter), channel mix doughnut
- **Tab: 챗봇** — chatbot flow stacked bar + resolution-rate line, daily NPS combo
- **Tab: NPS** — daily NPS combo, department NPS bar, dept × channel heatmap (clickable)
- **Tab: 문의유형** — top 20 inquiry types horizontal bar

## Run locally

```bash
python3 -m http.server 8080
# open http://localhost:8080
```

A simple HTTP server is required because the page fetches `./data.json`.

## Update data

Replace `data.json` keeping the same shape. Sections:

- `meta` — title, periods, last updated
- `channelDaily` — `{date, io, channel, tickets}`
- `channelMix` — `{io, channel, tickets, ratio}`
- `chatbotResolution` — `{date, botSolved, botToAgent, agentDirect, ibTotal, totalSolveRate, botInflowRate, chatSolveRate}`
- `chatbotNps` — `{date, promote, neutral, detract, responses, nps}`
- `topInquiryTypes` — `{io, channel, type, tickets, ratio}`
- `deptChannelNps` — `{dept, channel, promote, neutral, detract, responses, nps}`
- `npsDaily` — `{date, promote, neutral, detract, responses, nps}`
- `deptNps` — `{dept, promote, neutral, detract, responses, nps}`

## Stack

- Vanilla HTML / CSS / JS (no build step)
- [Chart.js 4.4](https://www.chartjs.org/) via CDN
