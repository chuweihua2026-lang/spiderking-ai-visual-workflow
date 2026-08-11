---
name: spiderking-styling-engine
description: >-
  Generate three 9:16 different-scene standing model images for SpiderKing
  footwear marketing from product style, selling points, and scene direction.
  Use when Codex must create Chinese female model styling, non-repeating outfits,
  accessories, bags, atmospheric scenes, scene-title poster typography, and shoe
  visibility constraints. All image generation must use ChatGPT image generation
  only.
---

# SpiderKing Styling Engine

Use this Skill after `spiderking-product-vision` and scene direction are available. It creates three different 9:16 standing model scene images while protecting shoe visibility.

## Required Input

- `extracted_attributes.json` or product style tags from Product Vision.
- `commercial_styling_decision.json`: approved output from `spiderking-commercial-visual-stylist`.
- `scene_spec.json` or scene direction from Scene Engine, if available.
- `key_selling_points`: shoe selling points from Product Vision or main poster copy.
- `shoe_reference`: original shoe image or validated product reference.
- Optional `style_hint`: campaign mood, customer profile, season, or store channel.

## Hard Rules

- Invoke `spiderking-commercial-visual-stylist` before generating each model image and load its detailed framework.
- Do not generate when `commercial_styling_decision.json` is missing, stale for another product, or not `approved`.
- Follow the mandatory analysis order before prompting: person, brand, product function, scene, clothing, footwear, bag, accessories, color, materials, pose/camera, and commercial optimization.
- Let product function control the scene and outfit before trend styling. Do not reduce outdoor hiking, trail, business, or other specialized footwear to generic sportswear.
- Generate exactly three different 9:16 model scene images.
- Generate them as three separate image files, not one combined triptych, collage, grid, contact sheet, or multi-panel preview.
- All models must be standing. Do not use sitting, crouching, kneeling, lying, jumping, or half-body-only poses.
- Standing actions must not repeat across the three images. Each image needs a distinct standing pose and body direction while keeping the shoes visible.
- Model styling must not repeat across the three images. Vary outfit silhouette, color emphasis, accessories, bag type, hairstyle, makeup design, and scene mood while keeping the same shoe.
- Every image must have a strong scene atmosphere, not a plain background.
- Scene materials and backgrounds must not feel repetitive. Do not reuse the same stone pavement look across all images.
- Use varied ground and background materials when appropriate: grass, wooden bridge, cobblestone, pebble path, cafe tile, asphalt, steps, storefront, water edge, garden path, campus lane, or city terrace.
- Camera angle and viewing perspective must not be too similar across the three images. Vary full-body framing, low-angle shoe emphasis, walking-stance standing pose, side-facing standing pose, or 3/4 standing composition while keeping shoes visible.
- Add poster typography to each image. The text content is a scene title, not a blunt location label.
- Scene title text must sound professional and atmospheric, such as a campaign phrase. Avoid overly direct titles like `公园`, `街头`, or `商场`.
- Use ChatGPT image generation only for all model images. Do not use Midjourney, Stable Diffusion, ComfyUI, or other image models.
- Keep the shoe one-to-one with the source reference in all generated images.
- Styling must match the shoe style and selected scene.
- Styling must not visually overpower the shoe.
- Outfit styling may use current fashion elements when they fit the product and scene, such as light utility jacket, cropped knitwear, tennis skirt, layered socks, airy windbreaker, sheer sun-protection layer, ribbon details, balletcore accents, sporty-preppy pieces, clean city casual tailoring, or soft outdoor styling.
- Makeup and hair design must adapt to each scene. Do not repeat the same makeup and hairstyle across all three images. Use scene-appropriate variations such as natural glossy makeup, soft pink blush, clean sporty makeup, light cafe-toned makeup, fresh ponytail, half-up hair, loose waves, braided details, ribbon ponytail, hair clips, or clean bun.
- Hats are optional styling details. Add them only when they fit the scene and outfit, such as baseball cap, straw hat, beret, bucket hat, visor, or soft knit cap. Do not force every image to include a hat.
- Add personal, distinctive details where suitable: custom charms, bag pendant, shoe charm, hair clip set, small brooch, scarf tie, keychain, phone charm, bracelet stack, necklace pendant, or delicate anklet. Keep them tasteful and do not cover the shoes.
- Avoid long hems, wide pants, large bags, props, aggressive shadows, or poses that hide the shoe.
- Use a maximum of three main outfit colors and document a 60/30/10 color plan for each scene.
- Build a complete but restrained accessory layer when appropriate: watch, jewelry, hat or hair detail, bag, and one or two personalized charms. Accessories must support the character without overtaking the shoe.
- For an outdoor hiking or trail shoe set, include at least one credible mountain trail, forest path, creek, rocky terrain, or light-hiking environment. A running track or generic city park cannot replace the authentic outdoor scene.
- For an outdoor hiking or trail shoe set, use at least two long-bottom looks and three different bottom silhouettes. Do not default repeatedly to shorts or short skirts.
- Performance leggings or yoga pants are valid for outdoor footwear when the scene, weather, silhouette, and shoe function support them.

## Styling Workflow

1. Read product style, detailed functional classification, visible shoe evidence, selling points, and scene direction.
2. Invoke `spiderking-commercial-visual-stylist`; complete and approve the full commercial analysis before any generation call.
3. Select three distinct scene concepts that fit the same shoe function and selling points, with clearly different terrain, ground materials, background elements, and atmosphere.
4. For each scene, create a unique standing model look: outfit silhouette, bottom type, color ratio, materials, makeup, hairstyle, optional hat, watch, jewelry, hair details, bag, personal charms, and a non-repeating standing action.
5. Run a cross-image diversity check before generation. Reject repeated bottom silhouettes, outerwear, bag types, hair, makeup, actions, or camera angles.
6. Write one professional atmospheric scene title for each image.
7. Generate three separate 9:16 images with ChatGPT image generation, attaching or referencing the original shoe image. Do not generate a single combined preview sheet.
8. Validate shoe visibility, standing pose, non-repetition, function-scene fit, accessory completeness, scene atmosphere, and typography.
9. If any shoe detail drifts, any pose is not standing, or product function is diluted, regenerate that image before passing downstream.

## Outputs

- `scene_model_01.png`: 9:16 standing model image for scene 1.
- `scene_model_02.png`: 9:16 standing model image for scene 2.
- `scene_model_03.png`: 9:16 standing model image for scene 3.
- `styling_spec.json`: model styling, scene titles, prompts, and generation metadata.

## `styling_spec.json` Schema

```json
{
  "source_image_ref": "",
  "image_backend": "ChatGPT image generation",
  "commercial_styling_decision_ref": "commercial_styling_decision.json",
  "product_classification_snapshot": {
    "primary_category": "",
    "subcategory": "",
    "intended_activities": [],
    "terrain_or_use_context": [],
    "visible_functional_features": [],
    "fashion_attributes": []
  },
  "model_profile": {
    "market": "Chinese young female model",
    "age_range": "",
    "overall_mood": ""
  },
  "scene_images": [
    {
      "output": "scene_model_01.png",
      "aspect_ratio": "9:16",
      "scene_concept": "",
      "scene_title": "",
      "standing_pose": true,
      "outfit_design": {
        "top": "",
        "bottom": "",
        "outerwear": "",
        "colors": [],
        "materials": [],
        "fit_notes": ""
      },
      "color_plan": {
        "main_60_percent": "",
        "support_30_percent": "",
        "accent_10_percent": "",
        "main_color_count": 3
      },
      "accessories": {
        "bag": "",
        "jewelry": "",
        "hair_accessories": "",
        "necklace": "",
        "brooch_or_charms": "",
        "personalized_details": [],
        "other": []
      },
      "beauty_design": {
        "makeup": "",
        "hairstyle": "",
        "optional_hat": "",
        "hair_detail": ""
      },
      "scene_materials": {
        "ground": "",
        "background": "",
        "atmosphere": ""
      },
      "pose_and_framing": {
        "pose": "standing",
        "shoe_visibility": "",
        "camera_angle": "",
        "avoid": []
      },
      "image_prompt": ""
    }
  ],
  "non_repetition_rules": [
    "Do not repeat standing action, body direction, outfit silhouette, bag type, hairstyle, makeup design, accessories, scene mood, ground material, background type, or camera perspective across the three images."
  ],
  "consistency_constraints": [
    "以输入鞋图为唯一产品参考，鞋子本体一比一还原，不改变结构、材质、颜色、比例、Logo 和细节"
  ],
  "negative_prompt": "Do not alter the shoe. Do not cover the shoe with pants, skirt, bag, props, shadows, motion blur, or crop. Do not generate a single combined triptych, collage, grid, contact sheet, or multi-panel preview. Do not use sitting, crouching, kneeling, lying, jumping, or half-body-only poses. Do not repeat standing action, body direction, model styling, makeup, hairstyle, ground material, background type, or camera perspective across scenes. Do not make outfit colors or accessories more visually dominant than the shoe. Do not use any image model other than ChatGPT image generation."
}
```

## Standing Action Diversity Rules

- All three images must be standing, but the standing action must be different.
- Good action set examples:
  - one foot stepping forward, relaxed shopping posture;
  - side-facing standing pose, one hand holding bag strap;
  - crossed-foot fashion pose with slight turn or glance;
  - standing near a railing without leaning heavily or hiding shoes;
  - standing with one foot on a low step if both shoes remain visible.
- Do not reuse the same straight-front standing pose three times.
- Do not choose actions that hide the shoes or crop the feet.

## Scene Diversity Rules

- Generate three separate finished 9:16 image files.
- Treat ground material as a major design choice. Avoid three similar paved-floor scenes.
- Good ground/background combinations include:
  - park grass with trees and sunlight;
  - wooden bridge with water or garden background;
  - pebble path with greenery;
  - cafe tile with storefront and terrace seating;
  - clean asphalt street with shop windows;
  - city steps with architectural backdrop;
  - campus lane with tree shade.
- Do not use more than one visually similar pavement-dominant scene unless the user explicitly requests it.
- Vary viewing angle enough that the three images do not cause visual fatigue.

### Outdoor Footwear Scene Set

When the classification is hiking, trail, trekking, light outdoor, or urban outdoor, build the set from function-led concepts such as:

- Mountain Trail Progression: high-waisted performance leggings or yoga pants, quick-dry base layer, light shell, trail pack, sports watch, and sun cap on a rocky slope or forest dirt trail.
- Creekside Exploration: cuffed technical cargo trousers, functional top, light outdoor vest, bucket hat, carabiner charm, and waist bag around wooden bridges, creek stones, moss, or wetland vegetation.
- Urban Gorpcore: tapered technical trousers, cropped sun-protection layer, technical crossbody bag, metal watch, layered necklace, earrings, and one or two personal bag charms near an outdoor shop or urban mountain-style district.

Adapt colors, season, and gender to the current product. These are functional archetypes, not hardcoded outfits.

## Scene Title Rules

- Add one scene title to each 9:16 image.
- Titles should feel like professional poster typography, not plain labels.
- Keep titles short, atmospheric, and aligned with the scene mood.
- Good examples: `微光漫步`, `城市轻行`, `周末氧感`, `晴日出街`, `松弛通勤`, `午后轻闪`.
- Avoid blunt labels: `公园`, `咖啡店`, `街头`, `商场`, `校园`.
- Typography should match the image style and stay away from the shoes.

## Required Stage Summary

After completing this Skill, output:

1. Skill 目标: Generate three 9:16 different-scene standing model images for the same SpiderKing shoe.
2. 输入参数: `extracted_attributes.json`, optional `scene_spec.json`, `key_selling_points`, `shoe_reference`, optional `style_hint`.
3. 输出结果: `scene_model_01.png`, `scene_model_02.png`, `scene_model_03.png`, `styling_spec.json`.
4. 核心规则: ChatGPT image generation only; output three separate 9:16 image files; all models standing; standing action, body direction, styling, makeup, hairstyle, scene materials, background type, and viewing angle must not repeat; strong scene atmosphere; each image includes professional atmospheric scene-title typography; shoes stay one-to-one.
5. 可复用接口: `SpiderKingStylingEngine.run({ extracted_attributes, scene_spec, key_selling_points, shoe_reference, style_hint })`.
6. 与下游 Skill 的连接方式: Pass the three 9:16 scene model images and `styling_spec.json` to Layout Engine for the final brand card bottom scene section.

## Acceptance Check

Accept only if:

- Exactly three 9:16 scene model images are produced.
- The three images are separate files, not one combined preview sheet.
- Every model is standing and the shoes are clearly visible.
- Standing actions and body directions do not repeat across the three images.
- Outfit and accessories match the product style and scene.
- The approved Commercial Visual Stylist decision exists and all applicable checks pass.
- Product function remains visible in the scene and outfit logic.
- Model styling, makeup, and hairstyle do not repeat across the three images.
- Ground material, background type, and camera perspective do not repeat across the three images.
- Each image has strong scene atmosphere.
- Each image contains a professional atmospheric scene title, not a blunt location label.
- The model styling supports the shoe instead of competing with it.
- Both shoes or the featured shoe are clearly visible.
- The generated shoe details remain one-to-one with the input reference.
- Outdoor footwear sets include an authentic outdoor environment, at least two long-bottom looks, three different bottom silhouettes, and no repeated short-skirt/shorts default.
- Each look has an intentional accessory hierarchy and a valid 60/30/10 color plan without exceeding three main colors.
