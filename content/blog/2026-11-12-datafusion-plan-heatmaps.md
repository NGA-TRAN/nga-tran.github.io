---
title: "DataFusion metrics: see the hot spots"
description: Plan Visualizer now colors operators by runtime metrics. Switch between compute time, output bytes, and other metrics to see what stands out.
pubDate: 2026-11-12
type: note
tags:
  - DataFusion
  - Query Planning
  - Query Performance
  - App
ogImage: diagrams/plan-visualizer/elapsed-compute-heatmap.png
app: plan-visualizer
---

In my [earlier post](/blog/datafusion-plan-visualizer/), I introduced Plan Visualizer for drawing DataFusion physical plans. It now supports **heatmaps for runtime metrics**: color operators by a selected metric, such as compute time, output bytes, row counts, memory usage, and more.

Paste a plan with metrics, such as `EXPLAIN ANALYZE` output, select **Labels + heatmap**, and choose a metric. Here is a synthetic sample colored by compute time:

<figure class="plan-figure plan-demo">
  <a href="/diagrams/plan-visualizer/elapsed-compute-heatmap.png">
    <img src="/diagrams/plan-visualizer/elapsed-compute-heatmap.png" alt="Compute-time heatmap: the hash join has the strongest orange fill, reporting 45 ms, followed by the orders scan at 18 ms." />
  </a>
  <figcaption>elapsed_compute: the hash join stands out at 45 ms.</figcaption>
</figure>

Switch metrics to see different operators stand out. In the orange palette, stronger color means a larger reported value. Each metric has its own scale. **Not reported** means missing data, not zero; operator compute times are not the query's wall-clock time.

Try [this sample plan][sample] or paste your own into [Plan Visualizer](https://nga-tran.github.io/plan-visualizer/). Heatmaps are also available in the [plan-viz library](https://www.npmjs.com/package/plan-viz) ([release notes](https://github.com/NGA-TRAN/plan_viz/blob/master/CHANGELOG.md)).

[sample]: https://nga-tran.github.io/plan-visualizer/#plan=v2.H4sIAAAAAAACE61VbW_aMBD-K6d8AintkkAZQ4pE1xetK5oq0X3KUOQmR-ousTPb6UAV_32XBGgJFLpufCH22b7n5Xx-svKUCWtgjaUyFzOMBnAr8-vWFE1077tO2wac5coPpIpR6aEL5xfjM_j2fTQaw-h0fGuDwoRLMXTgdCMwsSFXqFE9YpgzZbihVVwkfjBlqUYKZ2gUj7QfYMpyjXEYySwvDPpupm2QhaFBqORvTTjW4ztGwJCmnmfmphz3HPg8-SEAbpR8wKjMVvOp8a9RMr1EbEMkC2FaV8L0ui233SZyFKyJ7oPniAY87zC8jreCB3CaJISAGazxZTJG_5ILltqQ3M13QSU0jDb5QQPxPpRe9k6U5Buyn2GGWVjQgX7_2IFrmtU5T9OwQuA7yyHlq3dW-1ZTVTpnyRbgTLIUdYQ3qyrQJfFVdLce1dr_rEi_qUhnWxGvoUi3v0ORXvdfJSl_X5i-_yq5eMH6TNLiyIxwamx4oFho5jn6V0KgImDCD1pRoY3MUIU8HlLKjWG7unOr6l_L5u4TpXuyddlOHOewMK5HqyqKdwVP42dxXK8umA2uAJc8NahqrozwPeLQAx-MKnATdIPgWzh4uygcLHavWxFo4AQ4Z4aNZaGiZT1OeYphomSRa__JheprAEEw5TNTUIf7sEL84uuYOt6vAs1ksniVnb3uQ7UexLBKVVm-3L-HdGf7fr-BdGcn6ZfmaMNMUTZ6H8pUKRqM9zi0z5feli_9XRi7zdLqvscZr3ZGb1hTN_Pl35GztsWG19a4b7OuVukvLXO3OlBVgwcF6fTXgli2pdEYeke1NXiyYq7p_Z7T-32PzGQsp3idnqYa6SmUUyM29DWwpGIiKae4IOfpoSY-xLI8s95Pr2hJjZbGpPq00BQ9-tjvnbidT9bCtlhBYtCe6KpxQHmjF4s_qPy2wVgIAAA
