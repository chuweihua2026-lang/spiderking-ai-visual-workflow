---
name: spiderking-product-vision
description: >-
  Generate SpiderKing shoe product visual assets from 1 to 3 shoe reference
  images. Use when Codex must create a structure-faithful Product Vision stage:
  3:2 single-shoe side view on white background, 3:2 pair-of-shoes 45-degree
  commercial hero view, 3:2 pair-of-shoes top view, two short selling-point text
  lines under each view, and extracted shoe attributes for downstream scene,
  styling, copy, and layout Skills. All image generation must use ChatGPT image
  generation only and must preserve the input shoe one-to-one.
---

# SpiderKing Product Vision

Use this Skill first in the SpiderKing brand card pipeline. The only product source of truth is the uploaded shoe image set.

## Required Input

- `shoe_image`: 1 to 3 paths, URLs, or attachment references for the original shoe images.
- Optional `optional_product_hint`: known model name, category, selling context, target customer, or product description.
- `commercial_styling_decision.json`: required only for the image-rendering phase, after product recognition, consumer profiling, and styling approval.

## Hard Rules

- Always run product recognition first without generating images.
- Invoke `spiderking-commercial-visual-stylist` only after `product_recognition.json` exists, then require its approved decision before creating any product-view image. For product-only views, person fields may be `not_applicable` in the rendering brief.
- Do not generate until `commercial_styling_decision.json.status` is `approved`.
- Use ChatGPT image generation only for all image generation or image editing.
- Do not use Midjourney, Stable Diffusion, ComfyUI, or any other image model.
- Use the input shoe images as the only product references.
- Do not redesign, simplify, stylize, recolor, mirror incorrectly, or reinterpret the shoe.
- Preserve one-to-one: shoe shape, silhouette, outsole, upper panels, stitching, logo, texture, material finish, lace or buckle system, hardware, color blocking, toe shape, heel shape, proportions, and visible wear details.
- Only allow lighting cleanup, background cleanup, shadow refinement, angle normalization, and commercial polish.
- If consistency conflicts with visual drama, protect shoe consistency first.
- Classify product function before assigning a generic style label. Record primary category, subcategory, intended activity, terrain or use context, visible functional construction, fashion attributes, evidence confidence, and unsupported claims.
- Do not infer waterproofing, medical benefits, absolute anti-slip performance, durability, or other functions that the images and supplied product information do not prove.

## Workflow

1. Inspect all provided shoe images and identify the most reliable product facts without calling an image model.
2. Produce `product_recognition.json` and `extracted_attributes.json`, separating visible evidence, user-supplied facts, inference, confidence, and unsupported claims.
3. Pass product recognition to the Consumer Profile, Persona Selection, and Commercial Visual Styling stages.
4. Receive approved `commercial_styling_decision.json` after those stages complete.
5. Generate the three 3:2 product images with ChatGPT image generation, always attaching or referencing the original shoe image set.
6. Validate each output against the consistency checklist.
7. Regenerate with stricter reference constraints if any key detail drifts.

## Outputs

- `side_view.png`: 3:2 side view, one single shoe, clean white background, clear structure, two short selling-point text lines below the image.
- `hero_45_view.png`: 3:2 45-degree front commercial hero view, one pair of shoes, clean white background and polished lighting, two short selling-point text lines below the image.
- `top_view.png`: 3:2 top-down front view, one pair of shoes, shoe laces, upper, and toe structure clearly visible, two short selling-point text lines below the image.
- `product_vision_preview.png`: polished horizontal preview sheet combining the three views into a clear commercial product card.
- `product_recognition.json`: image-free product recognition result and the upstream source of truth for consumer, persona, styling, scene, copy, and selling-point decisions.
- `extracted_attributes.json`: structured product attributes for downstream Skills.

## `product_recognition.json` Schema

```json
{
  "stage": "product_recognition",
  "status": "approved",
  "source_images": [],
  "product_identity": {
    "brand": "SpiderKing",
    "product_type": "",
    "primary_category": "",
    "subcategory": "",
    "target_gender_or_unisex": "",
    "season_or_weather_context": []
  },
  "visible_facts": {
    "shape_and_silhouette": [],
    "colors": [],
    "materials": [],
    "sole_and_tread": [],
    "upper_and_protection": [],
    "closure": [],
    "logo_and_brand_details": [],
    "fashion_attributes": []
  },
  "functional_classification": {
    "intended_activities": [],
    "terrain_or_use_context": [],
    "activity_intensity": "",
    "visible_functional_features": []
  },
  "evidence": [],
  "inferences_with_confidence": [],
  "unsupported_claims": [],
  "recognition_check": {
    "source_images_consistent": true,
    "specialized_category_not_reduced_to_generic_sports": true,
    "unsupported_claims_excluded": true
  }
}
```

## `extracted_attributes.json` Schema

```json
{
  "skill_name": "Product Vision Skill",
  "inputs": {
    "shoe_image": [],
    "optional_product_hint": ""
  },
  "image_backend": "ChatGPT image generation",
  "outputs": {
    "side_view": "side_view.png",
    "hero_45_view": "hero_45_view.png",
    "top_view": "top_view.png",
    "product_vision_preview": "product_vision_preview.png",
    "extracted_attributes": {
      "shoe_type": "",
      "product_style": "",
      "functional_classification": {
        "primary_category": "",
        "subcategory": "",
        "intended_activities": [],
        "terrain_or_use_context": [],
        "activity_intensity": "",
        "visible_functional_features": [],
        "fashion_attributes": [],
        "classification_evidence": [],
        "unsupported_claims": []
      },
      "main_colors": [],
      "materials": [],
      "sole_type": "",
      "design_language": "",
      "key_visual_elements": [],
      "view_selling_points": {
        "side_view": ["", ""],
        "hero_45_view": ["", ""],
        "top_view": ["", ""]
      },
      "logo_positions": [],
      "closure_type": "",
      "texture_and_finish": [],
      "visible_construction": []
    }
  },
  "consistency_constraints": [
    "以输入鞋图为唯一产品参考，鞋子本体一比一还原，不改变结构、材质、颜色、比例、Logo 和细节"
  ],
  "commercial_styling_decision_ref": "commercial_styling_decision.json",
  "product_recognition_ref": "product_recognition.json",
  "image_prompts": {
    "side_view": "",
    "hero_45_view": "",
    "top_view": ""
  },
  "negative_prompt": "Do not alter shoe structure, outsole, upper paneling, logo, stitching, materials, color blocking, proportions, laces, hardware, toe shape, heel shape, or texture. Do not invent new details. Do not use any image model other than ChatGPT image generation."
}
```

## Prompt Requirements

Every ChatGPT image-generation prompt must include this exact Chinese constraint:

`以输入鞋图为唯一产品参考，鞋子本体一比一还原，不改变结构、材质、颜色、比例、Logo 和细节。`

Every prompt must also follow the approved brand, product, color, material, composition, and commercial-photography decisions from `commercial_styling_decision.json`.

Use these view-specific requirements:

- `side_view`: one single shoe, exact side profile, clean white background, 3:2 ratio, ecommerce product clarity, two short Chinese selling-point text lines below the product image.
- `hero_45_view`: one pair of shoes, 45-degree front angle, white background, commercial lighting, 3:2 ratio, two short Chinese selling-point text lines below the product image.
- `top_view`: one pair of shoes, top-down front view, white background, laces, upper, and toe structure clear, 3:2 ratio, two short Chinese selling-point text lines below the product image.

Text under each view must be concise and visually light. Use exactly two short Chinese lines, each no more than 8 Chinese characters when possible. Choose points from the visible angle, such as structure, breathable upper, diamond-like decoration, light cushioning, stable outsole, or easy matching. Do not use exaggerated or absolute claims.

## Preview Sheet Direction

Create `product_vision_preview.png` after the three product views are accepted.

- Use a horizontal commercial product card layout.
- Keep three clear equal columns: side view, 45-degree hero view, top view.
- Use warm white or clean white background, soft commercial shadows, subtle dividers, and generous margins.
- Add understated angle labels such as `正侧面`, `45°主视觉`, and `俯视细节`.
- Put the two short selling-point text lines below each product view.
- Use refined modern Chinese ecommerce typography: first line slightly bolder, second line lighter; dark gray text with optional small green accent.
- Keep the structure bright, clear, and visually premium. Do not make the sheet look like a plain contact sheet.

## Consistency Checklist

Check every generated image for:

- Overall silhouette and proportion
- Outsole shape, tread impression, thickness, and color
- Upper panel layout and seams
- Stitching and decorative lines
- Logo shape, position, scale, and orientation
- Lace, buckle, zipper, or closure details
- Material grain, gloss, fabric, leather, mesh, or knit texture
- Color blocking and small accent colors
- Toe, heel, collar, tongue, and opening shape

If any item fails, regenerate with ChatGPT image generation and a stricter reference prompt.

## Required Stage Summary

After completing this Skill, output:

1. Skill 目标: Generate standardized 3:2 product views and structured shoe attributes.
2. 输入参数: `shoe_image` supporting 1 to 3 images, optional `optional_product_hint`, and approved `commercial_styling_decision.json` for rendering.
3. 输出结果: `product_recognition.json`, `side_view.png`, `hero_45_view.png`, `top_view.png`, `product_vision_preview.png`, `extracted_attributes.json`; each product view includes two short selling-point text lines below the image.
4. 核心规则: ChatGPT image generation only; preserve the input shoe one-to-one; do not redesign, recolor, or alter structure; only improve clarity, lighting, white background, and commercial polish.
5. 可复用接口: `SpiderKingProductVision.recognize({ shoe_image, optional_product_hint })`, then `SpiderKingProductVision.render({ product_recognition, commercial_styling_decision, shoe_image })`.
6. 与下游 Skill 的连接方式: Pass `extracted_attributes.json` to Scene Engine, Styling Engine, and Copywriting; pass all three product views to Layout Engine.

## Attribute Acceptance Gate

Accept product classification only if:

- The primary category and subcategory are more specific than a generic `运动鞋` label when visible evidence supports a specialized use.
- Functional attributes cite visible construction or user-supplied facts.
- Outdoor hiking or trail footwear remains outdoor-led in downstream scene and styling decisions.
- Unsupported claims are explicitly listed and excluded from copy.
- The revalidated `commercial_styling_decision.json.status` is `approved`.
