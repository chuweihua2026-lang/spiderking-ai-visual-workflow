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
  -> product recognition (product_recognition.json)
      -> consumer profile (consumer_profile.json)
          -> persona selection (persona_selection.json)
              -> clothing styling
                  -> shoe, bag, and accessory styling (commercial_styling_decision.json)
                      -> scene selection (commercial_scene_decision*.json)
                          -> commercial photography generation
                              -> spiderking-product-vision.render
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

- Product-only white-background images obey: `商品识别 -> 结构一致性分析 -> 角度与数量规划 -> 白底商业化生成 -> 一致性质检`.
- Model, lifestyle-scene, advertising, and scenario-storytelling images obey: `商品识别 -> 消费者画像 -> 人物选择 -> 服装搭配 -> 鞋包搭配 -> 场景选择 -> 商业摄影生成`.
- The commercial-image stages may not be reordered, merged, or skipped. Product-only renders do not create consumer, persona, styling, or scene files filled with `not_applicable`.
- Preserve the strict stage order: product recognition -> consumer profile -> persona selection -> clothing styling -> shoe-bag-accessory styling -> scene selection -> commercial photography -> final layout.
- Product recognition runs before any consumer, person, outfit, bag, accessory, or scene decision and does not require image generation.
- Keep `product_recognition.json`, `consumer_profile.json`, and `persona_selection.json` as separate approved audit artifacts.
- Every image-generation or image-editing call requires an approved `commercial_styling_decision.json` from `spiderking-commercial-visual-stylist`.
- Every image that creates or changes an environment requires an approved `commercial_scene_decision.json` from `spiderking-commercial-scene-director`.
- Scene selection follows product -> consumer -> use context -> brand feeling -> space -> time/light -> action -> camera.
- Every human subject is selected through the built-in persona database using product price band, target consumer, purchase decision-maker, actual user, and use scene; the workflow does not default to the youngest or most attractive model.
- Complete person, brand, product, scene, clothing, footwear, bag, accessories, color, material, pose, camera, and commercial checks before model-image generation.
- Product function controls the scene and outfit before fashion decoration; specialized outdoor, trail, business, or other footwear must not be reduced to generic sports styling.
- Clothing styling uses the standard outfit reference library at `/Users/chuchu/Desktop/素材库/穿搭参考图/标准化档案库` when available. It reads `穿搭参考库索引.csv` and selects by image content, product function, consumer, season, scene, and silhouette rather than trusting filenames.
- Outfit boards are reference-only. The workflow may extract silhouette, layering, material, color, bag, and accessory logic, but may not paste or reproduce the reference person, pose, text, logo, background, reference shoe, or complete outfit.
- Each generated model image records a unique outfit reference ID; the three 9:16 images may not reuse one reference board or merely recolor one silhouette.
- Preserve the input shoe one-to-one across every generated image.
- Product structure, colors, materials, stitching, logo, laces, decorative details, and proportions must not change.
- The SpiderKing logo must use the uploaded asset and must not be redrawn or replaced.
- If image generation is uncertain, prioritize product consistency over visual drama.
- Final layout should preserve approved upstream image quality and avoid unnecessary redraws.
