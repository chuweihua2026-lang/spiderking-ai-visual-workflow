---
name: spiderking-selling-points
description: >-
  Generate a 27:18 horizontal SpiderKing shoe selling-points board divided into
  three polished sections: visual selling points, functional selling points, and
  scenario selling points. Use when Codex must analyze product details, enlarge
  shoe detail crops, add concise labels, auto-match supporting visuals to selling
  point copy, and create a beautified ecommerce marketing image. All image
  generation must use ChatGPT image generation only.
---

# SpiderKing Selling Points

Use this Skill after `spiderking-product-vision` has extracted shoe attributes and generated product views. It turns product details into one polished commercial selling-points board.

## Required Input

- `shoe_reference`: original shoe image or validated Product Vision output.
- `product_recognition.json`.
- `consumer_profile.json`.
- `persona_selection.json` when consumer-facing scene language depends on a human use context.
- `extracted_attributes.json`: shoe structure, colors, materials, visual details, and style tags.
- `commercial_styling_decision.json`: approved output from `spiderking-commercial-visual-stylist`.
- `commercial_scene_decisions`: 3 to 4 approved outputs from `spiderking-commercial-scene-director` for scenario cards.
- Optional `key_selling_points`: known selling points from copywriting or user notes.
- Optional `product_hint`: product name, launch theme, target customer, or channel.

## Hard Rules

- Invoke `spiderking-commercial-visual-stylist` before generating detail expansions, supporting visuals, scenario images, or the final board.
- Invoke `spiderking-commercial-scene-director` before generating each scenario image and load its commercial scene database.
- Do not generate until `commercial_styling_decision.json.status` is `approved`.
- Do not generate a scenario card until its matching `commercial_scene_decision_*.json.status` is `approved`.
- Select scenarios from detailed product function first and fashion position second. Do not apply the same generic park, commute, and shopping scenes to every shoe.
- Keep visible evidence, inferred benefit, and unsupported claims separate.
- Output one horizontal image with aspect ratio `27:18`.
- Divide the image into exactly three clear sections:
  1. Visual Selling Points
  2. Functional Selling Points
  3. Scenario Selling Points
- Use ChatGPT image generation only for all image generation, detail expansion, supporting visuals, and composited image output.
- Do not use Midjourney, Stable Diffusion, ComfyUI, or other image models.
- Preserve the shoe one-to-one with the input reference. Do not redesign, recolor, or invent product details.
- Use concise Chinese copy. Avoid long paragraphs and avoid claims not supported by visible product details.
- The board must be automatically arranged and beautified: clear hierarchy, refined typography, clean spacing, commercial visual rhythm, and consistent brand mood.

## Three-Section Logic

### 1. Visual Selling Points

Analyze visible shoe details and create enlarged detail crops or close-up callouts.

Good visual details include:

- breathable mesh upper;
- rhinestone or crystal decorative overlay;
- contrast color accents;
- lace, pull tab, stitching, or reflective tab details;
- toe cap, collar, side panel, or logo position.

Output requirements:

- Use product detail close-ups or magnified detail frames.
- Add concise visual-point labels near each detail.
- Keep labels short and premium, such as `闪钻点缀`, `透气网面`, `绿意撞色`, `细节走线`.
- Do not invent details that are not visible in the source shoe.

### 2. Functional Selling Points

Convert product structure into functional benefit points and auto-match supporting visuals to the text.

Good functional directions include:

- breathable upper;
- light cushioning;
- stable lacing;
- thick sole comfort;
- anti-slip style outsole only when the outsole texture visibly supports it;
- daily comfort and easy matching.

Output requirements:

- Pair each function point with a supporting product or lifestyle visual.
- Do not make medical, orthopedic, waterproof, absolute anti-slip, or durability claims unless explicitly supported.
- Keep copy direct and ecommerce-friendly.

### 3. Scenario Selling Points

Translate the shoe style and benefits into 3 to 4 representative usage scenario cards.

Good scenario directions include:

- weekend walk;
- light commute;
- shopping street;
- cafe street;
- campus daily wear;
- park or city leisure.
- mountain trail, forest dirt path, rocky slope, creekside boardwalk, campsite, or outdoor district when the product is hiking, trail, trekking, or light outdoor footwear.

Output requirements:

- Create 3 to 4 rectangular small scenario images inside the Scenario Selling Points section.
- Each scenario card should show only one representative environment scene. Do not include models, legs, feet, or shoes in scenario selling-point cards.
- Put concise scenario text below or beside each small image: a short scenario title plus one short descriptive line.
- Select scenarios from the product style and benefits. Do not use the same fixed scenarios for every shoe.
- For this white-green sparkling casual sneaker style, suitable examples include:
  - `周末轻行`: park, lawn, sunny path, relaxed walk;
  - `通勤百搭`: city street, commute block, office-adjacent walkway;
  - `出街吸睛`: commercial pedestrian street, shopping mall, boutique storefront;
  - `咖啡小憩`: cafe terrace or lifestyle street if a fourth card is needed.
- Scenario images should vary in material, color, and atmosphere. Do not make all cards look like the same street.
- Arrange scenario cards vertically, not as a 2x2 grid. Use a stacked vertical list or staggered vertical column so the layout works for either 3 or 4 scenes.
- Each scenario image should be a horizontal rectangle.
- Copy should communicate where and why the shoe fits the scene.

## Layout Direction

- Canvas ratio: `27:18` horizontal.
- Structure: three visually distinct but unified sections.
- Each section should have:
  - a short section title;
  - one hero visual or detail visual;
  - 1 to 3 concise selling-point labels;
  - refined commercial typography.
- For Scenario Selling Points, replace the single hero visual with 3 to 4 horizontal rectangular scenario cards in a vertical stacked layout. Each card has a scene-only image and short scenario text.
- Prefer a clean white, light gray, and pale green system when it matches the shoe.
- Use subtle dividers, soft shadows, magnified detail frames, callout lines, and light brand accents.
- Avoid clutter. The final image should feel clear, premium, and ready for ecommerce or social media.

## Workflow

1. Inspect `shoe_reference` and `extracted_attributes.json`.
2. Invoke `spiderking-commercial-visual-stylist` and approve the product-led commercial direction.
3. Select the strongest visual, functional, and scenario selling points, excluding unsupported claims.
4. Build a three-section layout plan for a `27:18` horizontal image.
5. For visual selling points, generate or crop magnified product detail visuals and add callout labels.
6. For functional selling points, create supporting visuals that match the visible structure and benefit text.
7. Invoke `spiderking-commercial-scene-director` for each scenario card, pass sibling diversity signatures, then create 3 to 4 function-led horizontal rectangular scene-only cards in a vertical stacked layout, each with short text below or beside the image.
8. Generate `selling_points_board_27x18.png` with ChatGPT image generation only.
9. Output `selling_points_manifest.json` with selected points, evidence, excluded claims, copy, prompts, and validation notes.
10. Regenerate if the product position drifts, the shoe drifts, text is too long, or the three sections are not visually clear.

## Outputs

- `selling_points_board_27x18.png`: horizontal 27:18 selling-points board.
- `selling_points_manifest.json`: selected selling points, copy, section plan, and prompt metadata.

## `selling_points_manifest.json` Schema

```json
{
  "skill_name": "SpiderKing Selling Points",
  "image_backend": "ChatGPT image generation",
  "commercial_styling_decision_ref": "commercial_styling_decision.json",
  "product_recognition_ref": "product_recognition.json",
  "consumer_profile_ref": "consumer_profile.json",
  "persona_selection_ref": "persona_selection.json",
  "commercial_scene_decision_refs": [],
  "aspect_ratio": "27:18",
  "source_image_ref": "",
  "output_image": "selling_points_board_27x18.png",
  "sections": {
    "visual_selling_points": {
      "section_title": "视觉卖点",
      "details_to_enlarge": [],
      "labels": [],
      "image_prompt": ""
    },
    "functional_selling_points": {
      "section_title": "功能卖点",
      "benefits": [],
      "supporting_visuals": [],
      "image_prompt": "",
      "evidence": [],
      "excluded_unsupported_claims": []
    },
    "scenario_selling_points": {
      "section_title": "场景卖点",
      "scenario_cards": [
        {
          "title": "",
          "description": "",
          "scene_visual": "",
          "scene_basis": "",
          "commercial_scene_decision_ref": "",
          "must_not_include": ["model", "legs", "feet", "shoes"]
        }
      ],
      "image_prompt": ""
    }
  },
  "layout_notes": {
    "composition": "three-section horizontal ecommerce board",
    "typography": "concise modern Chinese commercial typography",
    "visual_style": "clean, premium, clear, beautified"
  },
  "consistency_constraints": [
    "以输入鞋图为唯一产品参考，鞋子本体一比一还原，不改变结构、材质、颜色、比例、Logo 和细节"
  ],
  "negative_prompt": "Do not redesign the shoe. Do not invent unsupported product details or claims. Do not use long copy. Do not use any image model other than ChatGPT image generation."
}
```

## Required Stage Summary

After completing this Skill, output:

1. Skill 目标: Generate a 27:18 horizontal three-section selling-points board.
2. 输入参数: `shoe_reference`, `extracted_attributes.json`, optional `key_selling_points`, optional `product_hint`.
3. 输出结果: `selling_points_board_27x18.png`, `selling_points_manifest.json`.
4. 核心规则: ChatGPT image generation only; three sections for visual, functional, and scenario selling points; preserve shoe one-to-one; use concise supported copy; auto-layout and beautify the image.
5. 可复用接口: `SpiderKingSellingPoints.run({ shoe_reference, extracted_attributes, key_selling_points, product_hint })`.
6. 与下游 Skill 的连接方式: Pass `selling_points_board_27x18.png` and `selling_points_manifest.json` to Layout Engine for final brand card composition.

## Acceptance Check

Accept only if:

- The final image is horizontal `27:18`.
- The image has exactly three clear sections: visual, functional, and scenario selling points.
- Visual selling points include enlarged or close-up product details with labels.
- Functional selling points pair concise copy with matching supporting visuals.
- Scenario selling points include 3 to 4 horizontal rectangular scene-only images in a vertical stacked layout, each with a short title and one short descriptive line.
- Scenario cards are based on product style and usage context, and the scene visuals are materially and atmospherically distinct.
- Scenario cards follow the approved detailed product-function classification rather than a generic sports template.
- The Commercial Visual Stylist decision exists and is approved.
- Every scenario card has an approved Commercial Scene Director decision, and cards differ in space, architecture, ground, time or light, and camera language.
- Scenario cards do not include models, legs, feet, or shoes.
- Text is short, readable, and visually integrated.
- The layout is polished, clear, and not overcrowded.
- The shoe remains consistent with the original reference.
- All image generation used ChatGPT image generation only.
