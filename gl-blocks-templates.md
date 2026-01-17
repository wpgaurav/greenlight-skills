# GL Page Builder Template Creation

Create ready-to-paste WordPress block markup for GL Page Builder (GreenLight/Greenshift). Output valid block code that can be copied directly into the WordPress editor.

## Core Block Structure

Every GL block follows this format:

```html
<!-- wp:greenshift-blocks/element {JSON_ATTRIBUTES} -->
<html_tag class="gsbp-{id}">Content</html_tag>
<!-- /wp:greenshift-blocks/element -->
```

## ID Generation

Generate unique IDs with format `gsbp-{7 alphanumeric characters}`:
- `id` and `localId` must be identical
- Example: `gsbp-a1b2c3d`

## Block Types

### Text Block
```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-abc1234","textContent":"Your text here","localId":"gsbp-abc1234","styleAttributes":{"fontSize":["var(--wp--preset--font-size--r, 1.2rem)"]}} -->
<div class="gsbp-abc1234">Your text here</div>
<!-- /wp:greenshift-blocks/element -->
```

### Heading Block
```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-def5678","textContent":"Heading Text","tag":"h2","localId":"gsbp-def5678","styleAttributes":{"fontSize":["var(--wp--preset--font-size--xl, clamp(1.6rem, 2.75vw, 1.9rem))"],"fontWeight":["700"],"marginBottom":["var(--wp--preset--spacing--50, 1.5rem)"]}} -->
<h2 class="gsbp-def5678">Heading Text</h2>
<!-- /wp:greenshift-blocks/element -->
```

### Container Block (for nesting)
```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-ghi9012","type":"inner","localId":"gsbp-ghi9012","styleAttributes":{"padding":["var(--wp--preset--spacing--50, 1.5rem)"],"backgroundColor":["#f5f5f5"],"borderRadius":["var(--wp--custom--border-radius--medium, 15px)"]}} -->
<div class="gsbp-ghi9012">
<!-- nested blocks here -->
</div>
<!-- /wp:greenshift-blocks/element -->
```

### Image Block
```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-jkl3456","tag":"img","localId":"gsbp-jkl3456","src":"https://placehold.co/800x600","alt":"Description","originalWidth":800,"originalHeight":600,"styleAttributes":{"width":["100%"],"height":["auto"],"objectFit":["cover"],"borderRadius":["var(--wp--custom--border-radius--small, 10px)"]}} -->
<img class="gsbp-jkl3456" src="https://placehold.co/800x600" alt="Description" width="800" height="600" loading="lazy"/>
<!-- /wp:greenshift-blocks/element -->
```

### Link/Button Block
```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-mno7890","textContent":"Click Here","tag":"a","localId":"gsbp-mno7890","href":"https://example.com","styleAttributes":{"display":["inline-block"],"paddingTop":["var(--wp--preset--spacing--40, 1rem)"],"paddingBottom":["var(--wp--preset--spacing--40, 1rem)"],"paddingLeft":["var(--wp--preset--spacing--60, 2.25rem)"],"paddingRight":["var(--wp--preset--spacing--60, 2.25rem)"],"backgroundColor":["var(--wp--preset--color--brand, #33EFAB)"],"borderRadius":["var(--wp--custom--border-radius--medium, 15px)"],"textDecoration":["none"],"color":["#000"],"backgroundColor_hover":["var(--wp--preset--color--brand-hover, #7AFFCE)"]}} -->
<a class="gsbp-mno7890" href="https://example.com">Click Here</a>
<!-- /wp:greenshift-blocks/element -->
```

### SVG Icon Block
```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-pqr1234","tag":"svg","icon":{"icon":{"svg":"<svg viewBox=\"0 0 24 24\" xmlns=\"http://www.w3.org/2000/svg\"><path d=\"M12 2L2 7l10 5 10-5-10-5zM2 17l10 5 10-5M2 12l10 5 10-5\"/></svg>","image":""},"fill":"currentColor","type":"svg"},"localId":"gsbp-pqr1234","styleAttributes":{"width":["24px"],"height":["24px"],"color":["currentColor"]}} -->
<svg viewBox="0 0 24 24" width="24" height="24" class="gsbp-pqr1234"><path d="M12 2L2 7l10 5 10-5-10-5zM2 17l10 5 10-5M2 12l10 5 10-5"/></svg>
<!-- /wp:greenshift-blocks/element -->
```

## Layout Templates

### Full-Width Section with Centered Content
```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-sec1234","tag":"section","type":"inner","localId":"gsbp-sec1234","align":"full","dynamicAttributes":[{"name":"data-type","value":"section-component"}],"styleAttributes":{"display":["flex"],"justifyContent":["center"],"flexDirection":["column"],"alignItems":["center"],"paddingRight":["var(--wp--custom--spacing--side, min(3vw, 20px))"],"paddingLeft":["var(--wp--custom--spacing--side, min(3vw, 20px))"],"paddingTop":["var(--wp--preset--spacing--70, 3.38rem)"],"paddingBottom":["var(--wp--preset--spacing--70, 3.38rem)"],"position":["relative"]},"isVariation":"contentwrapper"} -->
<section class="gsbp-sec1234 alignfull" data-type="section-component"><!-- wp:greenshift-blocks/element {"id":"gsbp-cnt5678","type":"inner","localId":"gsbp-cnt5678","dynamicAttributes":[{"name":"data-type","value":"content-area-component"}],"styleAttributes":{"maxWidth":["100%"],"width":["var(--wp--style--global--wide-size, 1200px)"]},"isVariation":"nocolumncontent","metadata":{"name":"Content Area"}} -->
<div class="gsbp-cnt5678" data-type="content-area-component">
<!-- Content goes here -->
</div>
<!-- /wp:greenshift-blocks/element --></section>
<!-- /wp:greenshift-blocks/element -->
```

### Two-Column Layout
```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-col1234","tag":"section","type":"inner","localId":"gsbp-col1234","align":"full","dynamicAttributes":[{"name":"data-type","value":"section-component"}],"styleAttributes":{"display":["flex"],"justifyContent":["center"],"flexDirection":["column"],"alignItems":["center"],"paddingRight":["var(--wp--custom--spacing--side, min(3vw, 20px))"],"paddingLeft":["var(--wp--custom--spacing--side, min(3vw, 20px))"],"paddingTop":["var(--wp--preset--spacing--70, 3.38rem)"],"paddingBottom":["var(--wp--preset--spacing--70, 3.38rem)"],"position":["relative"]},"isVariation":"contentcolumns"} -->
<section class="gsbp-col1234 alignfull" data-type="section-component"><!-- wp:greenshift-blocks/element {"id":"gsbp-row5678","type":"inner","localId":"gsbp-row5678","dynamicAttributes":[{"name":"data-type","value":"content-area-component"}],"styleAttributes":{"maxWidth":["100%"],"width":["var(--wp--style--global--wide-size, 1200px)"],"display":["flex"],"flexColumns_Extra":2,"flexWidths_Extra":{"desktop":{"name":"50/50","widths":[50,50]},"tablet":{"name":"50/50","widths":[50,50]},"mobile":{"name":"100/100","widths":[100,100]}},"flexDirection":["row"],"columnGap":["var(--wp--preset--spacing--50, 1.5rem)"],"rowGap":["var(--wp--preset--spacing--50, 1.5rem)"],"flexWrap":["wrap"]},"isVariation":"contentarea","metadata":{"name":"Content Area"}} -->
<div class="gsbp-row5678" data-type="content-area-component"><!-- wp:greenshift-blocks/element {"id":"gsbp-left9012","type":"inner","localId":"gsbp-left9012"} -->
<div>
<!-- Left column content -->
</div>
<!-- /wp:greenshift-blocks/element -->

<!-- wp:greenshift-blocks/element {"id":"gsbp-rght3456","type":"inner","localId":"gsbp-rght3456"} -->
<div>
<!-- Right column content -->
</div>
<!-- /wp:greenshift-blocks/element --></div>
<!-- /wp:greenshift-blocks/element --></section>
<!-- /wp:greenshift-blocks/element -->
```

### Three-Column Grid
Use `flexColumns_Extra: 3` and `flexWidths_Extra` with `[33.33, 33.33, 33.33]` widths.

### Four-Column Grid
Use `flexColumns_Extra: 4` and `flexWidths_Extra` with `[25, 25, 25, 25]` widths.

## Styling Reference

### styleAttributes Format
```json
{
  "styleAttributes": {
    "property": ["desktop_value", "tablet_value", "mobile_landscape", "mobile_portrait"],
    "property_hover": ["hover_value"],
    "property_focus": ["focus_value"]
  }
}
```

Single value applies to all breakpoints: `"padding": ["20px"]`

### Common CSS Variables

**Font Sizes:**
- `var(--wp--preset--font-size--xs, 0.85rem)`
- `var(--wp--preset--font-size--s, 1rem)`
- `var(--wp--preset--font-size--r, 1.2rem)`
- `var(--wp--preset--font-size--m, 1.35rem)`
- `var(--wp--preset--font-size--l, 1.55rem)`
- `var(--wp--preset--font-size--xl, clamp(1.6rem, 2.75vw, 1.9rem))`
- `var(--wp--preset--font-size--xxl, clamp(1.75rem, 3vw, 2.2rem))`
- `var(--wp--preset--font-size--giga, clamp(3rem, 5vw, 4.5rem))`

**Spacing:**
- `var(--wp--preset--spacing--20, 0.44rem)`
- `var(--wp--preset--spacing--40, 1rem)`
- `var(--wp--preset--spacing--50, 1.5rem)`
- `var(--wp--preset--spacing--60, 2.25rem)`
- `var(--wp--preset--spacing--70, 3.38rem)`
- `var(--wp--preset--spacing--80, 5.06rem)`

**Border Radius:**
- `var(--wp--custom--border-radius--mini, 5px)`
- `var(--wp--custom--border-radius--small, 10px)`
- `var(--wp--custom--border-radius--medium, 15px)`
- `var(--wp--custom--border-radius--large, 20px)`

**Shadows:**
- `var(--wp--preset--shadow--soft, 0px 15px 30px 0px rgba(119, 123, 146, 0.1))`
- `var(--wp--preset--shadow--elegant, 0px 5px 23px 0px rgba(188, 207, 219, 0.35))`

**Transitions:**
- `var(--wp--custom--transition--ease, all 0.5s ease)`
- `var(--wp--custom--transition--creative, all 0.5s cubic-bezier(0.165, 0.84, 0.44, 1))`

## Gradients

### Background Gradient
```json
{
  "styleAttributes": {
    "imageGradient_Extra": true,
    "backgroundImage": ["linear-gradient(135deg, #667eea 0%, #764ba2 100%)"]
  }
}
```

### Text Gradient
```json
{
  "styleAttributes": {
    "imageGradient_Extra": true,
    "backgroundImage": ["linear-gradient(135deg, #667eea 0%, #764ba2 100%)"],
    "backgroundClip": ["text"],
    "color": ["transparent"]
  }
}
```

## Output Requirements

1. Return only valid block markup
2. Use `wp:greenshift-blocks/element` as block name
3. Generate unique IDs for each block
4. Include `localId` matching `id`
5. Add class with `localId` when `styleAttributes` present
6. Use placeholder images: `https://placehold.co/WIDTHxHEIGHT`
7. Add `loading="lazy"` to images
8. Use CSS variables over hardcoded values when possible
