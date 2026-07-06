# Parameter-preserving Real-time BIM Rendering via Direct GPU Ray Tracing

Project page for the paper **"Parameter-preserving Real-time BIM Rendering via Direct GPU Ray Tracing"**, published in *Computer Animation and Virtual Worlds* (CAVW) and presented at **CASAXR 2026**.

🔗 **Paper:** [10.1002/cav.70159](http://dx.doi.org/10.1002/cav.70159)

## Authors

- [Donggyu Lee](https://tony7078.github.io)<sup>1*</sup>
- Jaehyuk Lim<sup>1*</sup>
- Junghyun Han<sup>1†</sup>
- Seung-wook Kim<sup>2†</sup>

<sup>1</sup>Korea University &nbsp;&nbsp; <sup>2</sup>Hankuk University of Foreign Studies
<br><sup>*</sup>Equal contribution &nbsp;&nbsp; <sup>†</sup>Corresponding authors

## Abstract

Current BIM visualization systems tessellate parametric geometry into triangle meshes before rendering, which increases memory usage, introduces faceting on curved surfaces, and adds significant export-time overhead.

We present an end-to-end system that preserves parametric shape definitions from BIM models through to GPU ray tracing, bypassing mesh conversion for supported parametric shapes. Our exporter extracts parametric shapes from a BIM authoring tool and encodes them into a compact binary format with two-tier caching to avoid redundant extraction. Our renderer maps preserved BIM primitives to an instanced GPU scene layout and performs direct ray-primitive intersections, with mixed-precision parameter encoding and ray advancement improving memory efficiency and numerical robustness.

Evaluation on architectural projects shows that our system achieves a lower GPU memory footprint, produces mathematically exact curved surfaces free of tessellation artifacts, and exports models faster than standard workflows.

## Highlights

- **Parameter preservation** — parametric shapes flow from BIM extraction to GPU rendering without mesh conversion.
- **Compact exporter** — classifies each BIM face by surface type, extracts mathematical parameters, applies two-tier caching, and writes a compact binary file.
- **Direct GPU ray tracing** — builds OptiX acceleration structures and uses per-shape-type custom intersection programs for direct ray-primitive intersection.
- **Ray advancement** — advancing the ray to the AABB entry point improves numerical conditioning and reduces average frame time from 2.71 ms to 1.63 ms.
- **Exact curved surfaces** — mathematically exact surfaces free of tessellation faceting, with a lower GPU memory footprint.

## About this repository

This repository contains the static web page for the project. It is a single self-contained `index.html` with supporting assets, and can be hosted directly on GitHub Pages or any static file server.

```
.
├── index.html            # Project page (structure, styles, scripts)
└── static
    ├── css/              # Bulma, Font Awesome, custom styles
    ├── js/               # Font Awesome scripts
    ├── images/           # Overview figure, ray-advancement figures, qualitative results
    └── videos/           # Revit vs. Ours comparison videos (4 scenes)
```

## Local preview

The page is fully static — just serve the directory and open it in a browser:

```bash
# Python
python -m http.server 8000

# or Node
npx serve .
```

Then visit `http://localhost:8000`.

## Citation

```bibtex
@article{lee2026parameter,
  author    = {Lee, Donggyu and Lim, Jaehyuk and Han, Junghyun and Kim, Seung-wook},
  title     = {Parameter-preserving Real-time BIM Rendering via Direct GPU Ray Tracing},
  journal   = {Computer Animation and Virtual Worlds},
  volume    = {37},
  number    = {4},
  year      = {2026},
  doi       = {10.1002/cav.70159},
}
```

## Acknowledgements

The webpage template is adapted from [Nerfies](https://github.com/nerfies/nerfies.github.io), under a [CC BY-SA 4.0 License](http://creativecommons.org/licenses/by-sa/4.0/).
