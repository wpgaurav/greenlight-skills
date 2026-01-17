# GL Page Builder to GenerateBlocks Converter

Convert GL Page Builder (GreenLight/Greenshift) block markup to GenerateBlocks V2 format.

## Block Type Mapping

| GL Page Builder | GenerateBlocks Block | Condition |
|-----------------|---------------------|-----------|
| `type: "inner"` | `generateblocks/element` | Has child blocks |
| `type: "text"` or text content | `generateblocks/text` | Has textContent or text-like tag |
| `tag: "img"` | `generateblocks/media` | Image elements |
| `tag: "svg"` with `icon` | `generateblocks/shape` | SVG icons |
| No type, no children | `generateblocks/text` | Simple text/links |

## Attribute Mapping

### Core Attributes

| GL Page Builder | GenerateBlocks | Notes |
|-----------------|---------------|-------|
| `id` | `uniqueId` | Remove `gsbp-` prefix |
| `localId` | (not needed) | Only `id` exists in GB |
| `tag` | `tagName` | Same values, div is default |
| `className` | `className` | Direct copy |
| `href` | `htmlAttributes.href` | Move to htmlAttributes |
| `src` | `htmlAttributes.src` | Move to htmlAttributes |
| `alt` | `htmlAttributes.alt` | Move to htmlAttributes |
| `linkNewWindow` | `htmlAttributes.target` | `true` → `"_blank"` |
| `linkNoFollow` | `htmlAttributes.rel` | `true` → `"nofollow noopener"` |
| `styleAttributes` | `styles` + `css` | Convert from arrays |
| `textContent` | HTML content | Move to inner HTML |

### Styles Conversion

**GL Page Builder** uses responsive arrays:
```json
{
  "styleAttributes": {
    "display": ["flex"],
    "columnGap": ["2rem"],
    "rowGap": ["2rem"],
    "padding": ["3rem", "2rem", "1.5rem", "1rem"]
  }
}
```

**GenerateBlocks** uses flat object + CSS string:
```json
{
  "styles": {
    "display": "flex",
    "gap": "2rem",
    "padding": "3rem"
  },
  "css": ".gb-element-hero001{display:flex;gap:2rem;padding:3rem}@media(max-width:1024px){.gb-element-hero001{padding:2rem}}@media(max-width:767px){.gb-element-hero001{padding:1.5rem}}"
}
```

### Property Name Changes

| GL Page Builder | GenerateBlocks | Notes |
|-----------------|---------------|-------|
| `columnGap` + `rowGap` | `gap` | Combine if equal |
| `flexColumns_Extra` | (not used) | Convert to grid |
| `flexWidths_Extra` | `gridTemplateColumns` | Convert to CSS Grid |
| `imageGradient_Extra` | (not needed) | Just use backgroundImage |

### Hover States

**GL Page Builder** uses `_hover` suffix:
```json
{
  "styleAttributes": {
    "backgroundColor": ["#0073aa"],
    "backgroundColor_hover": ["#005a87"]
  }
}
```

**GenerateBlocks** uses nested objects AND CSS string:
```json
{
  "styles": {
    "backgroundColor": "#0073aa",
    "&:hover": {
      "backgroundColor": "#005a87"
    }
  },
  "css": ".gb-text-btn001{background-color:#0073aa}.gb-text-btn001:hover{background-color:#005a87}"
}
```

### Responsive Breakpoints

**GL Page Builder** array positions:
```
Index 0: Desktop (base)
Index 1: Tablet (1024px)
Index 2: Mobile Landscape (768px)
Index 3: Mobile Portrait
```

**GenerateBlocks** uses CSS media queries:
```css
.gb-element-abc{padding:3rem}@media(max-width:1024px){.gb-element-abc{padding:2rem}}@media(max-width:767px){.gb-element-abc{padding:1rem}}
```

## Conversion Examples

### Example 1: Container Section

**GL Page Builder:**
```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-hero001","tag":"section","type":"inner","localId":"gsbp-hero001","styleAttributes":{"display":["flex"],"flexDirection":["column"],"columnGap":["2rem"],"rowGap":["2rem"],"padding":["3rem 1.5rem"],"backgroundColor":["#f8f9fa"]}} -->
<section class="gsbp-hero001">
<!-- content -->
</section>
<!-- /wp:greenshift-blocks/element -->
```

**GenerateBlocks:**
```html
<!-- wp:generateblocks/element {"uniqueId":"hero001","tagName":"section","styles":{"display":"flex","flexDirection":"column","gap":"2rem","padding":"3rem 1.5rem","backgroundColor":"#f8f9fa"},"css":".gb-element-hero001{display:flex;flex-direction:column;gap:2rem;padding:3rem 1.5rem;background-color:#f8f9fa}"} -->
<section class="gb-element-hero001">
    <!-- content -->
</section>
<!-- /wp:generateblocks/element -->
```

### Example 2: Heading

**GL Page Builder:**
```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-text001","textContent":"Welcome to Our Site","tag":"h2","localId":"gsbp-text001","styleAttributes":{"fontSize":["2rem"],"fontWeight":["700"],"color":["#0a0a0a"],"marginBottom":["1rem"]}} -->
<h2 class="gsbp-text001">Welcome to Our Site</h2>
<!-- /wp:greenshift-blocks/element -->
```

**GenerateBlocks:**
```html
<!-- wp:generateblocks/text {"uniqueId":"text001","tagName":"h2","styles":{"fontSize":"2rem","fontWeight":"700","color":"#0a0a0a","marginBottom":"1rem"},"css":".gb-text-text001{font-size:2rem;font-weight:700;color:#0a0a0a;margin-bottom:1rem}"} -->
<h2 class="gb-text gb-text-text001">Welcome to Our Site</h2>
<!-- /wp:generateblocks/text -->
```

### Example 3: Link/Button with Hover

**GL Page Builder:**
```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-btn001","textContent":"Get Started","tag":"a","localId":"gsbp-btn001","href":"https://example.com","styleAttributes":{"padding":["1rem 2rem"],"backgroundColor":["#0073aa"],"color":["#ffffff"],"borderRadius":["4px"],"textDecoration":["none"],"transition":["all 0.3s"],"backgroundColor_hover":["#005a87"],"transform_hover":["translateY(-2px)"]}} -->
<a class="gsbp-btn001" href="https://example.com">Get Started</a>
<!-- /wp:greenshift-blocks/element -->
```

**GenerateBlocks:**
```html
<!-- wp:generateblocks/text {"uniqueId":"btn001","tagName":"a","htmlAttributes":{"href":"https://example.com"},"styles":{"padding":"1rem 2rem","backgroundColor":"#0073aa","color":"#ffffff","borderRadius":"4px","textDecoration":"none","transition":"all 0.3s","&:hover":{"backgroundColor":"#005a87","transform":"translateY(-2px)"}},"css":".gb-text-btn001{padding:1rem 2rem;background-color:#0073aa;color:#ffffff;border-radius:4px;text-decoration:none;transition:all 0.3s}.gb-text-btn001:hover{background-color:#005a87;transform:translateY(-2px)}"} -->
<a class="gb-text gb-text-btn001" href="https://example.com">Get Started</a>
<!-- /wp:generateblocks/text -->
```

### Example 4: Image

**GL Page Builder:**
```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-img001","tag":"img","localId":"gsbp-img001","src":"https://example.com/photo.jpg","alt":"Featured photo","originalWidth":600,"originalHeight":400,"styleAttributes":{"width":["100%"],"height":["auto"],"borderRadius":["8px"],"objectFit":["cover"]}} -->
<img class="gsbp-img001" src="https://example.com/photo.jpg" alt="Featured photo" width="600" height="400" loading="lazy"/>
<!-- /wp:greenshift-blocks/element -->
```

**GenerateBlocks:**
```html
<!-- wp:generateblocks/media {"uniqueId":"img001","tagName":"img","htmlAttributes":{"src":"https://example.com/photo.jpg","alt":"Featured photo","width":"600","height":"400","loading":"lazy"},"styles":{"width":"100%","height":"auto","borderRadius":"8px","objectFit":"cover"},"css":".gb-media-img001{width:100%;height:auto;border-radius:8px;object-fit:cover}"} -->
<img class="gb-media-img001" src="https://example.com/photo.jpg" alt="Featured photo" width="600" height="400" loading="lazy"/>
<!-- /wp:generateblocks/media -->
```

### Example 5: SVG Icon

**GL Page Builder:**
```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-icon001","tag":"svg","icon":{"icon":{"svg":"<svg viewBox=\"0 0 24 24\"><path d=\"M12 2l10 5-10 5-10-5 10-5z\"/></svg>","image":""},"fill":"#0073aa","type":"svg"},"localId":"gsbp-icon001","styleAttributes":{"width":["24px"],"height":["24px"]}} -->
<svg viewBox="0 0 24 24" width="24" height="24" class="gsbp-icon001"><path d="M12 2l10 5-10 5-10-5 10-5z"/></svg>
<!-- /wp:greenshift-blocks/element -->
```

**GenerateBlocks:**
```html
<!-- wp:generateblocks/shape {"uniqueId":"icon001","styles":{"width":"24px","height":"24px","svg":{"fill":"#0073aa"}},"css":".gb-shape-icon001{width:24px;height:24px}.gb-shape-icon001 svg{fill:#0073aa}"} -->
<span class="gb-shape gb-shape-icon001">
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24"><path d="M12 2l10 5-10 5-10-5 10-5z"/></svg>
</span>
<!-- /wp:generateblocks/shape -->
```

### Example 6: Flex Columns to Grid

**GL Page Builder:**
```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-grid001","type":"inner","localId":"gsbp-grid001","styleAttributes":{"display":["flex"],"flexColumns_Extra":3,"flexWidths_Extra":{"desktop":{"name":"33/33/33","widths":[33.33,33.33,33.33]},"tablet":{"name":"50/50/100","widths":[50,50,100]},"mobile":{"name":"100/100/100","widths":[100,100,100]}},"flexWrap":["wrap"],"columnGap":["2rem"],"rowGap":["2rem"]}} -->
<div class="gsbp-grid001">
<!-- items -->
</div>
<!-- /wp:greenshift-blocks/element -->
```

**GenerateBlocks:**
```html
<!-- wp:generateblocks/element {"uniqueId":"grid001","tagName":"div","styles":{"display":"grid","gridTemplateColumns":"repeat(3, 1fr)","gap":"2rem"},"css":".gb-element-grid001{display:grid;grid-template-columns:repeat(3, 1fr);gap:2rem}@media(max-width:1024px){.gb-element-grid001{grid-template-columns:repeat(2, 1fr)}}@media(max-width:767px){.gb-element-grid001{grid-template-columns:1fr}}"} -->
<div class="gb-element-grid001">
    <!-- items -->
</div>
<!-- /wp:generateblocks/element -->
```

### Example 7: Responsive Padding

**GL Page Builder:**
```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-resp001","type":"inner","localId":"gsbp-resp001","styleAttributes":{"padding":["4rem 2rem","3rem 1.5rem","2rem 1rem","2rem 1rem"]}} -->
<div class="gsbp-resp001">Content</div>
<!-- /wp:greenshift-blocks/element -->
```

**GenerateBlocks:**
```html
<!-- wp:generateblocks/element {"uniqueId":"resp001","tagName":"div","styles":{"padding":"4rem 2rem"},"css":".gb-element-resp001{padding:4rem 2rem}@media(max-width:1024px){.gb-element-resp001{padding:3rem 1.5rem}}@media(max-width:767px){.gb-element-resp001{padding:2rem 1rem}}"} -->
<div class="gb-element-resp001">Content</div>
<!-- /wp:generateblocks/element -->
```

### Example 8: dynamicGClasses (Pseudo-Elements)

**GL Page Builder:**
```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-card001","type":"inner","localId":"gsbp-card001","styleAttributes":{"position":["relative"],"padding":["2rem"]},"dynamicGClasses":[{"value":"card_styles","type":"local","selectors":[{"value":"::before","attributes":{"styleAttributes":{"content":["\"\""],"position":["absolute"],"top":["0"],"left":["0"],"width":["4px"],"height":["100%"],"backgroundColor":["#0073aa"]}}}]}],"className":"card_styles"} -->
<div class="gsbp-card001 card_styles">Content</div>
<!-- /wp:greenshift-blocks/element -->
```

**GenerateBlocks:**
```html
<!-- wp:generateblocks/element {"uniqueId":"card001","tagName":"div","styles":{"position":"relative","padding":"2rem","&::before":{"content":"''","position":"absolute","top":"0","left":"0","width":"4px","height":"100%","backgroundColor":"#0073aa"}},"css":".gb-element-card001{position:relative;padding:2rem}.gb-element-card001::before{content:'';position:absolute;top:0;left:0;width:4px;height:100%;background-color:#0073aa}"} -->
<div class="gb-element-card001">Content</div>
<!-- /wp:generateblocks/element -->
```

## flexWidths_Extra to Grid Conversion

| GL flexWidths | GenerateBlocks Grid |
|---------------|-------------------|
| `[50, 50]` | `repeat(2, 1fr)` |
| `[33.33, 33.33, 33.33]` | `repeat(3, 1fr)` |
| `[25, 25, 25, 25]` | `repeat(4, 1fr)` |
| `[66.66, 33.33]` | `2fr 1fr` |
| `[33.33, 66.66]` | `1fr 2fr` |
| `[100, 100]` | `1fr` (stacked) |

## Class Naming Conversion

| GL Page Builder | GenerateBlocks |
|-----------------|---------------|
| `gsbp-{id}` | `gb-element-{id}` or `gb-text-{id}` etc. |
| (none) | `gb-element` (for element blocks) |
| (none) | `gb-text` (for text blocks) |
| (none) | `gb-shape` (for shape blocks) |
| custom className | className (keep) |

## Tag to Block Type Decision

| GL `tag` Value | GenerateBlocks Block |
|---------------|---------------------|
| `div` (with `type: "inner"`) | `generateblocks/element` |
| `section`, `article`, `header`, `footer`, `nav`, `main`, `aside` | `generateblocks/element` |
| `h1`, `h2`, `h3`, `h4`, `h5`, `h6` | `generateblocks/text` |
| `p`, `span` | `generateblocks/text` |
| `a` (link) | `generateblocks/text` |
| `button` | `generateblocks/text` |
| `img` | `generateblocks/media` |
| `svg` | `generateblocks/shape` |
| `ul`, `ol`, `li` | `generateblocks/element` |
| `figure`, `figcaption` | `generateblocks/element` / `generateblocks/text` |

## CSS Generation

When generating the `css` attribute:

1. **Base class format:**
   - Element: `.gb-element-{uniqueId}`
   - Text: `.gb-text-{uniqueId}`
   - Media: `.gb-media-{uniqueId}`
   - Shape: `.gb-shape-{uniqueId}`

2. **Minify CSS** (no line breaks, minimal spaces)

3. **Order:**
   - Base styles first
   - Hover/focus states
   - Pseudo-elements (::before, ::after)
   - Media queries (largest to smallest)

4. **Media query breakpoints:**
   - Tablet: `@media(max-width:1024px)`
   - Mobile: `@media(max-width:767px)`

## Conversion Checklist

1. [ ] Change block name: `greenshift-blocks/element` → `generateblocks/*`
2. [ ] Remove `gsbp-` prefix from ID for `uniqueId`
3. [ ] Remove `localId` attribute
4. [ ] Change `tag` to `tagName`
5. [ ] Remove `type` attribute (determine block type from tag)
6. [ ] Move `href`, `src`, `alt` to `htmlAttributes`
7. [ ] Convert `linkNewWindow` to `htmlAttributes.target`
8. [ ] Convert `styleAttributes` arrays to flat `styles` object
9. [ ] Combine `columnGap` + `rowGap` to `gap` if equal
10. [ ] Convert `flexWidths_Extra` to `gridTemplateColumns`
11. [ ] Extract `_hover` styles to `&:hover` nested object
12. [ ] Generate `css` attribute from all styles
13. [ ] Add responsive media queries for array values
14. [ ] Convert `dynamicGClasses` to nested pseudo-element styles
15. [ ] Extract `icon.icon.svg` and wrap in `<span>` for shapes
16. [ ] Add appropriate base classes (`gb-text`, `gb-shape`, etc.)
17. [ ] Update class names in HTML output
