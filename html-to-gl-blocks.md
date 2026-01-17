# HTML to GL Page Builder Blocks Converter

Convert standard HTML/CSS into GL Page Builder (GreenLight/Greenshift) block markup for WordPress.

## Conversion Rules

### 1. Element Mapping

| HTML Element | GL Block Tag | Notes |
|-------------|--------------|-------|
| `<div>` | (default) | Omit `tag` attribute |
| `<section>` | `"tag":"section"` | Use for page sections |
| `<article>` | `"tag":"article"` | For article content |
| `<header>` | `"tag":"header"` | |
| `<footer>` | `"tag":"footer"` | |
| `<nav>` | `"tag":"nav"` | |
| `<aside>` | `"tag":"aside"` | |
| `<main>` | `"tag":"main"` | |
| `<h1-h6>` | `"tag":"h1"` etc | |
| `<p>` | `"tag":"p"` | |
| `<span>` | `"tag":"span"` | |
| `<a>` | `"tag":"a"` | Add `href` attribute |
| `<button>` | `"tag":"button"` | Use `formAttributes.type` |
| `<img>` | `"tag":"img"` | Add `src`, `alt`, dimensions |
| `<video>` | `"tag":"video"` | |
| `<audio>` | `"tag":"audio"` | |
| `<iframe>` | `"tag":"iframe"` | |
| `<ul>`, `<ol>` | `"tag":"ul"` / `"tag":"ol"` | |
| `<li>` | `"tag":"li"` | |
| `<table>` | `"tag":"table"` | Use `tableStyles` |
| `<tr>` | `"tag":"tr"` | |
| `<td>`, `<th>` | `"tag":"td"` / `"tag":"th"` | |
| `<form>` | `"tag":"form"` | |
| `<input>` | `"tag":"input"` | Use `formAttributes` |
| `<textarea>` | `"tag":"textarea"` | |
| `<select>` | `"tag":"select"` | |
| `<svg>` | `"tag":"svg"` | Use `icon` attribute |

### 2. Content Type Selection

| Content | `type` Value | When to Use |
|---------|-------------|-------------|
| Text only | `"text"` or omit | Simple text content |
| Nested blocks | `"inner"` | Contains child blocks |
| Empty/spacer | `"no"` | Decorative elements |
| Charts | `"chart"` | ApexCharts data |

### 3. CSS to styleAttributes Conversion

**CSS Property → JSON Property (camelCase)**

```
background-color → backgroundColor
font-size → fontSize
padding-top → paddingTop
margin-bottom → marginBottom
border-radius → borderRadius (or individual corners)
flex-direction → flexDirection
justify-content → justifyContent
align-items → alignItems
text-decoration → textDecoration
box-shadow → boxShadow
z-index → zIndex
```

**Responsive Array Format:**
```json
"property": ["desktop", "tablet", "mobile_landscape", "mobile_portrait"]
```

Single value = all breakpoints: `"padding": ["20px"]`

### 4. Inline Styles Conversion

**Before (HTML):**
```html
<div style="padding: 20px; background: #f5f5f5; border-radius: 10px;">
```

**After (GL Block):**
```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-abc1234","type":"inner","localId":"gsbp-abc1234","styleAttributes":{"padding":["20px"],"backgroundColor":["#f5f5f5"],"borderRadius":["10px"]}} -->
<div class="gsbp-abc1234"></div>
<!-- /wp:greenshift-blocks/element -->
```

### 5. Class-Based Styles Conversion

When converting CSS classes, map them to `styleAttributes`:

**Original CSS:**
```css
.card {
  padding: 24px;
  background: white;
  border-radius: 12px;
  box-shadow: 0 4px 6px rgba(0,0,0,0.1);
}
.card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 25px rgba(0,0,0,0.15);
}
```

**Converted:**
```json
{
  "styleAttributes": {
    "padding": ["24px"],
    "backgroundColor": ["white"],
    "borderRadius": ["12px"],
    "boxShadow": ["0 4px 6px rgba(0,0,0,0.1)"],
    "transition": ["var(--wp--custom--transition--ease, all 0.5s ease)"],
    "transform_hover": ["translateY(-4px)"],
    "boxShadow_hover": ["0 8px 25px rgba(0,0,0,0.15)"]
  }
}
```

### 6. Flexbox Conversion

**Original:**
```html
<div style="display: flex; gap: 20px; flex-wrap: wrap; justify-content: center;">
```

**Converted:**
```json
{
  "styleAttributes": {
    "display": ["flex"],
    "columnGap": ["20px"],
    "rowGap": ["20px"],
    "flexWrap": ["wrap"],
    "justifyContent": ["center"]
  }
}
```

### 7. Grid Columns Conversion

For flex-based column layouts, use `flexColumns_Extra` and `flexWidths_Extra`:

**Two Equal Columns:**
```json
{
  "styleAttributes": {
    "display": ["flex"],
    "flexColumns_Extra": 2,
    "flexWidths_Extra": {
      "desktop": {"name": "50/50", "widths": [50, 50]},
      "tablet": {"name": "50/50", "widths": [50, 50]},
      "mobile": {"name": "100/100", "widths": [100, 100]}
    },
    "flexWrap": ["wrap"],
    "columnGap": ["24px"],
    "rowGap": ["24px"]
  }
}
```

**Three Columns:**
```json
"flexColumns_Extra": 3,
"flexWidths_Extra": {
  "desktop": {"name": "33/33/33", "widths": [33.33, 33.33, 33.33]},
  "tablet": {"name": "50/50/100", "widths": [50, 50, 100]},
  "mobile": {"name": "100/100/100", "widths": [100, 100, 100]}
}
```

### 8. Link Attributes Conversion

**Original:**
```html
<a href="https://example.com" target="_blank" rel="noopener nofollow">
```

**Converted:**
```json
{
  "tag": "a",
  "href": "https://example.com",
  "linkNewWindow": true,
  "linkNoFollow": true
}
```

### 9. Image Conversion

**Original:**
```html
<img src="image.jpg" alt="Description" width="800" height="600" loading="lazy">
```

**Converted:**
```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-img1234","tag":"img","localId":"gsbp-img1234","src":"image.jpg","alt":"Description","originalWidth":800,"originalHeight":600} -->
<img class="gsbp-img1234" src="image.jpg" alt="Description" width="800" height="600" loading="lazy"/>
<!-- /wp:greenshift-blocks/element -->
```

### 10. SVG Conversion

**Original:**
```html
<svg viewBox="0 0 24 24" width="24" height="24">
  <path d="M12 2L2 7l10 5 10-5z"/>
</svg>
```

**Converted:**
```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-svg1234","tag":"svg","icon":{"icon":{"svg":"<svg viewBox=\"0 0 24 24\"><path d=\"M12 2L2 7l10 5 10-5z\"/></svg>","image":""},"fill":"currentColor","type":"svg"},"localId":"gsbp-svg1234","styleAttributes":{"width":["24px"],"height":["24px"]}} -->
<svg viewBox="0 0 24 24" width="24" height="24" class="gsbp-svg1234"><path d="M12 2L2 7l10 5 10-5z"/></svg>
<!-- /wp:greenshift-blocks/element -->
```

**Note:** Remove `xmlns` attributes from SVG and path elements.

### 11. Data Attributes Conversion

Use `dynamicAttributes` for custom data attributes:

**Original:**
```html
<div data-aos="fade-up" data-delay="100">
```

**Converted:**
```json
{
  "dynamicAttributes": [
    {"name": "data-aos", "value": "fade-up"},
    {"name": "data-delay", "value": "100"}
  ]
}
```

### 12. Form Elements Conversion

**Button:**
```html
<!-- Original -->
<button type="submit">Submit</button>

<!-- Converted -->
<!-- wp:greenshift-blocks/element {"id":"gsbp-btn1234","textContent":"Submit","tag":"button","localId":"gsbp-btn1234","type":"text","formAttributes":{"type":"submit"}} -->
<button type="submit">Submit</button>
<!-- /wp:greenshift-blocks/element -->
```

**Input:**
```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-inp1234","tag":"input","localId":"gsbp-inp1234","formAttributes":{"type":"text","name":"email","placeholder":"Enter email"}} -->
<input type="text" name="email" placeholder="Enter email"/>
<!-- /wp:greenshift-blocks/element -->
```

### 13. Complex Selectors with dynamicGClasses

For pseudo-elements, child selectors, or complex hover states, use `dynamicGClasses`:

**Original CSS:**
```css
.card::before {
  content: "";
  position: absolute;
  background: linear-gradient(to right, #667eea, #764ba2);
}
.card:hover .title {
  color: #667eea;
}
```

**Converted:**
```json
{
  "dynamicGClasses": [{
    "value": "card_styles",
    "type": "local",
    "label": "card_styles",
    "localed": false,
    "css": ".card_styles{position:relative;}",
    "attributes": {"styleAttributes": {"position": ["relative"]}},
    "originalID": "gsbp-card123",
    "originalBlock": "greenshift-blocks/element",
    "selectors": [
      {
        "value": "::before",
        "attributes": {"styleAttributes": {"content": ["\"\""], "position": ["absolute"], "backgroundImage": ["linear-gradient(to right, #667eea, #764ba2)"]}},
        "css": ".card_styles::before{content:\"\";position:absolute;background-image:linear-gradient(to right, #667eea, #764ba2);}"
      },
      {
        "value": ":hover .title",
        "attributes": {"styleAttributes": {"color": ["#667eea"]}},
        "css": ".card_styles:hover .title{color:#667eea;}"
      }
    ]
  }],
  "className": "card_styles"
}
```

### 14. Responsive CSS Conversion

**Media Query CSS:**
```css
.element {
  font-size: 24px;
}
@media (max-width: 768px) {
  .element {
    font-size: 20px;
  }
}
@media (max-width: 576px) {
  .element {
    font-size: 16px;
  }
}
```

**Converted (array order: desktop, tablet, mobile_landscape, mobile_portrait):**
```json
{
  "styleAttributes": {
    "fontSize": ["24px", "20px", "16px", "16px"]
  }
}
```

## Conversion Process

1. **Analyze HTML structure** - Identify nesting, content types
2. **Generate unique IDs** - Format: `gsbp-{7 alphanumeric}`
3. **Map elements to tags** - Use appropriate `tag` values
4. **Convert inline styles** - Transform to `styleAttributes`
5. **Handle CSS classes** - Map to `styleAttributes` or `dynamicGClasses`
6. **Process attributes** - Map href, src, alt, data-* etc.
7. **Set content type** - `text`, `inner`, or `no`
8. **Add required classes** - Include `localId` in class when styled

## Output Requirements

1. Valid WordPress block markup only
2. Block name: `wp:greenshift-blocks/element`
3. Properly escaped JSON in comments
4. Matching `id` and `localId`
5. Class includes `localId` when `styleAttributes` present
6. No `xmlns` in SVG output
7. `loading="lazy"` on images
8. Prefer CSS variables over hardcoded values
