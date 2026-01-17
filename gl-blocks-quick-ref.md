# GL Page Builder Quick Reference

Fast lookup for GL Page Builder block creation.

## Block Structure

```html
<!-- wp:greenshift-blocks/element {JSON} -->
<tag class="gsbp-{id}">content</tag>
<!-- /wp:greenshift-blocks/element -->
```

## Required Attributes

| Attribute | Format | Notes |
|-----------|--------|-------|
| `id` | `gsbp-{7 alphanumeric}` | Unique identifier |
| `localId` | Same as `id` | Must match `id` |
| `tag` | HTML tag name | Optional, defaults to `div` |
| `type` | `text`, `inner`, `no` | Content type |

## Content Types

- **`text`** or omit - Text only, needs `textContent`
- **`inner`** - Contains nested blocks
- **`no`** - Empty/decorative element
- **`chart`** - ApexCharts data

## styleAttributes Format

```json
{
  "styleAttributes": {
    "property": ["desktop", "tablet", "mobile_l", "mobile_p"],
    "property_hover": ["value"],
    "property_focus": ["value"]
  }
}
```

Single value = all breakpoints: `"padding": ["20px"]`

## Common Style Properties

### Spacing
```json
"paddingTop": ["20px"]
"paddingBottom": ["20px"]
"paddingLeft": ["20px"]
"paddingRight": ["20px"]
"marginTop": ["20px"]
"marginBottom": ["20px"]
```

### Typography
```json
"fontSize": ["16px"]
"fontWeight": ["600"]
"lineHeight": ["1.5"]
"textAlign": ["center"]
"textDecoration": ["none"]
"color": ["#333"]
```

### Layout
```json
"display": ["flex"]
"flexDirection": ["row"]
"justifyContent": ["center"]
"alignItems": ["center"]
"flexWrap": ["wrap"]
"columnGap": ["20px"]
"rowGap": ["20px"]
```

### Box Model
```json
"width": ["100%"]
"height": ["auto"]
"maxWidth": ["1200px"]
"minHeight": ["300px"]
"backgroundColor": ["#fff"]
"borderRadius": ["10px"]
"boxShadow": ["0 4px 6px rgba(0,0,0,0.1)"]
"overflow": ["hidden"]
```

### Position
```json
"position": ["relative"]
"top": ["0px"]
"left": ["0px"]
"zIndex": ["10"]
```

### Transform
```json
"transform": ["translateY(-10px)"]
"transform_hover": ["scale(1.05)"]
"transition": ["all 0.3s ease"]
```

## Flex Columns

```json
"flexColumns_Extra": 2,
"flexWidths_Extra": {
  "desktop": {"name": "50/50", "widths": [50, 50]},
  "tablet": {"name": "50/50", "widths": [50, 50]},
  "mobile": {"name": "100/100", "widths": [100, 100]}
}
```

## Link Attributes

| Attribute | Type | Output |
|-----------|------|--------|
| `href` | string | `href="url"` |
| `linkNewWindow` | true | `target="_blank" rel="noopener"` |
| `linkNoFollow` | true | `rel="nofollow"` |
| `linkSponsored` | true | `rel="sponsored"` |

## Image Attributes

```json
{
  "tag": "img",
  "src": "https://placehold.co/800x600",
  "alt": "Description",
  "originalWidth": 800,
  "originalHeight": 600
}
```

## Form Attributes

```json
{
  "tag": "button",
  "formAttributes": {
    "type": "submit",
    "name": "fieldname"
  }
}
```

## Dynamic Attributes

```json
{
  "dynamicAttributes": [
    {"name": "data-type", "value": "component"},
    {"name": "aria-label", "value": "Description"}
  ]
}
```

## SVG Icon

```json
{
  "tag": "svg",
  "icon": {
    "icon": {
      "svg": "<svg viewBox=\"0 0 24 24\"><path d=\"...\"/></svg>",
      "image": ""
    },
    "fill": "currentColor",
    "type": "svg"
  }
}
```

## Gradient Background

```json
{
  "imageGradient_Extra": true,
  "backgroundImage": ["linear-gradient(135deg, #667eea 0%, #764ba2 100%)"]
}
```

## Text Gradient

```json
{
  "imageGradient_Extra": true,
  "backgroundImage": ["linear-gradient(135deg, #667eea 0%, #764ba2 100%)"],
  "backgroundClip": ["text"],
  "color": ["transparent"]
}
```

## CSS Animation

```json
{
  "animation_keyframes_Extra": [
    {"name": "gs_fade", "code": "0%{opacity:0;}100%{opacity:1;}"}
  ],
  "animation": ["gs_fade 0.5s ease forwards"]
}
```

## Scroll Animation

```json
{
  "animation_keyframes_Extra": [{"name": "gs_reveal", "code": "0%{opacity:0;}100%{opacity:1;}"}],
  "animation": ["gs_reveal linear both"],
  "animationTimeline": ["view()"],
  "animationRange": ["entry"]
}
```

## CSS Variables

### Font Sizes
- `var(--wp--preset--font-size--xs, 0.85rem)`
- `var(--wp--preset--font-size--s, 1rem)`
- `var(--wp--preset--font-size--r, 1.2rem)`
- `var(--wp--preset--font-size--m, 1.35rem)`
- `var(--wp--preset--font-size--l, 1.55rem)`
- `var(--wp--preset--font-size--xl)`
- `var(--wp--preset--font-size--xxl)`
- `var(--wp--preset--font-size--giga)`

### Spacing
- `var(--wp--preset--spacing--20, 0.44rem)`
- `var(--wp--preset--spacing--30, 0.67rem)`
- `var(--wp--preset--spacing--40, 1rem)`
- `var(--wp--preset--spacing--50, 1.5rem)`
- `var(--wp--preset--spacing--60, 2.25rem)`
- `var(--wp--preset--spacing--70, 3.38rem)`

### Border Radius
- `var(--wp--custom--border-radius--mini, 5px)`
- `var(--wp--custom--border-radius--small, 10px)`
- `var(--wp--custom--border-radius--medium, 15px)`
- `var(--wp--custom--border-radius--large, 20px)`

### Shadows
- `var(--wp--preset--shadow--soft)`
- `var(--wp--preset--shadow--elegant)`
- `var(--wp--preset--shadow--highlight)`

### Transitions
- `var(--wp--custom--transition--ease)`
- `var(--wp--custom--transition--creative)`
- `var(--wp--custom--transition--soft)`

## Dynamic Content

### Post Data
```json
{
  "dynamictext": {
    "dynamicEnable": true,
    "dynamicType": "postdata",
    "dynamicSource": "latest_item",
    "dynamicPostData": "post_title"
  }
}
```

### Post Data Options
`post_title`, `post_image`, `post_date`, `post_excerpt`, `permalink`, `post_author`, `comment_count`

### Taxonomy
```json
{
  "dynamictext": {
    "dynamicEnable": true,
    "dynamicType": "taxonomyvalue",
    "dynamicTaxonomyValue": "category",
    "dynamicTaxonomyLink": true
  }
}
```

### Custom Field
```json
{
  "dynamictext": {
    "dynamicEnable": true,
    "dynamicType": "custom",
    "dynamicField": "field_name"
  }
}
```

## Placeholders

- `{{POST_ID}}`, `{{POST_TITLE}}`, `{{POST_URL}}`
- `{{AUTHOR_ID}}`, `{{AUTHOR_NAME}}`
- `{{CURRENT_USER_ID}}`, `{{CURRENT_USER_NAME}}`
- `{{META:meta_key}}`, `{{GET:param}}`
- `{{SITE_URL}}`, `{{CURRENT_DATE_YMD}}`

## isVariation Values

| Value | Purpose |
|-------|---------|
| `contentwrapper` | Full-width section |
| `contentcolumns` | Section with columns |
| `contentarea` | Flex column container |
| `nocolumncontent` | Single content area |
| `divtext` | Text block |
| `buttoncomponent` | Themed button |
| `accordion` | Accordion container |
| `tabs` | Tabs container |
| `counter` | Animated counter |
| `countdown` | Countdown timer |
| `marquee` | Marquee/scroll text |
| `videolightbox` | Video lightbox |
| `chart` | ApexCharts |
| `youtubeplay` | YouTube embed |
| `vimeoplay` | Vimeo embed |

## Output Rules

1. Block name: `wp:greenshift-blocks/element`
2. `id` and `localId` must match
3. Add `localId` to class when styled
4. Use `loading="lazy"` on images
5. Remove `xmlns` from SVG
6. Escape quotes in JSON: `\u0022`
7. Use CSS variables over hardcoded values
