# Transparent PNG Skill

A reusable Codex Skill for converting or editing images into true transparent-background RGBA PNG assets.

## Features

- True RGBA PNG output
- Real Alpha transparency
- No white background
- No gray background
- No background mask
- No baked-in checkerboard pattern
- Preservation of original subject and design
- Anti-aliased edge preservation
- Protection of legitimate white elements inside the subject

## Use Cases

Useful for:

- Logos
- Chinese calligraphy
- Stamps and seals
- UI assets
- WeChat Mini Program assets
- Decorative elements
- Typography assets
- Icons
- Illustration elements
- Image-generation post-processing

## Repository Structure

```text
transparent-png-skill/
├── SKILL.md
├── README.md
└── LICENSE
```

## Installation

Clone the repository into the location where your Codex Skills are managed:

```bash
git clone https://github.com/YOUR_USERNAME/transparent-png-skill.git
```

Then make sure the Skill directory contains:

```text
transparent-png-skill/
└── SKILL.md
```

The `SKILL.md` file contains the actual Skill instructions.

## Basic Usage

When working with an image, request:

```text
Convert this image to a true transparent-background RGBA PNG.
```

The Skill instructs the agent to:

1. Preserve the original subject.
2. Remove only the background.
3. Preserve legitimate white elements.
4. Preserve anti-aliased edges.
5. Ensure a real Alpha channel.
6. Avoid white or simulated transparent backgrounds.

## Default Prompt

```text
Export this image as a true RGBA PNG with a fully transparent background.

Remove only the background and preserve the subject, typography, colors, texture, borders, proportions, and all original visual details.

Do not add white pixels, a background mask, a white background, or checkerboard pixels.

Preserve legitimate white elements inside the subject.

Ensure the final PNG contains a real Alpha channel with transparent background pixels set to Alpha=0.
```

## Expected Output

A correct output should behave as:

```text
PNG
└── RGBA
    ├── R
    ├── G
    ├── B
    └── A
```

The background should have:

```text
Alpha = 0
```

rather than:

```text
RGB(255,255,255), Alpha=255
```

## Important

Do not commit sensitive information to this repository.

Never include:

- SSH private keys
- Passwords
- API keys
- Access tokens
- Cloud credentials
- Personal secrets

## License

MIT License.