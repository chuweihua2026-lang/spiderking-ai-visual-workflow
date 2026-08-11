---
name: spiderking-product-vision
description: >-
  Generate SpiderKing shoe product visual assets from 1 to 3 shoe reference
  images. Use when Codex must create a structure-faithful Product Vision stage:
  3:2 single-shoe side view on white background, 3:2 pair-of-shoes 45-degree
  commercial hero view, 3:2 pair-of-shoes top view, a separate preview sheet
  with two selling-point lines under each view, and extracted shoe attributes for downstream scene,
  styling, copy, and layout Skills. All image generation must use ChatGPT image
  generation only and must preserve the input shoe one-to-one.
---

# SpiderKing Product Vision

Use this Skill first in the SpiderKing brand card pipeline. The only product source of truth is the uploaded shoe image set.

## Required Input

- `shoe_image`: 1 to 3 paths, URLs, or attachment references for the original shoe images.
- Optional `optional_product_hint`: known model name, category, selling context, target customer, or product description.

## Hard Rules

- Product Vision is a product-only route. Before generation enforce: `商品识别 -> 结构一致性分析 -> 角度与数量规划 -> 白底商业化生成 -> 一致性质检`.
- Do not require consumer profile, persona selection, clothing, bag, accessory, or scene decisions for white-background product views.
- Always run product recognition first without generating images.
- Use ChatGPT image generation only for all image generation or image editing.
- Do not use Midjourney, Stable Diffusion, ComfyUI, or any other image model.
- Use the input shoe images as the only product references.
- Do not redesign, simplify, stylize, recolor, mirror incorrectly, or reinterpret the shoe.
- Preserve one-to-one: shoe shape, silhouette, outsole, upper panels, stitching, logo, texture, material finish, lace or buckle system, hardware, color blocking, toe shape, heel shape, proportions, and visible wear details.
- Only allow lighting cleanup, background cleanup, shadow refinement, angle normalization, and commercial polish.
- If consistency conflicts with visual drama, protect shoe consistency first.
- Classify product function before assigning a generic style label. Record primary category, subcategory, intended activity, terrain or use context, visible functional construction, fashion attributes, evidence confidence, and unsupported claims.
- Do not infer waterproofing, medical benefits, absolute anti-slip performance, durability, or other functions that the images and supplied product information do not prove.
- Use the latest approved three-view reference as a minimum visual baseline: three equal columns, strong product scale, clean white background, restrained dividers, and no large meaningless blank areas.
- Under every shoe view, use exactly one four-Chinese-character primary selling point in large type and one four-Chinese-character supporting line in smaller type. Do not add redundant angle labels below these two lines in the final preview.
- Keep the four-character captions visually prominent after the three views are combined; do not shrink an already approved product card into a small image inside another framed card.
- Keep `side_view.png`, `hero_45_view.png`, and `top_view.png` as clean text-free product assets. Add selling-point typography only in `product_vision_preview.png`.
- Never remove baked-in captions with one fixed pixel-height crop shared across different view orientations. Prefer text-free generation; if legacy separation is unavoidable, detect and preserve each view's complete product region independently.
- Preserve at least 4% clear safety space around every complete shoe silhouette. Toe, outsole, heel, collar, opening, and pull tabs must all remain visible; touching the safety zone is a hard failure.

## Workflow

1. Inspect all provided shoe images and identify the most reliable product facts without calling an image model.
2. Produce `product_recognition.json` and `extracted_attributes.json`, separating visible evidence, user-supplied facts, inference, confidence, and unsupported claims.
3. Complete structure consistency analysis and approve the exact view/count plan.
4. Generate the three 3:2 product images with ChatGPT image generation, always attaching or referencing the original shoe image set.
5. Validate each output against the consistency checklist.
6. Regenerate with stricter reference constraints if any key detail drifts.
7. Pass approved recognition and product assets to the Consumer Profile, Persona Selection, Commercial Visual Styling, and Scene Selection stages only when downstream commercial imagery is requested.

## Outputs

- `side_view.png`: text-free 3:2 side view, one single shoe, clean white background, complete silhouette and clear structure.
- `hero_45_view.png`: text-free 3:2 45-degree front commercial hero view, one complete pair of shoes, clean white background and polished lighting.
- `top_view.png`: text-free 3:2 top-down front view, one complete pair of shoes with toe, laces, upper, collar, heel, and pull tabs fully visible.
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

Every prompt must follow the approved product-recognition, structure-consistency, angle/count, white-background photography, and consistency-QA decisions.

Use these view-specific requirements:

- `side_view`: one complete single shoe, exact side profile, clean white background, 3:2 ratio, ecommerce product clarity, no text.
- `hero_45_view`: one complete pair of shoes, 45-degree front angle, white background, commercial lighting, 3:2 ratio, no text.
- `top_view`: one complete pair of shoes, top-down front view, white background, toe, laces, upper, collar, heel, and pull tabs clear, 3:2 ratio, no text.

Selling-point text belongs only to the preview sheet. Use exactly two short Chinese lines there, each no more than 8 Chinese characters when possible. Choose points from the visible angle and avoid exaggerated or absolute claims.

## Preview Sheet Direction

Create `product_vision_preview.png` after the three product views are accepted.

- Use a horizontal commercial product card layout.
- Keep three clear equal columns: side view, 45-degree hero view, top view.
- Use warm white or clean white background, soft commercial shadows, subtle dividers, and generous margins.
- Put exactly one four-character primary selling point and one four-character supporting line below each product view.
- Do not add a second row of redundant angle labels beneath the selling-point lines.
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
- Complete product silhouette with at least 4% clear space on every side; no toe, outsole, heel, collar, opening, or pull tab may be clipped
- `top_view.png` explicitly shows both complete shoes from toe through heel and both pull tabs
- Three equal columns with product scale and information density at least equal to the approved reference
- One large four-character headline plus one smaller four-character support line under each shoe view
- No redundant bottom labels, nested cards, or large meaningless blank areas

If any item fails, regenerate with ChatGPT image generation and a stricter reference prompt.

## Required Stage Summary

After completing this Skill, output:

1. Skill 目标: Generate standardized 3:2 product views and structured shoe attributes.
2. 输入参数: `shoe_image` supporting 1 to 3 images and optional `optional_product_hint`.
3. 输出结果: `product_recognition.json`, three text-free product-view assets, `product_vision_preview.png` with two short selling-point lines per view, and `extracted_attributes.json`.
4. 核心规则: ChatGPT image generation only; preserve the input shoe one-to-one; do not redesign, recolor, or alter structure; only improve clarity, lighting, white background, and commercial polish.
5. 可复用接口: `SpiderKingProductVision.recognize({ shoe_image, optional_product_hint })`, then `SpiderKingProductVision.render({ product_recognition, structure_consistency, view_plan, shoe_image })`.
6. 与下游 Skill 的连接方式: Pass `extracted_attributes.json` to Scene Engine, Styling Engine, and Copywriting; pass all three product views to Layout Engine.

## Attribute Acceptance Gate

Accept product classification only if:

- The primary category and subcategory are more specific than a generic `运动鞋` label when visible evidence supports a specialized use.
- Functional attributes cite visible construction or user-supplied facts.
- Outdoor hiking or trail footwear remains outdoor-led in downstream scene and styling decisions.
- Unsupported claims are explicitly listed and excluded from copy.
- The product structure, view/count plan, and final one-to-one consistency review are approved.
