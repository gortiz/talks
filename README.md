# Your queries are slow (and probably it's your fault)

Talk for **Commit Conf 2026** (Track 5) — Gonzalo Ortiz, StarTree.

A Reveal.js deck on why many "slow database" problems are really the developer
hiding business invariants from the query optimizer — demonstrated on Apache
Pinot with the TPC-H dataset (SF=100). Four traps: expressions that defeat
pruning, joins that should be semi-joins, co-location, and OFFSET pagination.

## Presenting

Serve over HTTP (recommended, so the speaker-notes view works reliably) and
open the deck:

```sh
python3 -m http.server 8000      # or: npx http-server -p 8000
# then open http://localhost:8000/index.html   (press S for speaker notes)
```

Opening `index.html` directly via `file://` mostly works (diagrams are
pre-rendered), but HTTP avoids speaker-view sync and local-file quirks.

## Diagrams

Mermaid diagrams are **pre-rendered to inline static SVG** to avoid first-open
flicker. To edit one:

```sh
node diagrams/prerender.mjs --unbake   # restore live <pre class="mermaid"> blocks
# edit the diagram in index.html
node diagrams/prerender.mjs            # re-bake to static SVG
```

## PDF export

```sh
(cd diagrams && node export-pdf.mjs)              # one page per slide
(cd diagrams && node export-pdf.mjs --fragments)  # one page per build step
```

## License

This repository is **dual-licensed**:

- **Slide content** — the talk text, the diagrams, and the prose — is licensed
  under [**Creative Commons Attribution 4.0 International (CC BY 4.0)**](https://creativecommons.org/licenses/by/4.0/).
  You may share, adapt, translate, and reuse it (including commercially), as
  long as you give appropriate credit.
- **Code** — the Reveal.js setup, the CSS theme, and the build tooling under
  `diagrams/` — is licensed under the [**MIT License**](./LICENSE).

Vendored dependencies keep their own licenses (reveal.js, mermaid, qrcode — MIT;
puppeteer-core — Apache-2.0). TPC-H is a public benchmark from the
[Transaction Processing Performance Council](https://www.tpc.org/tpch/).

© 2026 Gonzalo Ortiz Jaureguizar.
