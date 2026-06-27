---
name: spiderking-copywriting
description: >-
  Generate the 3:2 horizontal main poster for SpiderKing shoe marketing, including Chinese
  ecommerce poster copy, a young Chinese female model wearing the shoes, logo
  placement guidance, new-arrival badge text, and 3 to 5 selling points. Use
  after product, scene, and styling context exists. All image generation must use
  ChatGPT image generation only.
---

# SpiderKing Copywriting Main Poster

Use this Skill after Product Vision, Scene Engine, and Styling Engine are available. This Skill owns the main poster image, not only the copy.

## Built-In Brand Asset

- SpiderKing logo: `assets/spiderking-logo.jpg`
- Use this uploaded logo by default. Do not redraw, replace, stylize, or invent the logo.

## Required Input

- `shoe_attributes.json`
- `scene_spec.json`
- Optional `styling_spec.json`; if missing, create styling from product style, scene, and selling points.
- Optional `brand_logo`; default to `assets/spiderking-logo.jpg`.
- `shoe_reference`: original shoe image or validated Product Vision output.
- Optional `product_hint`: product name, launch theme, or campaign direction.

## Hard Rules

- Main poster aspect ratio must be `3:2` horizontal.
- Main visual must be a young Chinese female model wearing the input shoes.
- Use ChatGPT image generation only for the poster image. Do not use Midjourney, Stable Diffusion, ComfyUI, or other image models.
- Attach or reference the original shoe image for every poster generation.
- Preserve the shoe one-to-one: shoe shape, upper structure, sole, colors, materials, logo, stitching, laces, decorations, and proportions must not change.
- Use the uploaded SpiderKing logo asset. Do not redraw, replace, stylize, or invent the logo.
- Prioritize shoe consistency over decorative impact if the image generation is uncertain.
- Avoid text or model clothing covering the shoes.

## Poster Direction

- Composition: 3:2 horizontal commercial ecommerce poster.
- Subject: Chinese young female model, natural sweet style, realistic body proportions, wearing the product shoes clearly.
- Framing: full-body or 3/4 body framing, shoes visible and not cropped.
- Scene: choose the most representative scene from product style, try-on context, and selling points. Do not choose randomly.
- Styling: match the outfit to this shoe style, scene, and selling points. The outfit must support the shoes and not overpower them.
- Accessories: automatically add style-consistent details such as jewelry, hair accessories, necklace, brooch, charms, earrings, bracelet, or other small decorative elements.
- Bag: automatically match a style-consistent bag such as crossbody bag, handbag, shoulder bag, underarm bag, tote, or mini bag.
- Copy: include one selling-point-driven main title, important shoe selling points, and a `新款上市` style badge.
- Logo: place the uploaded SpiderKing logo in the upper-left safe area, preserving original ratio.
- Typography: text font and visual style must match the poster mood. Keep text crisp, commercial, and not overcrowded.

## Workflow

1. Read product, scene, styling, logo, and shoe references.
2. Choose the most representative scene based on product style, try-on context, and selling points.
3. Build model styling: outfit, accessories, jewelry, hair accessory, necklace, brooch or charm details, and a style-consistent bag.
4. Write concise Chinese poster copy supported by the shoe attributes and use scene.
5. Build a ChatGPT image-generation prompt for one 3:2 horizontal main poster with the model wearing the shoes.
6. Generate `main_poster_3x2.png` with ChatGPT image generation only.
7. Inspect the poster for shoe consistency, logo fidelity, model-on-foot visibility, text hierarchy, and 3:2 ratio.
8. If the shoe or logo drifts, regenerate with stricter reference constraints before passing downstream.

## Outputs

- `main_poster_3x2.png`: 3:2 horizontal main poster image.
- `main_poster_copywriting.json`: structured poster copy and generation metadata.

## `main_poster_copywriting.json` Schema

```json
{
  "brand": "SpiderKing",
  "language": "zh-CN",
  "image_backend": "ChatGPT image generation",
  "poster_aspect_ratio": "3:2",
  "main_poster_image": "main_poster_3x2.png",
  "main_title": "",
  "subtitle": "",
  "new_arrival_badge_text": "新款上市",
  "selling_points": [
    {
      "label": "",
      "copy": "",
      "source_basis": ""
    }
  ],
  "tone": "commercial, simple, high conversion",
  "model_on_foot_requirements": {
    "model_profile": "Chinese young female model",
    "shoe_visibility": "shoes clearly worn on feet, not blocked or cropped",
    "styling_source": "styling_spec.json or generated from product style, scene, and selling points"
  },
  "styling_plan": {
    "scene_type": "",
    "outfit": "",
    "jewelry": "",
    "hair_accessories": "",
    "necklace": "",
    "brooch_or_charms": "",
    "bag": ""
  },
  "logo_rules": {
    "brand_logo_ref": "assets/spiderking-logo.jpg",
    "placement": "upper-left safe area",
    "preserve_original_ratio": true,
    "do_not_redraw_logo": true
  },
  "image_prompt": "",
  "negative_prompt": "Do not alter the shoe shape, upper structure, sole, colors, materials, logo, stitching, laces, decorations, or proportions. Do not hide or crop the shoes. Do not redraw, replace, stylize, or invent the SpiderKing logo. Do not use any image model other than ChatGPT image generation.",
  "downstream_notes": "Pass main_poster_3x2.png and this JSON to Layout Engine for final brand card composition."
}
```

## Required Stage Summary

After completing this Skill, output:

1. Skill 目标: Generate the 3:2 SpiderKing horizontal main poster with model-on-foot product display and poster copy.
2. 输入参数: `shoe_attributes.json`, `scene_spec.json`, optional `styling_spec.json`, optional `brand_logo`, `shoe_reference`, optional `product_hint`.
3. 输出结果: `main_poster_3x2.png`, `main_poster_copywriting.json`.
4. 核心规则: ChatGPT image generation only; 3:2 horizontal poster; model wears the shoes; preserve shoe one-to-one; use uploaded logo without redrawing; scene, outfit, accessories, and bag must match product style and selling points.
5. 可复用接口: `SpiderKingCopywriting.run({ shoe_attributes, scene_spec, styling_spec, brand_logo, shoe_reference, product_hint })`.
6. 与下游 Skill 的连接方式: Pass `main_poster_3x2.png`, poster copy, selling points, badge text, and styling plan to Layout Engine.

## Acceptance Check

Accept only if:

- `main_poster_3x2.png` is 3:2 horizontal.
- The model is wearing the product shoes and the shoes are clearly visible.
- The shoes remain one-to-one with the original reference.
- The uploaded logo is used without redrawing or replacement.
- Scene, outfit, accessories, jewelry, hair details, and bag all fit the product style and selling points.
- The title is short enough for poster layout.
- There are 3 to 5 selling points.
- Every selling point is supported by product attributes, style, or scene.
- The copy sounds commercial and direct, not poetic or technical.
