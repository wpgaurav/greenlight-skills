# GenerateBlocks to GL Page Builder Converter

Convert GenerateBlocks V2 block markup to GL Page Builder (GreenLight/Greenshift) format.

## Block Type Mapping

| GenerateBlocks Block | GL Page Builder |
|---------------------|-----------------|
| `generateblocks/element` | `greenshift-blocks/element` with `type: "inner"` |
| `generateblocks/text` | `greenshift-blocks/element` with `type: "text"` or omit |
| `generateblocks/media` | `greenshift-blocks/element` with `tag: "img"` |
| `generateblocks/shape` | `greenshift-blocks/element` with `tag: "svg"` |

## Attribute Mapping

### Core Attributes

| GenerateBlocks | GL Page Builder | Notes |
|---------------|-----------------|-------|
| `uniqueId` | `id` + `localId` | Prefix with `gsbp-`, both must match |
| `tagName` | `tag` | Same values, div is default (omit) |
| `className` | `className` | Direct copy |
| `htmlAttributes.href` | `href` | Move to root level |
| `htmlAttributes.src` | `src` | Move to root level |
| `htmlAttributes.alt` | `alt` | Move to root level |
| `htmlAttributes.target` | `linkNewWindow` | `"_blank"` → `true` |
| `htmlAttributes.rel` | `linkNoFollow` | Check for `nofollow` |
| `styles` | `styleAttributes` | Convert to responsive arrays |
| `css` | (processed) | Extract hover/pseudo into styleAttributes |

### Styles Conversion

**GenerateBlocks** uses flat object with camelCase:
```json
{
  "styles": {
    "display": "flex",
    "gap": "1rem",
    "padding": "2rem"
  }
}
```

**GL Page Builder** uses responsive arrays:
```json
{
  "styleAttributes": {
    "display": ["flex"],
    "columnGap": ["1rem"],
    "rowGap": ["1rem"],
    "padding": ["2rem"]
  }
}
```

### Property Name Changes

| GenerateBlocks | GL Page Builder | Notes |
|---------------|-----------------|-------|
| `gap` | `columnGap` + `rowGap` | Split into two properties |
| `background` | `backgroundColor` or `backgroundImage` | Depends on value |
| `gridTemplateColumns` | `flexColumns_Extra` + `flexWidths_Extra` | For column layouts |

### Hover States

**GenerateBlocks** uses nested objects or CSS string:
```json
{
  "styles": {
    "backgroundColor": "#0073aa",
    "&:hover": {
      "backgroundColor": "#005a87"
    }
  }
}
```

**GL Page Builder** uses `_hover` suffix:
```json
{
  "styleAttributes": {
    "backgroundColor": ["#0073aa"],
    "backgroundColor_hover": ["#005a87"]
  }
}
```

### Responsive Breakpoints

**GenerateBlocks** uses CSS media queries in `css` attribute.

**GL Page Builder** uses array positions:
```
Index 0: Desktop
Index 1: Tablet (768px)
Index 2: Mobile Landscape (576px)
Index 3: Mobile Portrait
```

Extract values from media queries:
```css
/* GenerateBlocks css attribute */
.gb-element-abc{padding:2rem}@media(max-width:1024px){.gb-element-abc{padding:1.5rem}}@media(max-width:767px){.gb-element-abc{padding:1rem}}
```

Becomes:
```json
{
  "styleAttributes": {
    "padding": ["2rem", "1.5rem", "1rem", "1rem"]
  }
}
```

## Conversion Examples

### Example 1: Container Element

**GenerateBlocks:**
```html
<!-- wp:generateblocks/element {"uniqueId":"hero001","tagName":"section","styles":{"display":"flex","flexDirection":"column","gap":"2rem","padding":"3rem 1.5rem","backgroundColor":"#f8f9fa"},"css":".gb-element-hero001{display:flex;flex-direction:column;gap:2rem;padding:3rem 1.5rem;background-color:#f8f9fa}"} -->
<section class="gb-element-hero001">
    <!-- content -->
</section>
<!-- /wp:generateblocks/element -->
```

**GL Page Builder:**
```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-hero001","tag":"section","type":"inner","localId":"gsbp-hero001","styleAttributes":{"display":["flex"],"flexDirection":["column"],"columnGap":["2rem"],"rowGap":["2rem"],"padding":["3rem 1.5rem"],"backgroundColor":["#f8f9fa"]}} -->
<section class="gsbp-hero001">
<!-- content -->
</section>
<!-- /wp:greenshift-blocks/element -->
```

### Example 2: Text/Heading

**GenerateBlocks:**
```html
<!-- wp:generateblocks/text {"uniqueId":"text001","tagName":"h2","styles":{"fontSize":"2rem","fontWeight":"700","color":"#0a0a0a","marginBottom":"1rem"},"css":".gb-text-text001{font-size:2rem;font-weight:700;color:#0a0a0a;margin-bottom:1rem}"} -->
<h2 class="gb-text gb-text-text001">Welcome to Our Site</h2>
<!-- /wp:generateblocks/text -->
```

**GL Page Builder:**
```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-text001","textContent":"Welcome to Our Site","tag":"h2","localId":"gsbp-text001","styleAttributes":{"fontSize":["2rem"],"fontWeight":["700"],"color":["#0a0a0a"],"marginBottom":["1rem"]}} -->
<h2 class="gsbp-text001">Welcome to Our Site</h2>
<!-- /wp:greenshift-blocks/element -->
```

### Example 3: Link/Button with Hover

**GenerateBlocks:**
```html
<!-- wp:generateblocks/text {"uniqueId":"btn001","tagName":"a","htmlAttributes":{"href":"https://example.com"},"styles":{"padding":"1rem 2rem","backgroundColor":"#0073aa","color":"#ffffff","borderRadius":"4px","textDecoration":"none","transition":"all 0.3s"},"css":".gb-text-btn001{padding:1rem 2rem;background-color:#0073aa;color:#ffffff;border-radius:4px;text-decoration:none;transition:all 0.3s}.gb-text-btn001:hover{background-color:#005a87;transform:translateY(-2px)}"} -->
<a class="gb-text gb-text-btn001" href="https://example.com">Get Started</a>
<!-- /wp:generateblocks/text -->
```

**GL Page Builder:**
```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-btn001","textContent":"Get Started","tag":"a","localId":"gsbp-btn001","href":"https://example.com","styleAttributes":{"padding":["1rem 2rem"],"backgroundColor":["#0073aa"],"color":["#ffffff"],"borderRadius":["4px"],"textDecoration":["none"],"transition":["all 0.3s"],"backgroundColor_hover":["#005a87"],"transform_hover":["translateY(-2px)"]}} -->
<a class="gsbp-btn001" href="https://example.com">Get Started</a>
<!-- /wp:greenshift-blocks/element -->
```

### Example 4: Image

**GenerateBlocks:**
```html
<!-- wp:generateblocks/media {"uniqueId":"img001","tagName":"img","htmlAttributes":{"src":"https://example.com/photo.jpg","alt":"Featured photo","width":"600","height":"400"},"styles":{"width":"100%","height":"auto","borderRadius":"8px","objectFit":"cover"},"css":".gb-media-img001{width:100%;height:auto;border-radius:8px;object-fit:cover}"} -->
<img class="gb-media-img001" src="https://example.com/photo.jpg" alt="Featured photo" width="600" height="400"/>
<!-- /wp:generateblocks/media -->
```

**GL Page Builder:**
```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-img001","tag":"img","localId":"gsbp-img001","src":"https://example.com/photo.jpg","alt":"Featured photo","originalWidth":600,"originalHeight":400,"styleAttributes":{"width":["100%"],"height":["auto"],"borderRadius":["8px"],"objectFit":["cover"]}} -->
<img class="gsbp-img001" src="https://example.com/photo.jpg" alt="Featured photo" width="600" height="400" loading="lazy"/>
<!-- /wp:greenshift-blocks/element -->
```

### Example 5: SVG Icon

**GenerateBlocks:**
```html
<!-- wp:generateblocks/shape {"uniqueId":"icon001","styles":{"width":"24px","height":"24px","svg":{"fill":"#0073aa"}},"css":".gb-shape-icon001{width:24px;height:24px}.gb-shape-icon001 svg{fill:#0073aa}"} -->
<span class="gb-shape gb-shape-icon001">
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><path d="M12 2l10 5-10 5-10-5 10-5z"/></svg>
</span>
<!-- /wp:generateblocks/shape -->
```

**GL Page Builder:**
```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-icon001","tag":"svg","icon":{"icon":{"svg":"<svg viewBox=\"0 0 24 24\"><path d=\"M12 2l10 5-10 5-10-5 10-5z\"/></svg>","image":""},"fill":"#0073aa","type":"svg"},"localId":"gsbp-icon001","styleAttributes":{"width":["24px"],"height":["24px"]}} -->
<svg viewBox="0 0 24 24" width="24" height="24" class="gsbp-icon001"><path d="M12 2l10 5-10 5-10-5 10-5z"/></svg>
<!-- /wp:greenshift-blocks/element -->
```

### Example 6: Grid to Flex Columns

**GenerateBlocks:**
```html
<!-- wp:generateblocks/element {"uniqueId":"grid001","tagName":"div","styles":{"display":"grid","gridTemplateColumns":"repeat(3, 1fr)","gap":"2rem"},"css":".gb-element-grid001{display:grid;grid-template-columns:repeat(3, 1fr);gap:2rem}@media(max-width:1024px){.gb-element-grid001{grid-template-columns:repeat(2, 1fr)}}@media(max-width:767px){.gb-element-grid001{grid-template-columns:1fr}}"} -->
<div class="gb-element-grid001">
    <!-- grid items -->
</div>
<!-- /wp:generateblocks/element -->
```

**GL Page Builder:**
```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-grid001","type":"inner","localId":"gsbp-grid001","styleAttributes":{"display":["flex"],"flexColumns_Extra":3,"flexWidths_Extra":{"desktop":{"name":"33/33/33","widths":[33.33,33.33,33.33]},"tablet":{"name":"50/50/100","widths":[50,50,100]},"mobile":{"name":"100/100/100","widths":[100,100,100]}},"flexWrap":["wrap"],"columnGap":["2rem"],"rowGap":["2rem"]}} -->
<div class="gsbp-grid001">
<!-- grid items -->
</div>
<!-- /wp:greenshift-blocks/element -->
```

### Example 7: Pseudo-Elements

**GenerateBlocks:**
```html
<!-- wp:generateblocks/element {"uniqueId":"card001","tagName":"div","styles":{"position":"relative","padding":"2rem"},"css":".gb-element-card001{position:relative;padding:2rem}.gb-element-card001::before{content:'';position:absolute;top:0;left:0;width:4px;height:100%;background-color:#0073aa}"} -->
<div class="gb-element-card001">Content</div>
<!-- /wp:generateblocks/element -->
```

**GL Page Builder:**
```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-card001","type":"inner","localId":"gsbp-card001","styleAttributes":{"position":["relative"],"padding":["2rem"]},"dynamicGClasses":[{"value":"card_styles","type":"local","label":"card_styles","localed":false,"css":".card_styles{position:relative;padding:2rem;}","attributes":{"styleAttributes":{"position":["relative"],"padding":["2rem"]}},"originalID":"gsbp-card001","originalBlock":"greenshift-blocks/element","selectors":[{"value":"::before","attributes":{"styleAttributes":{"content":["\"\""],"position":["absolute"],"top":["0"],"left":["0"],"width":["4px"],"height":["100%"],"backgroundColor":["#0073aa"]}},"css":".card_styles::before{content:\"\";position:absolute;top:0;left:0;width:4px;height:100%;background-color:#0073aa;}"}]}],"className":"card_styles"} -->
<div class="gsbp-card001 card_styles">Content</div>
<!-- /wp:greenshift-blocks/element -->
```

## Class Naming Conversion

| GenerateBlocks | GL Page Builder |
|---------------|-----------------|
| `gb-element` | (none - not needed) |
| `gb-element-{id}` | `gsbp-{id}` |
| `gb-text` | (none - not needed) |
| `gb-text-{id}` | `gsbp-{id}` |
| `gb-media-{id}` | `gsbp-{id}` |
| `gb-shape` | (none - not needed) |
| `gb-shape-{id}` | `gsbp-{id}` |

## Conversion Checklist

1. [ ] Change block name: `generateblocks/*` → `greenshift-blocks/element`
2. [ ] Prefix uniqueId with `gsbp-` for both `id` and `localId`
3. [ ] Change `tagName` to `tag`
4. [ ] Set `type: "inner"` for containers, omit for text
5. [ ] Move `htmlAttributes.href/src/alt` to root level
6. [ ] Convert `styles` object to `styleAttributes` arrays
7. [ ] Split `gap` into `columnGap` and `rowGap`
8. [ ] Extract hover states from CSS to `property_hover`
9. [ ] Extract responsive values from media queries to array positions
10. [ ] Convert `gridTemplateColumns` to `flexColumns_Extra` + `flexWidths_Extra`
11. [ ] Convert SVG to `icon` attribute format
12. [ ] Remove `xmlns` from SVG elements
13. [ ] Add `loading="lazy"` to images
14. [ ] Update class names in HTML output
