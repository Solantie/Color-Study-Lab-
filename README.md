# Color Study Lab 🎨

**A collection of browser-based color perception exercises for artists and curious learners.**

Color Study Lab started as a personal project: I wanted a simple way to practice judging hue, saturation, brightness, and tonal values without opening a full painting application. It currently includes three experimental training modules that run locally in a web browser.

> **Status:** Work in progress / personal learning project. The exercises are usable prototypes, not scientifically validated assessments of color perception or drawing ability.

**Language:** [English](README.md) | [简体中文](README.zh-CN.md)

**Website:** [Choose language](index.html) · [English](en/index.html) · [中文](zh/index.html)

## Try it

- **[HSB Trainer](en/apps/hsb-trainer.html)** — Match randomly generated colors using Hue, Saturation, and Brightness sliders. Includes single- and two-color modes, perceptual OKLab scoring, optional weighted HSB scoring, and target markers shown after checking.
- **[Value Trainer](en/apps/value-trainer.html)** — Upload an image and convert it into **2–12 grayscale levels**. Estimate each level with a brightness slider, then reveal the target values and errors.
- **[Photo Color Study](en/apps/photo-color-study.html)** — Upload a photo or illustration, reduce it to **2–12 representative color groups**, and recolor those groups with HSB sliders. Compare your result with the simplified reference image.

If GitHub Pages is enabled, open the [project homepage](index.html) to launch each exercise. Otherwise, download or clone the repository and open any HTML file under `en/apps/` or `zh/apps/` in a modern browser.

## Features at a glance

| Module | Input | Core exercise | Feedback |
| --- | --- | --- | --- |
| HSB Trainer | Random colors | Adjust H, S, B sliders | OKLab / weighted HSB scores and target markers |
| Value Trainer | Example or uploaded image | Match grayscale values for 2–12 levels | Per-level targets, errors, and overall score |
| Photo Color Study | Example or uploaded image | Recolor 2–12 clustered regions | Per-region and area-weighted scores |

### Photo Color Study algorithms

The photo exercise currently offers four color quantization options:

1. **RGB K-Means:** cluster colors in RGB space and use cluster mean colors.
2. **OKLab K-Means:** cluster in a perceptual color space and use converted cluster centers.
3. **Representative Colors:** cluster in OKLab and pick source-image colors near the cluster centers.
4. **Vivid Priority:** weight more chromatic pixels more heavily during clustering and choose representative source colors.

These are experimental **color grouping** algorithms, not semantic image segmentation. Complex artworks can produce fragmented regions or lose important details when reduced to a small palette.

## Repository structure

```text
color-study-lab/
├── index.html                 # Language selection page
├── README.md                  # English documentation
├── README.zh-CN.md            # Chinese documentation
├── .gitignore
├── zh/                         # Chinese-language website
│   ├── index.html
│   └── apps/                   # Three Chinese-language exercises
└── en/                         # English-language website
    ├── index.html
    └── apps/                   # Three English-language exercises
```

Each exercise is a **standalone HTML file** containing its own HTML, CSS, and JavaScript. There is no build step, backend, or account system.

## Run locally

1. Clone or download this repository.
2. Open `index.html` in a modern desktop or mobile browser.
3. Choose a training module.

The exercises perform color calculations and image processing client-side. Uploaded images are processed in your browser and are not sent to a server by this project.

## GitHub Pages

To publish a playable version:

1. Open your GitHub repository → **Settings → Pages**.
2. Under **Build and deployment**, select **Deploy from a branch**.
3. Select your default branch and the **/(root)** folder, then save.
4. Once deployment finishes, use the GitHub Pages URL displayed in the Pages settings.

All links in `index.html` are relative, so the homepage works under a repository-specific GitHub Pages path.

## Implementation notes

- **HSB/HSV** is the editing model used by the color sliders. HSV brightness is not the same as perceptual lightness.
- **OKLab** is used to compare colors perceptually. The numerical conversion into a 0–100 score is a custom heuristic for practice, not a standardized psychophysical metric.
- **Value Trainer** uses sRGB-weighted grayscale values and divides them into equal-width intervals before estimating each interval's average gray value. Its grayscale scale is not CIELAB L*.
- **Photo Color Study** uses K-Means-style color grouping. It does not identify objects or artistic lighting structure.

## Roadmap

- [ ] Improve grayscale/region selection and mobile interaction
- [ ] Compare alternative scoring and perceptual lightness metrics
- [ ] Add progress tracking for repeated exercises
- [ ] Refine palette extraction for complex illustrations
- [ ] Explore daily challenges and shareable results

## Motivation

The goal is to make short, repeatable color studies accessible on a phone or laptop. This repository documents the experiments as they evolve, including approaches that work well on simple images and approaches that need more research.

## License

MIT License
