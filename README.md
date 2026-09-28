# InfiniHand project website

Static site for **InfiniHand: Streaming World-Space Hand Motion Estimation from Egocentric Video**.

Serve locally with `python3 -m http.server 8765` and open http://localhost:8765.
Deploy GitHub Pages from the `main` branch, repository root. No build or external runtime service is required.

## Interactive demonstration

Seven scenes: three ARCTIC, three EgoDex and one Ego4D. One source video holds all four synchronized panels; the canvas extracts each panel and applies three adjustable boundaries. Order: Ours, ViDiHand, HaWoR, WiLoR. Boundaries support pointer, touch and arrow-key input.

World-space playback uses the same video clock, samples meshes at 3 Hz, and retains up to seven samples. Latest geometry is darkest. The viewer supports orbit/zoom and switches between Ours and HaWoR. Geometry is loaded only for the selected scene; switching cancels pending loads and disposes GPU meshes.

These visualization meshes use a **shared reference camera trajectory** (ARCTIC/EgoDex dataset cameras, Ego4D scaled SLAM), not each method's independently predicted trajectory. Ours uses GT boxes for ARCTIC/EgoDex and SAM3 boxes for Ego4D. This protocol is documented here and in the mesh metadata. It is not a Table 2 native world-space evaluation.

Ours web meshes were exported with Blender Catmull-Clark subdivision level 1. Web playback uses Three.js/WebGL, not Cycles. The source offline scenes use Cycles 128 samples. Position quantization bounds, validity and sample frame IDs are stored in each `assets/world/*/mesh.json`.

## Provenance

Title, author order, affiliations, and figures were read from the author-provided Overleaf project on 2026-09-28. No corresponding-author marks were added because none were present in that source.

Prediction throughput 11.19 FPS / 2.04× HaWoR refers to inference excluding asynchronous sparse BA.

Original website implementation, with visual direction inspired by GeoVerse and AHa-3D (links in footer). Three.js is distributed under MIT; see `assets/vendor/THREE-LICENSE.txt`. Research figures, video, and mesh assets retain their respective source rights.
