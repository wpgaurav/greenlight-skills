# GL Page Builder Animation Patterns

Create engaging animations using CSS animations and GSAP integration.

## CSS Keyframe Animations

Use `animation_keyframes_Extra` in `styleAttributes`:

```json
{
  "styleAttributes": {
    "animation_keyframes_Extra": [
      {
        "name": "gs_fade_in",
        "code": "0%{opacity:0;transform:translateY(20px);}100%{opacity:1;transform:translateY(0);}"
      }
    ],
    "animation": ["gs_fade_in 0.6s ease-out forwards"]
  }
}
```

### Fade In Animation

```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-fade123","textContent":"Fade In Content","localId":"gsbp-fade123","styleAttributes":{"animation_keyframes_Extra":[{"name":"gs_fade","code":"0%{opacity:0;}100%{opacity:1;}"}],"animation":["gs_fade 0.8s ease-out forwards"],"opacity":["0"]}} -->
<div class="gsbp-fade123">Fade In Content</div>
<!-- /wp:greenshift-blocks/element -->
```

### Slide Up Animation

```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-slide123","textContent":"Slide Up Content","localId":"gsbp-slide123","styleAttributes":{"animation_keyframes_Extra":[{"name":"gs_slide_up","code":"0%{opacity:0;transform:translateY(30px);}100%{opacity:1;transform:translateY(0);}"}],"animation":["gs_slide_up 0.6s ease-out forwards"]}} -->
<div class="gsbp-slide123">Slide Up Content</div>
<!-- /wp:greenshift-blocks/element -->
```

### Scale Animation

```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-scale123","textContent":"Scale In","localId":"gsbp-scale123","styleAttributes":{"animation_keyframes_Extra":[{"name":"gs_scale","code":"0%{opacity:0;transform:scale(0.8);}100%{opacity:1;transform:scale(1);}"}],"animation":["gs_scale 0.5s ease-out forwards"]}} -->
<div class="gsbp-scale123">Scale In</div>
<!-- /wp:greenshift-blocks/element -->
```

### Bounce Animation

```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-bounce12","textContent":"Bouncing","localId":"gsbp-bounce12","styleAttributes":{"animation_keyframes_Extra":[{"name":"gs_bounce","code":"0%,20%,50%,80%,100%{transform:translateY(0);}40%{transform:translateY(-15px);}60%{transform:translateY(-7px);}"}],"animation":["gs_bounce 1s ease infinite"]}} -->
<div class="gsbp-bounce12">Bouncing</div>
<!-- /wp:greenshift-blocks/element -->
```

### Pulse Animation

```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-pulse123","type":"inner","localId":"gsbp-pulse123","styleAttributes":{"animation_keyframes_Extra":[{"name":"gs_pulse","code":"0%{transform:scale(1);}50%{transform:scale(1.05);}100%{transform:scale(1);}"}],"animation":["gs_pulse 2s ease-in-out infinite"]}} -->
<div class="gsbp-pulse123">Pulsing Content</div>
<!-- /wp:greenshift-blocks/element -->
```

### Rotate Animation

```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-rot123","tag":"svg","icon":{"icon":{"svg":"<svg viewBox=\"0 0 24 24\"><circle cx=\"12\" cy=\"12\" r=\"10\" stroke=\"currentColor\" fill=\"none\" stroke-width=\"2\" stroke-dasharray=\"40\" stroke-dashoffset=\"10\"/></svg>","image":""},"fill":"currentColor","type":"svg"},"localId":"gsbp-rot123","styleAttributes":{"width":["40px"],"height":["40px"],"animation_keyframes_Extra":[{"name":"gs_spin","code":"0%{transform:rotate(0deg);}100%{transform:rotate(360deg);}"}],"animation":["gs_spin 1s linear infinite"]}} -->
<svg viewBox="0 0 24 24" width="40" height="40" class="gsbp-rot123"><circle cx="12" cy="12" r="10" stroke="currentColor" fill="none" stroke-width="2" stroke-dasharray="40" stroke-dashoffset="10"/></svg>
<!-- /wp:greenshift-blocks/element -->
```

## Scroll-Triggered CSS Animations

Use `animationTimeline` and `animationRange`:

```json
{
  "styleAttributes": {
    "animation_keyframes_Extra": [{"name": "gs_scroll", "code": "0%{opacity:0;scale:0.8;}100%{opacity:1;scale:1;}"}],
    "animation": ["gs_scroll linear both"],
    "animationTimeline": ["view()"],
    "animationRange": ["entry"]
  }
}
```

### Scroll Fade In

```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-scrfade","textContent":"Scroll to reveal","tag":"h2","localId":"gsbp-scrfade","styleAttributes":{"animation_keyframes_Extra":[{"name":"gs_reveal","code":"0%{opacity:0;transform:translateY(40px);}100%{opacity:1;transform:translateY(0);}"}],"animation":["gs_reveal linear both"],"animationTimeline":["view()"],"animationRange":["entry"]}} -->
<h2 class="gsbp-scrfade">Scroll to reveal</h2>
<!-- /wp:greenshift-blocks/element -->
```

### Scroll Scale

```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-scrscale","type":"inner","localId":"gsbp-scrscale","styleAttributes":{"animation_keyframes_Extra":[{"name":"gs_scale_scroll","code":"0%{opacity:0;scale:0.7;}100%{opacity:1;scale:1;}"}],"animation":["gs_scale_scroll linear both"],"animationTimeline":["view()"],"animationRange":["entry"]}} -->
<div class="gsbp-scrscale">Scaling content on scroll</div>
<!-- /wp:greenshift-blocks/element -->
```

### Animation Range Options

- `entry` - Animate as element enters viewport
- `exit` - Animate as element exits viewport
- `entry 0% exit 100%` - Full scroll progress
- `cover` - Cover the entire viewport

## GSAP Animations

For GSAP integration, use the `animation` attribute object:

```json
{
  "animation": {
    "usegsap": true,
    "delay": 0,
    "duration": 1000,
    "ease": "power2.out",
    "y": 50,
    "o": 0,
    "triggerstart": "top 80%"
  }
}
```

### GSAP Parameters

| Parameter | Description |
|-----------|-------------|
| `usegsap` | Enable GSAP (required) |
| `delay` | Animation delay (ms) |
| `duration` | Animation duration (ms) |
| `ease` | Easing function |
| `x`, `y`, `z` | Translate values |
| `r` | Rotation (degrees) |
| `rx`, `ry` | Rotate X/Y |
| `s` | Scale |
| `sx`, `sy` | Scale X/Y |
| `o` | Opacity (starting value) |
| `skewX`, `skewY` | Skew values |
| `origin` | Transform origin |
| `clipFinal` | Clip-path |
| `bg` | Background color |
| `color` | Text color |
| `triggerstart` | Scroll trigger start |
| `triggerend` | Scroll trigger end |

### GSAP Easing Options

- `power1.out`, `power2.out`, `power3.out`, `power4.out`
- `power1.in`, `power2.in`, `power3.in`, `power4.in`
- `power1.inOut`, `power2.inOut`, `power3.inOut`
- `back.out`, `back.in`, `back.inOut`
- `elastic.out`, `elastic.in`
- `bounce.out`, `bounce.in`
- `circ.out`, `circ.in`
- `expo.out`, `expo.in`
- `custom` (use with `easecustom`)

### GSAP Fade In From Bottom

```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-gsapfade","textContent":"GSAP Animated","localId":"gsbp-gsapfade","animation":{"usegsap":true,"delay":0,"duration":800,"ease":"power2.out","y":40,"o":0,"triggerstart":"top 85%"}} -->
<div class="gsbp-gsapfade" data-gsapinit="1" data-from="yes" data-duration="0.8" data-ease="power2.out" data-y="40" data-o="0" data-triggerstart="top 85%">GSAP Animated</div>
<!-- /wp:greenshift-blocks/element -->
```

### GSAP Stagger Animation

For staggered animations on children, add `staggerclass`:

```json
{
  "animation": {
    "usegsap": true,
    "duration": 600,
    "ease": "power2.out",
    "y": 30,
    "o": 0,
    "stagger": 0.1
  }
}
```

## Custom JavaScript Animations

Use `customJs` and `customJsEnabled` for custom scripts:

```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-customjs","textContent":"Custom Animation","localId":"gsbp-customjs","customJs":"import gsap from \"{{PLUGIN_URL}}/libs/motion/gsap.js\";\n\nconst el = document.querySelector('.gsbp-customjs');\ngsap.from(el, {\n  duration: 1,\n  y: 50,\n  opacity: 0,\n  ease: 'power3.out'\n});","customJsEnabled":true} -->
<div class="gsbp-customjs">Custom Animation</div>
<!-- /wp:greenshift-blocks/element -->
```

## Hover Animations

Use `_hover` suffix for hover states:

### Transform on Hover

```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-hvr123","type":"inner","localId":"gsbp-hvr123","styleAttributes":{"transition":["var(--wp--custom--transition--creative, all 0.5s cubic-bezier(0.165, 0.84, 0.44, 1))"],"transform_hover":["translateY(-8px)"],"boxShadow":["var(--wp--preset--shadow--soft)"],"boxShadow_hover":["var(--wp--preset--shadow--highlight)"]}} -->
<div class="gsbp-hvr123">Hover me</div>
<!-- /wp:greenshift-blocks/element -->
```

### Scale on Hover

```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-hvrscl","tag":"img","localId":"gsbp-hvrscl","src":"https://placehold.co/400x300","styleAttributes":{"transition":["transform 0.4s ease"],"transform_hover":["scale(1.05)"],"overflow":["hidden"]}} -->
<img class="gsbp-hvrscl" src="https://placehold.co/400x300" loading="lazy"/>
<!-- /wp:greenshift-blocks/element -->
```

### Color Transition on Hover

```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-hvrcol","textContent":"Hover for color change","tag":"a","localId":"gsbp-hvrcol","href":"#","styleAttributes":{"color":["#333333"],"color_hover":["var(--wp--preset--color--brand, #33EFAB)"],"transition":["color 0.3s ease"],"textDecoration":["none"]}} -->
<a class="gsbp-hvrcol" href="#">Hover for color change</a>
<!-- /wp:greenshift-blocks/element -->
```

## Interaction Layers

For click, hover, or scroll-triggered actions, use `interactionLayers`:

```json
{
  "interactionLayers": [
    {
      "actions": [{"actionname": "lightbox"}],
      "env": "no-action",
      "triggerData": {"trigger": "click"}
    }
  ]
}
```

### Available Actions

- `lightbox` - Open lightbox
- `toggle` - Toggle element
- `scroll` - Scroll to element
- `modal` - Open modal
- `panel` - Open sliding panel

## Transition Variables

Use built-in transition variables:

```json
{
  "styleAttributes": {
    "transition": ["var(--wp--custom--transition--ease, all 0.5s ease)"]
  }
}
```

Available transitions:
- `--wp--custom--transition--ease` - Standard ease
- `--wp--custom--transition--ease-in-out` - Ease in-out
- `--wp--custom--transition--creative` - Creative bounce
- `--wp--custom--transition--soft` - Soft easing
- `--wp--custom--transition--mild` - Mild easing
- `--wp--custom--transition--elegant` - Elegant spring
- `--wp--custom--transition--smooth` - Smooth
- `--wp--custom--transition--accent` - Accent
- `--wp--custom--transition--motion` - Motion
- `--wp--custom--transition--light` - Light

## Animation Performance Tips

1. **Prefer transform and opacity** - These are GPU-accelerated
2. **Use will-change sparingly** - Only for complex animations
3. **Avoid animating layout properties** - width, height, margin cause reflows
4. **Use CSS animations for simple effects** - Better performance than JS
5. **Use GSAP for complex sequences** - Better control and timeline features
6. **Test on mobile** - Reduce animation complexity for mobile
7. **Respect reduced motion** - CSS animations should include:

```css
@media (prefers-reduced-motion) {
  .animated-element {
    animation: none !important;
  }
}
```

## Complete Animated Card Example

```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-animcard","type":"inner","localId":"gsbp-animcard","styleAttributes":{"backgroundColor":["#ffffff"],"borderRadius":["var(--wp--custom--border-radius--medium, 15px)"],"overflow":["hidden"],"boxShadow":["var(--wp--preset--shadow--soft)"],"boxShadow_hover":["var(--wp--preset--shadow--highlight)"],"transform_hover":["translateY(-8px)"],"transition":["var(--wp--custom--transition--creative)"],"animation_keyframes_Extra":[{"name":"gs_card_enter","code":"0%{opacity:0;transform:translateY(30px);}100%{opacity:1;transform:translateY(0);}"}],"animation":["gs_card_enter linear both"],"animationTimeline":["view()"],"animationRange":["entry"]}} -->
<div class="gsbp-animcard">
<!-- Card content -->
</div>
<!-- /wp:greenshift-blocks/element -->
```
