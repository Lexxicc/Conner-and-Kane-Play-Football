# Flux Headshot Prompt - Template 

Duplicate this file per player (e.g. `beckham-2006.md`, `henry-2004.md`), fill the `{placeholders}`, paste into Flux.

Output feeds the DFF/FB/PK player card pipeline: generate -> flood-fill background removal (PIL, threshold 40) -> save as `* Headshot Transparent.png` -> point card `<img src>` at the transparent version.

---

## Real footballer (2000-2012 era)

```
Photorealistic studio headshot of {PLAYER NAME}, the {NATIONALITY} footballer,
circa {YEAR} during his time at {CLUB FROM THAT ERA}.
Head and upper shoulders only. Centred, head-on to camera, looking directly into lens.
Warm, confident open-mouth smile showing teeth, friendly and approachable, slight forward lean.
Wearing the {YEAR} {CLUB} home kit.
Background: pure solid matte black, completely flat, no gradient, no spotlight halo
behind the head, no studio backdrop texture, no shadow fade.
Lighting: flat even front-facing key light. No rim light. No back light.
No light bleed onto the background.
Era-accurate hairstyle, build, and face for {YEAR}.
Sharp focus on facial features, high detail skin and hair texture,
professional sports photography style. Square crop, 1:1 aspect ratio, high resolution.
```

## Custom character

```
Photorealistic studio headshot of a {AGE} {ETHNICITY} {GENDER},
{PHYSICAL DESCRIPTION: hair, build, distinguishing features}.
Head and upper shoulders only. Centred, head-on to camera, looking directly into lens.
Warm, confident open-mouth smile showing teeth, friendly and approachable, slight forward lean.
Wearing {KIT or CLOTHING DESCRIPTION}.
Background: pure solid matte black, completely flat, no gradient, no spotlight halo
behind the head, no studio backdrop texture, no shadow fade.
Lighting: flat even front-facing key light. No rim light. No back light.
No light bleed onto the background.
Sharp focus on facial features, high detail skin and hair texture,
professional sports photography style. Square crop, 1:1 aspect ratio, high resolution.
```

---

## Non-negotiable lines (keep these, they're what makes the transparent-PNG step painless)

- `pure solid matte black, completely flat, no gradient, no spotlight halo` - studio default is a soft vignette that flood-fill leaks through
- `no rim light, no back light, no light bleed onto the background` - rim light leaves a mid-grey halo around hair/shoulders that escapes the threshold-40 catch
- `era-accurate hairstyle, build, and face for {YEAR}` - Flux defaults to modern look without this

## Field cheatsheet

- `{YEAR}` - pick the player's peak year in 2000-2012 window
- `{CLUB FROM THAT ERA}` - their primary club that year (anchors face, hair, build to the right period)
- `{NATIONALITY}` - helps Flux narrow features (e.g. "Brazilian", "French", "English")
- Kit - either era-accurate club kit (locks them to that club) or `plain dark training top` (reusable across club chips on the card)
