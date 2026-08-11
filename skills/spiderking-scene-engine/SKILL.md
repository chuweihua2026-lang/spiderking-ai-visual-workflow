---
name: spiderking-scene-engine
description: >-
  Create one lifestyle scene for SpiderKing footwear marketing from extracted
  shoe attributes and the original shoe reference. Use when Codex must derive a
  9:16 scene image from product style while preserving the shoe one-to-one. All
  image generation must use ChatGPT image generation only.
---

# SpiderKing Scene Engine

Use this Skill after `spiderking-product-vision`. It creates one optimal lifestyle scene that fits the shoe style.

## Required Input

- `shoe_attributes.json` from Product Vision.
- `product_recognition.json`.
- `consumer_profile.json`.
- `persona_selection.json` when the scene includes a person.
- `source_image_ref` or product reference image from Product Vision.
- `commercial_styling_decision.json`: approved output from `spiderking-commercial-visual-stylist`.
- `commercial_scene_decision.json`: approved output from `spiderking-commercial-scene-director`.

## Hard Rules

- Invoke `spiderking-commercial-visual-stylist` before generating the scene.
- Invoke `spiderking-commercial-scene-director`, read its commercial scene database, and approve the scene before generation.
- Do not generate until `commercial_styling_decision.json.status` is `approved`.
- Do not generate until `commercial_scene_decision.json.status` is `approved`.
- Use ChatGPT image generation only. Do not use image2, Midjourney, Stable Diffusion, ComfyUI, Gemini image generation, or any other image model.
- Attach the original shoe image or validated product reference to every ChatGPT image-generation call.
- Derive the scene from detailed product function first and fashion style second, not from hardcoded examples.
- Keep the shoe one-to-one with the input reference in every visible detail.
- Do not let scene props, motion blur, camera angle, pants, grass, shadows, or foreground objects obscure key shoe details.

## Scene Selection

Choose one best scene based on `style_tags`, material, silhouette, and category:

- Street: fashion casual, chunky sole, high contrast colorway, trend styling.
- Park: soft casual, comfort, walking, breathable or lightweight shoe.
- Cafe: refined casual, loafers, flats, subtle leather, lifestyle elegance.
- Business street: commuting, leather, clean profile, urban professional use.
- Campus: youthful, sporty casual, lightweight, approachable daily wear.
- Mountain trail or forest path: hiking, trekking, trail, rugged outsole, protective upper, outdoor or utility styling.
- Creek, rocky slope, or outdoor boardwalk: light outdoor exploration, grip-led construction, functional styling.
- Urban outdoor district: outdoor function with gorpcore or city-trail fashion attributes.

If another scene is clearly better, use it and explain the reason in `scene_spec.json`.

## Outputs

- `scene_lifestyle_9x16.png`: one 9:16 lifestyle scene image.
- `scene_spec.json`: scene rationale and ChatGPT image-generation brief.

## `scene_spec.json` Schema

```json
{
  "source_image_ref": "",
  "image_backend": "ChatGPT image generation",
  "commercial_styling_decision_ref": "commercial_styling_decision.json",
  "product_recognition_ref": "product_recognition.json",
  "consumer_profile_ref": "consumer_profile.json",
  "persona_selection_ref": "persona_selection.json",
  "commercial_scene_decision_ref": "commercial_scene_decision.json",
  "selected_scene": "",
  "scene_rationale": "",
  "environment_details": {
    "location": "",
    "time_of_day": "",
    "lighting": "",
    "background_elements": [],
    "camera_style": ""
  },
  "shoe_visibility_plan": {
    "framing": "",
    "foot_position": "",
    "avoid_obstructions": []
  },
  "consistency_constraints": [
    "以输入鞋图为唯一产品参考，鞋子本体一比一还原，不改变结构、材质、颜色、比例、Logo 和细节"
  ],
  "image_prompt": "",
  "negative_prompt": "Do not change the shoe design, structure, material, logo, stitching, sole, color blocking, proportions, or details. Do not hide the shoe behind clothing, props, grass, motion blur, or shadows. Do not use any image model other than ChatGPT image generation."
}
```

## Prompt Requirements

Every ChatGPT image-generation prompt must include:

`以输入鞋图为唯一产品参考，鞋子本体一比一还原，不改变结构、材质、颜色、比例、Logo 和细节。`

## Acceptance Check

Accept only if:

- The selected scene clearly matches the shoe style.
- The selected scene matches the detailed product function and approved Commercial Visual Stylist decision.
- The approved Commercial Scene Director decision matches product, consumer, use context, brand feeling, space, time, light, action, and camera language.
- The shoe is visible enough for ecommerce marketing.
- The shoe details match the input reference one-to-one.
- The image is 9:16 or can be cleanly cropped to 9:16 without losing shoe visibility.
- ChatGPT image generation is the only image backend.
