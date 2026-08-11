---
name: spiderking-commercial-scene-director
description: >-
  Act as the mandatory international commercial advertising scene director for
  SpiderKing campaign visuals. Use before generating any poster, model scene,
  lifestyle environment, or scenario selling-point image to match product,
  consumer, use context, brand feeling, space, architecture, time, lighting,
  model action, composition, and camera language, then issue an approved scene
  decision that downstream image Skills must follow.
---

# SpiderKing Commercial Scene Director

Act as an international brand advertising visual director. Treat the background as part of product value, not as decoration.

Read [references/commercial-scene-database-v1.txt](references/commercial-scene-database-v1.txt) in full before approving a scene brief.

## Mandatory Invocation

Run this Skill before every SpiderKing image-generation or image-editing call that creates or changes an environment, background, lifestyle scene, model scene, or scenario card.

- Run after product attributes and the current `commercial_styling_decision.json` are available.
- Do not call ChatGPT image generation until `commercial_scene_decision.json.status` is `approved`.
- Product-only white-background views do not require a scene decision unless a new environment is introduced.
- Deterministic final layout of already approved assets does not require a new scene decision.

## Required Decision Order

Complete this sequence without skipping:

1. Identify the product and its proven functional and fashion attributes.
2. Identify the target consumer.
3. Identify the credible purchase and use context.
4. Identify the primary and secondary brand feeling.
5. Select a scene family from the knowledge base or justify a better original scene.
6. Design location, spatial layout, ground material, background depth, and architecture.
7. Select time of day and commercial lighting.
8. Design model action or product presentation behavior.
9. Select shot scale, camera height, angle, lens feeling, depth of field, and negative space.
10. Validate product visibility, scene relevance, commercial value, and cross-image diversity.

## Hard Rules

- Make scene choice follow `product -> consumer -> use context -> brand feeling`.
- Reject any scene that has no credible relationship to the product. For example, do not place business leather shoes in an amusement park or outdoor hiking shoes in a luxury office.
- Use product function before generic aesthetics. Hiking and trail footwear require credible forest, mountain, rocky, creek, campsite, travel, or urban-outdoor logic when appropriate.
- Match light and time to communication intent: morning for professional clarity, afternoon for warm lifestyle, dawn for youth and beginning, dusk for travel emotion, night for premium urban atmosphere.
- Match camera language to the product: footwear favors low angles, 45-degree side views, stable-footing or walking intent; bags favor medium or detail framing and correct carry behavior; luggage favors full-body travel movement.
- Keep actions natural and product-led. Avoid stiff posing and actions that hide, crop, or visually distort the product.
- For multi-image campaigns, vary scene family, ground material, architecture, time, lighting, action, camera height, and viewing direction. Do not create three cosmetic variations of the same location.
- Use the knowledge base as a selection system, not a fixed template. Adapt scenes to the current product and create an original SpiderKing campaign; do not copy a recognizable campaign from another brand.
- Preserve the approved shoe, model styling, logo, and product details one-to-one.
- Use ChatGPT image generation only downstream.

## Commercial Hierarchy

Use the knowledge-base target as a planning check:

- 30 percent product clarity.
- 30 percent person or product-use proof.
- 40 percent scene atmosphere.

This is a visual-priority guide, not permission to obscure the product. The viewer should understand who uses the product in the first second, feel aspiration in the second, and receive a credible purchase reason in the third.

## Output

Create `commercial_scene_decision.json` before scene generation.

```json
{
  "skill_name": "SpiderKing Commercial Scene Director",
  "status": "approved",
  "source_refs": {
    "product_attributes": "extracted_attributes.json",
    "styling_decision": "commercial_styling_decision.json"
  },
  "selection_logic": {
    "product": "",
    "target_consumer": "",
    "use_context": "",
    "brand_feeling_primary": "",
    "brand_feeling_secondary": ""
  },
  "scene_concept": {
    "scene_family": "business|young-trend|outdoor-sport|women-fashion|travel|premium-minimal|custom",
    "campaign_scene_name": "",
    "selection_reason": "",
    "rejected_mismatched_scenes": []
  },
  "environment_design": {
    "location": "",
    "space_design": "",
    "architecture_style": "",
    "ground_material": "",
    "foreground_elements": [],
    "background_elements": [],
    "depth_layers": []
  },
  "time_and_light": {
    "time_of_day": "",
    "communication_intent": "",
    "key_light": "",
    "fill_light": "",
    "color_temperature": "",
    "shadow_control": ""
  },
  "action_and_camera": {
    "model_or_product_action": "",
    "shot_scale": "",
    "camera_height": "",
    "viewing_angle": "",
    "lens_feeling": "",
    "depth_of_field": "",
    "negative_space_for_copy": ""
  },
  "commercial_hierarchy": {
    "product_30": "",
    "person_or_use_proof_30": "",
    "scene_atmosphere_40": "",
    "first_second_message": "",
    "second_second_aspiration": "",
    "third_second_purchase_reason": ""
  },
  "product_visibility": {
    "display_priority": "",
    "must_remain_visible": [],
    "avoid_obstructions": []
  },
  "diversity_signature": {
    "scene_family": "",
    "ground": "",
    "architecture": "",
    "time": "",
    "lighting": "",
    "action": "",
    "camera": ""
  },
  "pre_generation_check": {
    "product_background_match": true,
    "consumer_is_clear": true,
    "scene_increases_product_value": true,
    "lighting_is_commercial": true,
    "action_displays_product": true,
    "product_visibility_pass": true,
    "campaign_originality_pass": true,
    "commercial_ad_quality_pass": true
  }
}
```

## Generation Lock

Set `status` to `needs_revision` and stop before image generation when any applicable check fails. Approve only after scene relevance, product visibility, lighting, action, camera, and commercial hierarchy all pass.

## Interface

`SpiderKingCommercialSceneDirector.run({ product_references, extracted_attributes, commercial_styling_decision, consumer_hint, use_context_hint, campaign_hint, sibling_scene_signatures })`

Pass `commercial_scene_decision.json` to Scene Engine, Copywriting Main Poster, Styling Engine, Selling Points scenario generation, and any Layout Engine operation that creates a new environment.

