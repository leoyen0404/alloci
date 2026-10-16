---
title: lloci room
emoji: 🔦
colorFrom: indigo
colorTo: blue
sdk: static
app_file: index.html
pinned: false
license: apache-2.0
short_description: Type what you're looking for; it glows in a 3D scan.
---

# lloci: find things in a 3D room scan

Type a description ("a bottle", "the teddy", "slippers") and the matching object glows in a
Gaussian-splat scan of a room. Everything runs in your browser:

- **Search model:** EmbeddingGemma 2 text encoder, 4-bit ONNX via transformers.js
  (`onnx-community/embeddinggemma-2-ONNX`, ~207 MB, downloaded once and cached).
- **Index:** 2,325 object crops from the photos, embedded with EmbeddingGemma 2 (256-d, int8).
- **Aura:** precomputed crop → 3D-cluster table; a query sums the best crops' clusters and recolours the splat.
- **Rendering:** [Spark](https://sparkjs.dev) (three.js), 1.1M splats.

Scene: "room" from the Mip-NeRF 360 dataset (Barron et al.), used for research/demo purposes.

Works best in a recent desktop Chrome/Edge/Safari with WebGPU; falls back to WebAssembly (slower).
First visit downloads ~270 MB in total (splat + model).
