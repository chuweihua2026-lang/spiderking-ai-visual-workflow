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
- `scene_spec.json` or scene direction from Scene Engine, if available.
- `key_selling_points`: shoe selling points from Product Vision or main poster copy.
- `shoe_reference`: original shoe image or validated product reference.
- Optional `style_hint`: campaign mood, customer profile, season, or store channel.

## Hard Rules

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

## Styling Workflow

1. Read product style, visible shoe details, selling points, and scene direction.
2. Select three distinct scene concepts that fit the same shoe and selling points, with clearly different ground materials, background elements, and atmosphere.
3. For each scene, create a unique standing model look: outfit, color palette, makeup, hairstyle, optional hat, jewelry, hair accessories, necklace, brooch or charms, bag, personal decorative details, and a non-repeating standing action.
4. Write one professional atmospheric scene title for each image.
5. Generate three separate 9:16 images with ChatGPT image generation, attaching or referencing the original shoe image. Do not generate a single combined preview sheet.
6. Validate shoe visibility, standing pose, non-repetition, scene atmosphere, and typography.
7. If any shoe detail drifts or any pose is not standing, regenerate that image before passing downstream.

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
- Model styling, makeup, and hairstyle do not repeat across the three images.
- Ground material, background type, and camera perspective do not repeat across the three images.
- Each image has strong scene atmosphere.
- Each image contains a professional atmospheric scene title, not a blunt location label.
- The model styling supports the shoe instead of competing with it.
- Both shoes or the featured shoe are clearly visible.
- The generated shoe details remain one-to-one with the input reference.
