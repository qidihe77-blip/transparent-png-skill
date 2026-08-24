---
name: transparent-png
description: Convert or edit images into true transparent-background RGBA PNG assets. Use when the user requests transparent background, background removal, PNG transparency, Alpha channel preservation, or export of image assets with no white background.
---

# Transparent PNG Skill

## Purpose

Convert or edit an image so that it becomes a true transparent-background PNG while preserving the original subject and visual design.

The output must use a real Alpha channel rather than a white, gray, or simulated transparent background.

## Core Requirements

When processing an image for transparent PNG output:

1. Output format must be PNG.
2. Output must contain an Alpha channel.
3. Background areas must be fully transparent.
4. Transparent background pixels must have `Alpha = 0`.
5. Do not add a white background.
6. Do not add a gray background.
7. Do not add a background mask.
8. Do not use a checkerboard pattern as the actual image background.
9. Preserve the original subject, typography, texture, border, proportions, and visual details.
10. Do not redesign elements that the user did not ask to change.

## Default Image Prompt

Use the following prompt when an image-generation or image-editing model needs an explicit instruction:

> Convert this image into a true RGBA PNG with a fully transparent background.
>
> Remove only the background and make the background area fully transparent. Do not add white pixels, gray pixels, a background layer, a background mask, or a checkerboard pattern.
>
> Preserve the original subject, typography, texture, border, proportions, position, colors, and all existing visual details.
>
> Do not modify the design unless explicitly requested.
>
> Preserve natural anti-aliased edges and avoid white halos or unwanted edge artifacts.
>
> If the subject itself contains white elements, preserve those white elements and remove only the actual background.
>
> The final image must contain a real Alpha channel, with transparent background pixels using `Alpha = 0`.

## Transparency Requirements

A correct transparent PNG should conceptually contain:

```text
PNG
└── RGBA
    ├── Red
    ├── Green
    ├── Blue
    └── Alpha
```

Background:

```text
Alpha = 0
```

Incorrect examples:

```text
White background:
RGB(255,255,255), Alpha=255

Fake transparency:
Checkerboard pixels stored in the image

Correct transparency:
Background Alpha=0
```

## Edge Preservation

When removing the background:

- Preserve anti-aliased edges.
- Avoid white halos.
- Avoid jagged edges.
- Do not unnecessarily erode the subject.
- Do not remove legitimate white elements belonging to the subject.
- Do not change typography or decorative details.

## Preservation Rules

Unless explicitly requested, preserve:

- Subject
- Text
- Font style
- Font weight
- Typography layout
- Colors
- Texture
- Borders
- Decorative elements
- Proportions
- Position
- Composition

Only the background transparency should be changed.

## Forbidden Changes

Do not:

- Add a white background.
- Add a gray background.
- Add a colored background.
- Add a gradient background.
- Add a background rectangle.
- Add a background mask.
- Add a shadow plate behind the subject.
- Add a checkerboard pattern as image pixels.
- Change the subject's colors.
- Change the font.
- Change the subject's proportions.
- Redesign the composition.
- Remove white elements that belong to the subject.

## Output Validation

After processing, verify:

1. File extension is `.png`.
2. Image mode is RGBA or equivalent.
3. Alpha channel exists.
4. Background pixels are transparent.
5. No unintended white background remains.
6. No checkerboard pixels are baked into the image.
7. Subject edges do not contain obvious white halos.
8. Original subject details remain intact.

## User Request Mapping

If the user says:

### "透明背景"

Use the default transparent PNG prompt.

### "真正透明背景"

Explicitly require:

```text
True RGBA PNG
Alpha channel
Background Alpha=0
No white pixels in background
```

### "去掉白底"

Remove the white background while preserving legitimate white elements inside the subject.

### "导出透明 PNG"

Output a real RGBA PNG rather than a flattened RGB PNG.

### "透明背景，其余不变"

Do not modify any visual element except the background transparency.

## Minimal Prompt

For simple requests, use:

> Export this image as a true RGBA PNG with a fully transparent background. Remove only the background and preserve the subject, typography, colors, texture, borders, proportions, and all original visual details. Do not add white pixels, a background mask, a white background, or checkerboard pixels. Preserve legitimate white elements inside the subject. Ensure the final PNG contains a real Alpha channel with transparent background pixels set to Alpha=0.