---
name: spiderking-layout-engine
description: >-
  Compose the final SpiderKing branded card image system from all approved
  upstream assets: 3:2 main poster, Product Vision three-view preview, three
  separate 9:16 model scene images, 27:18 selling-points board, and uploaded
  SpiderKing logo. Use when Codex must create the final integrated ecommerce
  brand card layout. Default output is two different layout template images.
  Any image generation must use ChatGPT image generation only.
---

# SpiderKing Layout Engine

Use this Skill last. It integrates all approved SpiderKing visual modules into final brand card image systems. By default, output two different layout templates for selection.

## Built-In Brand Asset

- SpiderKing logo: `assets/spiderking-logo.jpg`
- Use this uploaded logo by default. Do not redraw, replace, stylize, or invent the logo.

## Required Input

- `main_poster_3x2.png` from `spiderking-copywriting`.
- `product_vision_preview.png` or product views from `spiderking-product-vision`.
- `scene_model_01.png`, `scene_model_02.png`, `scene_model_03.png` from `spiderking-styling-engine`.
- `selling_points_board_27x18.png` from `spiderking-selling-points`.
- `brand_logo`: default `assets/spiderking-logo.jpg`.
- Optional metadata JSON from upstream Skills.

## Hard Rules

- When new visual content must be generated, invoke `spiderking-commercial-visual-stylist` first and require an approved `commercial_styling_decision.json`. Pure deterministic placement of approved assets does not require a new styling pass.
- If any new image content must be generated, use ChatGPT image generation only.
- Do not use Midjourney, Stable Diffusion, ComfyUI, or other image models.
- Prefer deterministic layout composition from approved upstream PNG/JPG assets when the task is only final排版.
- Preserve original upstream image quality as much as possible: do not ask AI to redraw approved images, do not repaint the shoes, do not rewrite approved poster typography, and do not crop away important product/model content.
- Preserve all shoe details one-to-one across every module.
- Use the uploaded SpiderKing logo asset. Do not redraw, replace, stylize, or invent the logo.
- Keep the final card visually unified, clear, and ecommerce-ready.
- Do not overcrowd the layout. Use clear vertical hierarchy and consistent spacing.
- The final card must look like a finished SpiderKing marketing system, not a backend contact sheet, asset collection, or simple grid of uploaded images.
- Do not add obvious tool labels such as `主海报`, `产品视图`, `穿搭场景`, or `卖点解析` as large section titles unless the approved reference template already uses that wording.
- Do not wrap every upstream asset in heavy visible cards or boxed placeholders. Use clean white space, subtle separators, and the original module typography to create one unified layout.
- Scene model images must be integrated as a polished scene gallery, not cropped into random material slots or contact-sheet cells.
- Template B must not become a plain top-to-bottom stack. It must follow the approved vertical integrated card rhythm: brand header, hero poster, product view, scene gallery, selling-points section, and refined footer accents.
- Preserve upstream module logic:
  - main poster is `3:2` horizontal;
  - product vision includes side single shoe, 45-degree pair, and top pair;
  - scene model section contains three separate `9:16` standing model images;
  - selling-points board is `27:18` horizontal.

## Final Layout Direction

Create two polished brand card layout templates:

### Template A: Left-Right Business Card Layout

Use this as the preferred approved template when the user asks for a clear commercial card:

1. Left upper area: `main_poster_3x2.png`.
2. Left lower area: three separate `9:16` scene model images, arranged as a clean scene gallery.
3. Right upper area: `product_vision_preview.png`.
4. Right lower area: `selling_points_board_27x18.png`.
5. Include a clean SpiderKing logo/header zone if space allows.
6. Keep the layout close to the confirmed reference: large image modules on a soft off-white canvas, thin dividers, generous margins, minimal extra labels, no heavy card frames.

### Template B: Approved Vertical Integrated Card

Use this as the approved alternate template. It follows the already accepted generated reference:
`/Users/chuchu/.codex/generated_images/019f0691-3b5c-7010-aff9-07647e7f0d97/ig_03cefcbc1441eb47016a3f49cfd1a8819998893d2df5377698.png`

1. Create a vertical integrated brand card with a clean ecommerce hierarchy.
2. Top area: SpiderKing brand header/logo and main poster module.
3. Middle area: product vision three-view section.
4. Lower area: three separate model scene images and selling-point modules.
5. Keep the visual rhythm close to the approved reference image while preserving all current upstream asset content and shoe consistency.
6. Avoid shrinking the selling-points board into a tiny thumbnail. It must remain readable enough to function as a marketing section.

### Optional Vertical Template

Only create another fully stacked vertical card if the user explicitly asks for a third template:

1. Brand header.
2. Main poster.
3. Product vision.
4. Scene model gallery.
5. Selling-points board.

## Visual Style

- Use a clean white, light gray, pale green, and soft silver system for this product unless upstream assets indicate another palette.
- Use subtle dividers, soft shadows, consistent rounded corners, and refined modern Chinese ecommerce typography.
- Keep section titles short and premium.
- Make the final output feel like one unified SpiderKing product card, not unrelated images pasted together.
- Use the upstream asset typography and visual hierarchy as the primary visual language; additional labels should be subtle or omitted.

## Outputs

- `final_brand_card_template_a.png`: final integrated brand card image, left-right business card layout.
- `final_brand_card_template_b.png`: final integrated brand card image, approved vertical integrated card layout.
- `layout_manifest.json`: layout plan, asset references, and validation notes.

## `layout_manifest.json` Schema

```json
{
  "skill_name": "SpiderKing Layout Engine",
  "image_backend": "ChatGPT image generation",
  "brand_asset_ref": "assets/spiderking-logo.jpg",
  "inputs": {
    "main_poster": "main_poster_3x2.png",
    "product_vision_preview": "product_vision_preview.png",
    "scene_model_images": [
      "scene_model_01.png",
      "scene_model_02.png",
      "scene_model_03.png"
    ],
    "selling_points_board": "selling_points_board_27x18.png"
  },
  "outputs": {
    "final_brand_card_template_a": "final_brand_card_template_a.png",
    "final_brand_card_template_b": "final_brand_card_template_b.png"
  },
  "layout_templates": {
    "template_a": {
      "name": "Left-Right Business Card Layout",
      "sections": [
        "left_upper_main_poster",
        "left_lower_scene_model_gallery",
        "right_upper_product_vision",
        "right_lower_selling_points"
      ]
    },
    "template_b": {
      "name": "Approved Vertical Integrated Card",
      "reference_image": "/Users/chuchu/.codex/generated_images/019f0691-3b5c-7010-aff9-07647e7f0d97/ig_03cefcbc1441eb47016a3f49cfd1a8819998893d2df5377698.png",
      "sections": [
        "brand_header",
        "main_poster_module",
        "product_vision_module",
        "scene_model_gallery",
        "selling_points_modules"
      ]
    }
  },
  "brand_rules_applied": [
    "Use uploaded SpiderKing logo without redrawing.",
    "Preserve product consistency across every module."
  ],
  "consistency_constraints": [
    "以输入鞋图为唯一产品参考，鞋子本体一比一还原，不改变结构、材质、颜色、比例、Logo 和细节",
    "最终排版优先使用上游已确认图片原图，不通过 AI 重绘导致画质下降或内容变化"
  ],
  "negative_prompt": "Do not alter shoe details. Do not distort or redraw the SpiderKing logo. Do not create unrelated layouts. Do not overcrowd the final card. Do not use any image model other than ChatGPT image generation. Do not regenerate approved upstream images when deterministic layout composition is sufficient."
}
```

## Required Stage Summary

After completing this Skill, output:

1. Skill 目标: Compose the final SpiderKing brand card image system.
2. 输入参数: `main_poster_3x2.png`, `product_vision_preview.png`, three `scene_model_*.png` images, `selling_points_board_27x18.png`, and SpiderKing logo.
3. 输出结果: `final_brand_card_template_a.png`, `final_brand_card_template_b.png`, `layout_manifest.json`.
4. 核心规则: ChatGPT image generation only when new generated content is required; preserve shoe and logo consistency; use approved upstream images for final排版; output two clearly different brand-card templates.
5. 可复用接口: `SpiderKingLayoutEngine.run({ main_poster, product_vision_preview, scene_model_images, selling_points_board, brand_logo })`.
6. 与下游 Skill 的连接方式: This is the final output stage; pass both `final_brand_card_template_a.png` and `final_brand_card_template_b.png` to delivery or export workflow.

## Acceptance Check

Accept only if:

- The final output includes two different integrated brand card template images.
- Template A follows the left-upper main poster, left-lower scenes, right-upper product vision, right-lower selling-points structure.
- Template B follows the approved vertical integrated card reference image.
- Neither template looks like a simple collage, contact sheet, or asset management board.
- Extra section labels, thick boxes, and placeholder-like frames are avoided.
- The uploaded SpiderKing logo is used and remains readable.
- The main poster, product vision, model scene gallery, and selling-points board are all present.
- The three model scene images remain visually separate.
- The layout has clear hierarchy, consistent style, and enough breathing room.
- Shoe details remain consistent across the whole card.
- Approved upstream images are not unnecessarily redrawn, distorted, blurred, or degraded.
- Any newly generated image content used ChatGPT image generation only.
- Any newly generated image content follows an approved Commercial Visual Stylist decision.
