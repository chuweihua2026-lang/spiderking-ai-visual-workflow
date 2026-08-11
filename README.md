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
  -> spiderking-commercial-visual-stylist (mandatory pre-generation gate)
      -> spiderking-product-vision
          -> commercial styling revalidation
              -> spiderking-commercial-scene-director (for every environment image)
                  -> spiderking-copywriting
                  -> spiderking-styling-engine
                  -> spiderking-selling-points
                      -> spiderking-layout-engine
                          -> final_brand_card_template_a.png
                          -> final_brand_card_template_b.png
```

## Skills

- `spiderking-brand-card-workflow`: master parallel workflow orchestrator.
- `spiderking-commercial-visual-stylist`: mandatory senior stylist and visual-director analysis before any image generation.
- `spiderking-commercial-scene-director`: mandatory product-led scene, light, space, action, and camera direction before environment generation.
- `spiderking-product-vision`: product three-view visual assets and extracted shoe attributes.
- `spiderking-scene-engine`: product-function-led lifestyle scene selection.
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

- Every image-generation or image-editing call requires an approved `commercial_styling_decision.json` from `spiderking-commercial-visual-stylist`.
- Every image that creates or changes an environment requires an approved `commercial_scene_decision.json` from `spiderking-commercial-scene-director`.
- Scene selection follows product -> consumer -> use context -> brand feeling -> space -> time/light -> action -> camera.
- Every human subject is selected through the built-in persona database using product price band, target consumer, purchase decision-maker, actual user, and use scene; the workflow does not default to the youngest or most attractive model.
- Complete person, brand, product, scene, clothing, footwear, bag, accessories, color, material, pose, camera, and commercial checks before model-image generation.
- Product function controls the scene and outfit before fashion decoration; specialized outdoor, trail, business, or other footwear must not be reduced to generic sports styling.
- Preserve the input shoe one-to-one across every generated image.
- Product structure, colors, materials, stitching, logo, laces, decorative details, and proportions must not change.
- The SpiderKing logo must use the uploaded asset and must not be redrawn or replaced.
- If image generation is uncertain, prioritize product consistency over visual drama.
- Final layout should preserve approved upstream image quality and avoid unnecessary redraws.
