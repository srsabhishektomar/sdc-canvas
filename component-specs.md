# Component Specifications

## Event Hero

**Purpose:** Present the event identity and primary actions.

**Canvas inputs**
- `eyebrow`: uppercase small heading
- `title`: display heading
- `description`: editable rich prose
- `date_label`: event date
- `location_label`: venue and city, preserving a line break
- `primary_action_label` / `primary_action_url`
- `secondary_action_label` / `secondary_action_url`
- `media_url`: image asset or Drupal media URL

**Composition:** Two-column section on desktop, stacked on narrow screens. Text and media occupy independent regions so the editor can update copy or replace the image without changing layout code.

## Audience Card

**Purpose:** Link a food-community audience to resources.

**Canvas inputs**
- `title`
- `description`
- `link_label`
- `link_url`
- `image_url`
- `icon_url`

**Composition:** Image, overlapping circular icon, and text panel. The card is designed as an isolated reusable unit rather than a hard-coded page section.

## Audience Card Grid

**Purpose:** Arrange audience cards responsively.

**Canvas slot**
- `cards`: audience-card components

**Composition:** Four columns at desktop, two columns at tablet, and one column on small mobile widths.

## Shared Design Decisions

- Poppins is used for headings and body copy.
- IvyPresto Display is used for the event title.
- The supplied source tokens establish the honey, cream, border, radius, and content-width values.
- Orange, cream, and icon colors from the design remain theme constants, while content and links are component props.
- Font Awesome supplies familiar event metadata icons; the supplied PNG assets supply the four audience icons.
- The hero and card sections are separate components so an editor can reorder, duplicate, replace, or remove content in Canvas.

## Assumptions and Deviations

- The exact date copy in the supplied design reads January 17–19, 2027; the heading says 2028. The submitted copy preserves the design reference exactly.
- The standalone prototype provides direct visual validation. The Drupal module uses the same component boundaries and is installed in the local DXP environment.
- The card grid defaults to 4 desktop columns to match the reference and exposes 1, 2, 3, or 4 desktop columns in the Canvas property editor. It becomes 2 columns below 900px and 1 column below 540px.
- Drupal Canvas 1.13 is enabled and all three SDCs pass Canvas eligibility checks and generate Canvas component config entities. No page template or hard-coded page render array was added to the module; the page can be assembled in Canvas.
