# SDC Canvas module

## Purpose

`SDC Canvas` provides reusable Drupal Single Directory Components for a Winter FancyFaire event page and makes them available to Drupal Canvas.

The module separates presentation into independently configurable components:

- `sdc_canvas:event-hero` - event copy, date/location metadata, and a hero image.
- `sdc_canvas:button` - a reusable call-to-action link with primary and secondary styles.
- `sdc_canvas:audience-card` - one image-and-text audience resource card.
- `sdc_canvas:audience-grid` - a responsive container with a slot for Audience Card components.

## Dependencies

- Drupal core 10 or 11
- Drupal SDC
- Drupal Canvas

The module declares `drupal:sdc` and `drupal:canvas` dependencies in `sdc_canvas.info.yml`.

## Libraries

- `sdc_canvas/fonts` loads the supplied Adobe Fonts stylesheet and Font Awesome Free 6.7.2 from external CDNs.
- `sdc_canvas/global` attaches the shared SDC styles and component-specific CSS.

Component metadata attaches `sdc_canvas/global`, which also loads the fonts library. This keeps the standalone and Drupal-rendered implementations visually consistent.

## Components

### Event Hero

Machine ID: `sdc_canvas:event-hero`

Group: `Marketing/Hero`

Available props:

- `eyebrow`
- `title` - required
- `description`
- `date_label`
- `location_label`
- `image_url` - image prop; select the hero image from the Media Library

The `actions` slot accepts multiple nested `sdc_canvas:button` components. They display in a row and wrap onto additional lines when needed.

The required `title` prop has a Canvas-compatible first example. Its CSS uses a 46.4/53.6 split desktop layout and stacks below 900px.

### Button

Machine ID: `sdc_canvas:button`

Props:

- `label` - required button text
- `url` - destination URL
- `type` - `primary` or `secondary`; defaults to `secondary`

### Audience Card

Machine ID: `sdc_canvas:audience-card`

Group: `Marketing/Card`

Available props:

- `title` - required
- `description`
- `link_label`
- `link_url`
- `image_url` - image prop; select the card image from the Media Library
- `icon_url` - image prop; select the card icon from the Media Library

The card is a reusable unit and should be instantiated independently or placed inside the Audience Card Grid slot.
`link_url` is the card destination; image and icon props use Canvas's image shape, rather than URL text inputs.

### Audience Card Grid

Machine ID: `sdc_canvas:audience-grid`

Group: `Container`

Available props:

- `columns` - integer enum of 1, 2, 3, or 4; defaults to 4

Available slots:

- `cards` - Audience Card component instances

The CSS renders 4 desktop columns by default, 2 columns below 900px, and 1 column below 540px.

## Drupal Canvas use

1. Enable `canvas` and `sdc_canvas`.
2. Rebuild Drupal caches.
3. Open `/admin/appearance/component/status` and verify the three SDCs are enabled.
4. Open Canvas and place Event Hero and Audience Card Grid components.
5. Add Audience Card components to the grid's `cards` slot.
6. Configure titles, descriptions, and links in Canvas's component form; choose hero and card images and card icons from the Media Library.

Canvas 1.13 automatically creates component config entities for eligible SDCs. The three config entity IDs are:

- `canvas.component.sdc.sdc_canvas.event-hero`
- `canvas.component.sdc.sdc_canvas.button`
- `canvas.component.sdc.sdc_canvas.audience-card`
- `canvas.component.sdc.sdc_canvas.audience-grid`

## Validation

Validated against Drupal 11.4.13 and Drupal Canvas 1.13:

- All three SDC plugin definitions are discoverable.
- All three pass Canvas's component requirements checker.
- All three have generated Canvas component config entities.
- Adobe Fonts and Font Awesome libraries are discoverable.
- All three components render through Drupal's `#type: component` renderer.
- The 4-card Audience Grid renders 4 `<article>` elements.

## Assets

Supplied assets are stored under:

- `assets/images/`
- `assets/icons/`

