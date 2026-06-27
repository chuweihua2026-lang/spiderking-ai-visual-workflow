# SpiderKing AI Visual Workflow

SpiderKing AI Visual Workflow is a modular Codex Skill workflow for shoe marketing visual production.

## Goal

Input 1 to 3 product shoe images and output two final brand-card templates:

- Template A: left-right business card layout.
- Template B: approved vertical integrated card layout.

All image generation must use ChatGPT image generation only. Do not use Midjourney, Stable Diffusion, ComfyUI, or other image models.

## Workflow

```text
shoe_images
  -> spiderking-product-vision
      -> spiderking-copywriting
      -> spiderking-styling-engine
      -> spiderking-selling-points
          -> spiderking-layout-engine
              -> final_brand_card_template_a.png
              -> final_brand_card_template_b.png
```

## Skills

- `spiderking-brand-card-workflow`: master parallel workflow orchestrator.
- `spiderking-product-vision`: product three-view visual assets and extracted shoe attributes.
- `spiderking-copywriting`: 3:2 main poster with model, logo, title, selling points, and new-arrival badge.
- `spiderking-styling-engine`: three separate 9:16 standing model scene images.
- `spiderking-selling-points`: 27:18 selling-points board with visual, functional, and scenario sections.
- `spiderking-layout-engine`: final integration layout, outputting Template A and Template B.

## Usage

In Codex, invoke:

```text
@spiderking-brand-card-workflow
```

Then provide 1 to 3 shoe product images and optional product direction.

## Core Rules

- Preserve the input shoe one-to-one across every generated image.
- Product structure, colors, materials, stitching, logo, laces, decorative details, and proportions must not change.
- The SpiderKing logo must use the uploaded asset and must not be redrawn or replaced.
- If image generation is uncertain, prioritize product consistency over visual drama.
- Final layout should preserve approved upstream image quality and avoid unnecessary redraws.
