# GL Page Builder Component Patterns

Ready-to-use interactive component patterns for GL Page Builder. Copy and customize for your projects.

## Button Component

Standard themed button with hover effects:

```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-b65d91f","inlineCssStyles":".gs_button{text-decoration:none;display:inline-block;position:relative;overflow:hidden;border-bottom-left-radius:var(--wp--custom--button--border-radius, var(--wp-custom--border-radius--medium, 15px));border-bottom-right-radius:var(--wp--custom--button--border-radius, var(--wp-custom--border-radius--medium, 15px));border-top-left-radius:var(--wp--custom--button--border-radius, var(--wp-custom--border-radius--medium, 15px));border-top-right-radius:var(--wp--custom--button--border-radius, var(--wp-custom--border-radius--medium, 15px));padding-top:var(--wp--custom--button--spacing--vertical, var(--wp-preset--spacing--40, 1rem));padding-bottom:var(--wp--custom--button--spacing--vertical, var(--wp-preset--spacing--40, 1rem));padding-right:var(--wp--custom--button--spacing--horizontal, var(--wp-preset--spacing--60, 2.25rem));padding-left:var(--wp--custom--button--spacing--horizontal, var(--wp-preset--spacing--60, 2.25rem));background-color:var(--wp--custom--button--background, var(--wp-preset--color--brand, #33EFAB));color:var(--wp--custom--button--text, var(--wp-preset--color--text-on-brand, #000002));}.gs_button:hover{color:var(--wp--custom--button--text-hover, var(--wp-preset--color--text-on-brand-hover, #000003));background-color:var(--wp--custom--button--background-hover, var(--wp-preset--color--brand-hover, #7AFFCE));}","dynamicGClasses":[{"value":"gs-parent-hover","type":"preset","label":"gs-parent-hover"},{"value":"gs_button","type":"local","label":"gs_button","localed":false,"css":".gs_button{text-decoration:none;display:inline-block;position:relative;overflow:hidden;border-radius:var(--wp--custom--button--border-radius, 15px);padding:var(--wp--custom--button--spacing--vertical, 1rem) var(--wp--custom--button--spacing--horizontal, 2.25rem);background-color:var(--wp--custom--button--background, #33EFAB);color:var(--wp--custom--button--text, #000002);}.gs_button:hover{background-color:var(--wp--custom--button--background-hover, #7AFFCE);}","attributes":{"styleAttributes":{"textDecoration":["none"],"display":["inline-block"],"position":["relative"],"overflow":["hidden"],"borderRadius":["var(--wp--custom--button--border-radius, 15px)"],"padding":["var(--wp--custom--button--spacing--vertical, 1rem) var(--wp--custom--button--spacing--horizontal, 2.25rem)"],"backgroundColor":["var(--wp--custom--button--background, #33EFAB)"],"color":["var(--wp--custom--button--text, #000002)"],"backgroundColor_hover":["var(--wp--custom--button--background-hover, #7AFFCE)"]}},"originalBlock":"greenshift-blocks/element","selectors":[]}],"textContent":"Get Started","tag":"a","className":"gs-parent-hover gs_button","localId":"gsbp-b65d91f","href":"#","dynamicAttributes":[{"name":"data-type","value":"button-component"}],"isVariation":"buttoncomponent"} -->
<a class="gs-parent-hover gs_button" href="#" data-type="button-component">Get Started</a>
<!-- /wp:greenshift-blocks/element -->
```

## Accordion Component

Expandable content sections:

```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-4893b17","dynamicGClasses":[{"value":"gs_accordion_273","type":"local","label":"gs_accordion_273","localed":false,"css":"","attributes":{"styleAttributes":{}},"originalBlock":"greenshift-blocks/element","selectors":[{"value":" > .gs_item","attributes":{"styleAttributes":{"borderRadius":["8px"],"overflow":["hidden"],"borderWidth":["1px"],"borderStyle":["solid"],"borderColor":["var(--wp--preset--color--border, #00000012)"]}},"css":".gs_accordion_273 > .gs_item{border-radius:8px;overflow:hidden;border:1px solid var(--wp--preset--color--border, #00000012);}"},{"value":" .gs_title","attributes":{"styleAttributes":{"margin":["0px"],"padding":["0px"]}},"css":".gs_accordion_273 .gs_title{margin:0;padding:0;}"},{"value":" .gs_title button","attributes":{"styleAttributes":{"fontSize":["1rem"],"backgroundColor":["#0000000d"],"border":["none"],"padding":["1rem 1.5rem"],"fontWeight":["normal"],"display":["flex"],"justifyContent":["space-between"],"alignItems":["center"],"width":["100%"],"color":["#000000"],"cursor":["pointer"],"columnGap":["5px"]}},"css":".gs_accordion_273 .gs_title button{font-size:1rem;background-color:#0000000d;border:none;padding:1rem 1.5rem;display:flex;justify-content:space-between;align-items:center;width:100%;cursor:pointer;}"},{"value":" .gs_title .gs_icon","attributes":{"styleAttributes":{"width":["17px"],"height":["17px"],"transition":["all 0.5s ease"]}},"css":".gs_accordion_273 .gs_title .gs_icon{width:17px;height:17px;transition:all 0.5s ease;}"},{"value":"> .gs_item > .gs_content","attributes":{"styleAttributes":{"maxHeight":["0px"],"overflow":["hidden"],"transition":["max-height 0.5s cubic-bezier(0.42, 0, 0.58, 1), opacity 0.4s"],"opacity":["0"]}},"css":".gs_accordion_273 > .gs_item > .gs_content{max-height:0;overflow:hidden;opacity:0;transition:max-height 0.5s, opacity 0.4s;}"},{"value":" > .gs_item[data-active] > .gs_content","attributes":{"styleAttributes":{"maxHeight":["5000px"],"opacity":["1"]}},"css":".gs_accordion_273 > .gs_item[data-active] > .gs_content{max-height:5000px;opacity:1;}"},{"value":" .gs_content > .gs_content_inner","attributes":{"styleAttributes":{"padding":["25px"],"fontSize":["1rem"],"lineHeight":["1.3rem"]}},"css":".gs_accordion_273 .gs_content > .gs_content_inner{padding:25px;font-size:1rem;line-height:1.3rem;}"},{"value":" > .gs_item[data-active] > .gs_title .gs_icon","attributes":{"styleAttributes":{"transform":["rotate(90deg)"]}},"css":".gs_accordion_273 > .gs_item[data-active] > .gs_title .gs_icon{transform:rotate(90deg);}"}]}],"type":"inner","className":"gs_accordion_273 gs_collapsible","localId":"gsbp-4893b17","dynamicAttributes":[{"name":"data-type","value":"accordion-component"}],"styleAttributes":{"position":["relative"],"display":["flex"],"flexDirection":["column"],"rowGap":["15px"]},"isVariation":"accordion"} -->
<div class="gs_accordion_273 gs_collapsible gsbp-4893b17" data-type="accordion-component"><!-- wp:greenshift-blocks/element {"id":"gsbp-1d542bc","type":"inner","className":"gs_item","localId":"gsbp-1d542bc","metadata":{"name":"Accordion Item"}} -->
<div class="gs_item"><!-- wp:greenshift-blocks/element {"id":"gsbp-792c75d","tag":"h3","type":"inner","className":"gs_title","localId":"gsbp-792c75d","metadata":{"name":"Accordion Title"}} -->
<h3 class="gs_title"><!-- wp:greenshift-blocks/element {"id":"gsbp-594799c","tag":"button","type":"inner","className":"gs_click_sync","localId":"gsbp-594799c","formAttributes":{"type":"button"},"dynamicAttributes":[{"name":"aria-expanded","value":"false"}]} -->
<button class="gs_click_sync" type="button" aria-expanded="false"><!-- wp:greenshift-blocks/element {"id":"gsbp-26b9872","textContent":"Accordion Title","tag":"span","className":"gs_name","localId":"gsbp-26b9872"} -->
<span class="gs_name">Accordion Title</span>
<!-- /wp:greenshift-blocks/element -->

<!-- wp:greenshift-blocks/element {"id":"gsbp-d28e742","tag":"svg","icon":{"icon":{"font":"rhicon rhi-chevron-right","svg":"","image":""},"type":"font"},"className":"gs_icon","localId":"gsbp-d28e742"} -->
<svg viewBox="0 0 512 1024" width="512" height="1024" class="gs_icon"><path d="M49.414 76.202l-39.598 39.596c-9.372 9.372-9.372 24.568 0 33.942l361.398 362.26-361.398 362.26c-9.372 9.372-9.372 24.568 0 33.942l39.598 39.598c9.372 9.372 24.568 9.372 33.942 0l418.828-418.828c9.372-9.372 9.372-24.568 0-33.942l-418.828-418.828c-9.374-9.374-24.57-9.374-33.942 0z" /></svg>
<!-- /wp:greenshift-blocks/element --></button>
<!-- /wp:greenshift-blocks/element --></h3>
<!-- /wp:greenshift-blocks/element -->

<!-- wp:greenshift-blocks/element {"id":"gsbp-b31dbe5","type":"inner","className":"gs_content","localId":"gsbp-b31dbe5","dynamicAttributes":[{"name":"role","value":"region"},{"name":"aria-hidden","value":"true"}],"metadata":{"name":"Accordion Content"}} -->
<div class="gs_content" role="region" aria-hidden="true"><!-- wp:greenshift-blocks/element {"id":"gsbp-8ddb131","type":"inner","className":"gs_content_inner","localId":"gsbp-8ddb131"} -->
<div class="gs_content_inner">
<!-- Add your content here -->
</div>
<!-- /wp:greenshift-blocks/element --></div>
<!-- /wp:greenshift-blocks/element --></div>
<!-- /wp:greenshift-blocks/element --></div>
<!-- /wp:greenshift-blocks/element -->
```

## Tabs Component

Tabbed content navigation:

```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-286838a","dynamicGClasses":[{"value":"gs_tabs_517","type":"local","label":"gs_tabs_517","localed":false,"css":"","attributes":{"styleAttributes":{}},"originalBlock":"greenshift-blocks/element","selectors":[{"value":" .gs_tab","attributes":{"styleAttributes":{"fontSize":["1rem"],"backgroundColor":["#0000000d"],"border":["none"],"padding":["1rem 1.5rem"],"display":["flex"],"justifyContent":["center"],"alignItems":["center"],"color":["#000000"],"cursor":["pointer"],"columnGap":["10px"],"transition":["all 0.5s ease"]}},"css":".gs_tabs_517 .gs_tab{font-size:1rem;background-color:#0000000d;border:none;padding:1rem 1.5rem;display:flex;justify-content:center;align-items:center;cursor:pointer;transition:all 0.5s ease;}"},{"value":" .gs_tab.active","attributes":{"styleAttributes":{"backgroundColor":["#000000"],"color":["#fff"]}},"css":".gs_tabs_517 .gs_tab.active{background-color:#000000;color:#fff;}"},{"value":" .gs_content","attributes":{"styleAttributes":{"overflow":["hidden"],"opacity":["0"],"maxHeight":["0px"],"transition":["opacity 0.5s, max-height 0.5s"]}},"css":".gs_tabs_517 .gs_content{overflow:hidden;opacity:0;max-height:0;transition:opacity 0.5s, max-height 0.5s;}"},{"value":" .gs_content.active","attributes":{"styleAttributes":{"opacity":["1"],"maxHeight":["5000px"]}},"css":".gs_tabs_517 .gs_content.active{opacity:1;max-height:5000px;}"},{"value":" .gs_content > .gs_content_inner","attributes":{"styleAttributes":{"padding":["25px"],"fontSize":["1rem"],"lineHeight":["1.3rem"]}},"css":".gs_tabs_517 .gs_content > .gs_content_inner{padding:25px;font-size:1rem;line-height:1.3rem;}"}]}],"type":"inner","className":"gs_tabs_517 gs_root","localId":"gsbp-286838a","styleAttributes":{"position":["relative"],"display":["flex"],"flexDirection":["column"]},"isVariation":"tabs","dynamicAttributes":[{"name":"data-type","value":"tabs-component"}]} -->
<div class="gs_tabs_517 gs_root gsbp-286838a" data-type="tabs-component"><!-- wp:greenshift-blocks/element {"id":"gsbp-bd7643f","type":"inner","className":"gs_tabs_list","localId":"gsbp-bd7643f","dynamicAttributes":[{"name":"role","value":"tablist"}],"styleAttributes":{"display":["flex"],"flexDirection":["row"],"columnGap":["15px"],"rowGap":["15px"],"flexWrap":["wrap"]},"isVariation":"tablist","metadata":{"name":"Tabs List Container"}} -->
<div class="gs_tabs_list gsbp-bd7643f" role="tablist"><!-- wp:greenshift-blocks/element {"id":"gsbp-1cdb7ec","tag":"button","type":"inner","className":"gs_click_sync gs_tab active","localId":"gsbp-1cdb7ec","formAttributes":{"type":"button"},"dynamicAttributes":[{"name":"role","value":"tab"},{"name":"aria-selected","value":"true"}]} -->
<button class="gs_click_sync gs_tab active" type="button" role="tab" aria-selected="true"><!-- wp:greenshift-blocks/element {"id":"gsbp-ffc0456","textContent":"Tab 1","tag":"span","className":"gs_name","localId":"gsbp-ffc0456"} -->
<span class="gs_name">Tab 1</span>
<!-- /wp:greenshift-blocks/element --></button>
<!-- /wp:greenshift-blocks/element -->

<!-- wp:greenshift-blocks/element {"id":"gsbp-1b868fa","tag":"button","type":"inner","className":"gs_click_sync gs_tab","localId":"gsbp-1b868fa","formAttributes":{"type":"button"},"dynamicAttributes":[{"name":"role","value":"tab"},{"name":"aria-selected","value":"false"}]} -->
<button class="gs_click_sync gs_tab" type="button" role="tab" aria-selected="false"><!-- wp:greenshift-blocks/element {"id":"gsbp-ef77a6c","textContent":"Tab 2","tag":"span","className":"gs_name","localId":"gsbp-ef77a6c"} -->
<span class="gs_name">Tab 2</span>
<!-- /wp:greenshift-blocks/element --></button>
<!-- /wp:greenshift-blocks/element --></div>
<!-- /wp:greenshift-blocks/element -->

<!-- wp:greenshift-blocks/element {"id":"gsbp-ef872f3","type":"inner","className":"gs_content_area","localId":"gsbp-ef872f3","metadata":{"name":"Tabs Content Area"}} -->
<div class="gs_content_area"><!-- wp:greenshift-blocks/element {"id":"gsbp-e607d98","type":"inner","className":"gs_content active","localId":"gsbp-e607d98","dynamicAttributes":[{"name":"role","value":"tabpanel"},{"name":"aria-hidden","value":"false"}]} -->
<div class="gs_content active" role="tabpanel" aria-hidden="false"><!-- wp:greenshift-blocks/element {"id":"gsbp-a03c216","type":"inner","className":"gs_content_inner","localId":"gsbp-a03c216"} -->
<div class="gs_content_inner">
<!-- Tab 1 content -->
</div>
<!-- /wp:greenshift-blocks/element --></div>
<!-- /wp:greenshift-blocks/element -->

<!-- wp:greenshift-blocks/element {"id":"gsbp-d6a08f5","type":"inner","className":"gs_content","localId":"gsbp-d6a08f5","dynamicAttributes":[{"name":"role","value":"tabpanel"},{"name":"aria-hidden","value":"true"}]} -->
<div class="gs_content" role="tabpanel" aria-hidden="true"><!-- wp:greenshift-blocks/element {"id":"gsbp-691e301","type":"inner","className":"gs_content_inner","localId":"gsbp-691e301"} -->
<div class="gs_content_inner">
<!-- Tab 2 content -->
</div>
<!-- /wp:greenshift-blocks/element --></div>
<!-- /wp:greenshift-blocks/element --></div>
<!-- /wp:greenshift-blocks/element --></div>
<!-- /wp:greenshift-blocks/element -->
```

## Counter Component

Animated number counter:

```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-bfa10e7","textContent":"0","localId":"gsbp-bfa10e7","styleAttributes":{"fontSize":["50px"],"lineHeight":["50px"],"minHeight":["50px"],"minWidth":["50px"],"display":["inline-block"],"position":["relative"],"fontWeight":["700"]},"isVariation":"counter","endNumber":1500,"durationNumber":2,"offsetNumber":50,"stepNumber":1} -->
<div class="gsbp-bfa10e7" data-gs-counter="{&quot;end&quot;:1500,&quot;duration&quot;:2,&quot;offset&quot;:50,&quot;step&quot;:1}">0</div>
<!-- /wp:greenshift-blocks/element -->
```

**Parameters:**
- `endNumber`: Target number
- `durationNumber`: Animation duration in seconds
- `offsetNumber`: Viewport offset to trigger
- `stepNumber`: Increment step

## Countdown Timer

```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-f1aff34","dynamicGClasses":[{"value":"gs_countdown_169","type":"local","label":"gs_countdown_169","localed":false,"css":"","attributes":{"styleAttributes":{}},"originalBlock":"greenshift-blocks/element","selectors":[{"value":" .gs_countdown_item","attributes":{"styleAttributes":{"fontSize":["2rem"],"fontWeight":["bold"],"lineHeight":["2.3rem"]}},"css":".gs_countdown_169 .gs_countdown_item{font-size:2rem;font-weight:bold;line-height:2.3rem;}"},{"value":" .gs_date_divider","attributes":{"styleAttributes":{"fontSize":["1.7rem"],"lineHeight":["2.3rem"]}},"css":".gs_countdown_169 .gs_date_divider{font-size:1.7rem;line-height:2.3rem;}"}]}],"type":"inner","className":"gs_countdown_169 gs_countdown","localId":"gsbp-f1aff34","styleAttributes":{"position":["relative"],"display":["flex"],"flexDirection":["row"],"rowGap":["5px"],"columnGap":["5px"],"alignItems":["center"]},"isVariation":"countdown","endtime":"2025-12-31T23:59:59"} -->
<div class="gs_countdown_169 gs_countdown gsbp-f1aff34" data-end="2025-12-31T23:59:59"><!-- wp:greenshift-blocks/element {"id":"gsbp-51ed6cd","textContent":"00","tag":"span","className":"gs_days gs_countdown_item","localId":"gsbp-51ed6cd","metadata":{"name":"Countdown Days"}} -->
<span class="gs_days gs_countdown_item">00</span>
<!-- /wp:greenshift-blocks/element -->

<!-- wp:greenshift-blocks/element {"id":"gsbp-70defd7","textContent":":","tag":"span","className":"gs_date_divider","localId":"gsbp-70defd7"} -->
<span class="gs_date_divider">:</span>
<!-- /wp:greenshift-blocks/element -->

<!-- wp:greenshift-blocks/element {"id":"gsbp-7dc06fd","textContent":"00","tag":"span","className":"gs_hours gs_countdown_item","localId":"gsbp-7dc06fd"} -->
<span class="gs_hours gs_countdown_item">00</span>
<!-- /wp:greenshift-blocks/element -->

<!-- wp:greenshift-blocks/element {"id":"gsbp-4369f65","textContent":":","tag":"span","className":"gs_date_divider","localId":"gsbp-4369f65"} -->
<span class="gs_date_divider">:</span>
<!-- /wp:greenshift-blocks/element -->

<!-- wp:greenshift-blocks/element {"id":"gsbp-98cb8df","textContent":"00","tag":"span","className":"gs_minutes gs_countdown_item","localId":"gsbp-98cb8df"} -->
<span class="gs_minutes gs_countdown_item">00</span>
<!-- /wp:greenshift-blocks/element -->

<!-- wp:greenshift-blocks/element {"id":"gsbp-1840d36","textContent":":","tag":"span","className":"gs_date_divider","localId":"gsbp-1840d36"} -->
<span class="gs_date_divider">:</span>
<!-- /wp:greenshift-blocks/element -->

<!-- wp:greenshift-blocks/element {"id":"gsbp-005157f","textContent":"00","tag":"span","className":"gs_seconds gs_countdown_item","localId":"gsbp-005157f"} -->
<span class="gs_seconds gs_countdown_item">00</span>
<!-- /wp:greenshift-blocks/element --></div>
<!-- /wp:greenshift-blocks/element -->
```

## Marquee/Scroll Animation

```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-ee95a85","type":"inner","localId":"gsbp-ee95a85","marqueeSpeed":12,"isVariation":"marquee","styleAttributes":{"overflow":["hidden"]}} -->
<div class="gsbp-ee95a85"><div class="gspb_marquee_content"><!-- wp:greenshift-blocks/element {"id":"gsbp-a7ca8ce","textContent":"Your scrolling text here","tag":"span","localId":"gsbp-a7ca8ce","styleAttributes":{"fontSize":["30px"],"paddingRight":["50px"]}} -->
<span class="gsbp-a7ca8ce">Your scrolling text here</span>
<!-- /wp:greenshift-blocks/element --><span class="gspb_marquee_content_end"></span></div></div>
<!-- /wp:greenshift-blocks/element -->
```

## Video Lightbox

Play button with video popup:

```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-fc481da","dynamicGClasses":[{"value":"gs_videolightbox_853","type":"local","label":"gs_videolightbox_853","localed":false,"css":"","attributes":{"styleAttributes":{}},"originalBlock":"greenshift-blocks/element","selectors":[{"value":" .play_button_pulse","attributes":{"styleAttributes":{"position":["absolute"],"width":["80px"],"height":["80px"],"borderRadius":["50%"],"backgroundColor":["#ff0000"],"border":["none"],"cursor":["pointer"],"display":["flex"],"alignItems":["center"],"justifyContent":["center"],"zIndex":["1"]}},"css":".gs_videolightbox_853 .play_button_pulse{position:absolute;width:80px;height:80px;border-radius:50%;background-color:#ff0000;border:none;cursor:pointer;display:flex;align-items:center;justify-content:center;z-index:1;}"},{"value":" .play_button_pulse::before","attributes":{"styleAttributes":{"content":["\"\""],"borderRadius":["50%"],"animation":["pulse-ring 2s cubic-bezier(0.215, 0.61, 0.355, 1) infinite"],"position":["absolute"],"inset":["0"],"borderWidth":["1px"],"borderStyle":["solid"],"borderColor":["#ff0000"]}},"css":".gs_videolightbox_853 .play_button_pulse::before{content:\"\";border-radius:50%;animation:pulse-ring 2s infinite;position:absolute;inset:0;border:1px solid #ff0000;}"}]}],"interactionLayers":[{"actions":[{"actionname":"lightbox"}],"env":"no-action","triggerData":{"trigger":"click"}}],"type":"inner","className":"gs_videolightbox_853","localId":"gsbp-fc481da","styleAttributes":{"position":["relative"],"display":["flex"],"justifyContent":["center"],"alignItems":["center"]},"isVariation":"videolightbox","dynamicAttributes":[{"name":"data-type","value":"video-lightbox-component"}]} -->
<div data-gspbactions="[{&quot;actions&quot;:[{&quot;actionname&quot;:&quot;lightbox&quot;}],&quot;env&quot;:&quot;no-action&quot;,&quot;triggerData&quot;:{&quot;trigger&quot;:&quot;click&quot;}}]" class="gs_videolightbox_853 gsbp-fc481da" data-type="video-lightbox-component"><!-- wp:greenshift-blocks/element {"id":"gsbp-2f4769b","tag":"button","type":"inner","className":"play_button_pulse","localId":"gsbp-2f4769b","formAttributes":{"type":"button"}} -->
<button class="play_button_pulse" type="button"><!-- wp:greenshift-blocks/element {"id":"gsbp-89c9513","tag":"svg","icon":{"icon":{"svg":"<svg viewBox=\"0 0 100 100\"><polygon points=\"30,20 30,80 70,50\" fill=\"#ffffff\"/></svg>","image":""},"fill":"currentColor","type":"svg"},"localId":"gsbp-89c9513","styleAttributes":{"width":["30px"],"height":["30px"],"color":["#ffffff"]}} -->
<svg viewBox="0 0 100 100" width="100" height="100" class="gsbp-89c9513"><polygon points="30,20 30,80 70,50" fill="#ffffff"/></svg>
<!-- /wp:greenshift-blocks/element --></button>
<!-- /wp:greenshift-blocks/element -->

<!-- wp:greenshift-blocks/element {"id":"gsbp-745540d","tag":"img","localId":"gsbp-745540d","src":"https://placehold.co/1280x720","alt":"Video thumbnail","styleAttributes":{"aspectRatio":["16/9"],"objectFit":["cover"],"width":["100%"]}} -->
<img class="gsbp-745540d" src="https://placehold.co/1280x720" alt="Video thumbnail" loading="lazy"/>
<!-- /wp:greenshift-blocks/element --></div>
<!-- /wp:greenshift-blocks/element -->
```

## Table Component

```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-7f2c7b7","tag":"table","type":"inner","localId":"gsbp-7f2c7b7","tableAttributes":{"table":{"responsive":"yes"}},"tableStyles":{"table":{"layout":"fixed","border":"collapse"},"responsive":"yes","td":{"paddingTop":["6px"],"paddingBottom":["6px"],"paddingRight":["12px"],"paddingLeft":["12px"],"borderStyle":"solid","borderWidth":"1px","borderColor":"var(--wp--preset--color--border, #00000012)","fontSize":["14px"]},"th":{"paddingTop":["6px"],"paddingBottom":["6px"],"paddingRight":["12px"],"paddingLeft":["12px"],"borderStyle":"solid","borderWidth":"1px","borderColor":"var(--wp--preset--color--border, #00000012)","fontSize":["16px"],"backgroundColor":"var(--wp--preset--color--lightbg, #cddceb21)"}},"styleAttributes":{"width":["100%"]}} -->
<table class="gsbp-7f2c7b7"><!-- wp:greenshift-blocks/element {"id":"gsbp-86384cd","tag":"tr","type":"inner","localId":"gsbp-86384cd"} -->
<tr><!-- wp:greenshift-blocks/element {"id":"gsbp-d14108c","textContent":"Header 1","tag":"th","localId":"gsbp-d14108c"} -->
<th>Header 1</th>
<!-- /wp:greenshift-blocks/element -->

<!-- wp:greenshift-blocks/element {"id":"gsbp-537d215","textContent":"Header 2","tag":"th","localId":"gsbp-537d215"} -->
<th>Header 2</th>
<!-- /wp:greenshift-blocks/element -->

<!-- wp:greenshift-blocks/element {"id":"gsbp-243d78a","textContent":"Header 3","tag":"th","localId":"gsbp-243d78a"} -->
<th>Header 3</th>
<!-- /wp:greenshift-blocks/element --></tr>
<!-- /wp:greenshift-blocks/element -->

<!-- wp:greenshift-blocks/element {"id":"gsbp-c811a76","tag":"tr","type":"inner","localId":"gsbp-c811a76"} -->
<tr><!-- wp:greenshift-blocks/element {"id":"gsbp-39de8a7","textContent":"Cell 1","tag":"td","localId":"gsbp-39de8a7"} -->
<td>Cell 1</td>
<!-- /wp:greenshift-blocks/element -->

<!-- wp:greenshift-blocks/element {"id":"gsbp-ecb7f59","textContent":"Cell 2","tag":"td","localId":"gsbp-ecb7f59"} -->
<td>Cell 2</td>
<!-- /wp:greenshift-blocks/element -->

<!-- wp:greenshift-blocks/element {"id":"gsbp-cce32f2","textContent":"Cell 3","tag":"td","localId":"gsbp-cce32f2"} -->
<td>Cell 3</td>
<!-- /wp:greenshift-blocks/element --></tr>
<!-- /wp:greenshift-blocks/element --></table>
<!-- /wp:greenshift-blocks/element -->
```

## Video Embed (YouTube)

For background video or inline video:

```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-c1db4cc","tag":"iframe","localId":"gsbp-c1db4cc","src":"https://www.youtube.com/embed/VIDEO_ID?autoplay=1&mute=1&loop=1","dynamicAttributes":[{"name":"allow","value":"accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"},{"name":"allowfullscreen","value":"true"}],"styleAttributes":{"aspectRatio":["16/9"],"display":["block"],"objectFit":["cover"],"width":["100%"],"pointerEvents":["none"]},"isVariation":"youtubeplay"} -->
<iframe class="gsbp-c1db4cc" src="https://www.youtube.com/embed/VIDEO_ID?autoplay=1&mute=1&loop=1" frameborder="0" loading="lazy" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
<!-- /wp:greenshift-blocks/element -->
```

## Self-Hosted Video

```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-74e2fe8","tag":"video","localId":"gsbp-74e2fe8","src":"https://example.com/video.mp4","alt":"","originalWidth":1920,"originalHeight":1080,"loop":true,"controls":true,"muted":true,"autoplay":true,"playsinline":true,"styleAttributes":{"width":["100%"],"height":["auto"]}} -->
<video class="gsbp-74e2fe8" loop controls muted autoplay playsinline><source src="https://example.com/video.mp4" type="video/mp4"/></video>
<!-- /wp:greenshift-blocks/element -->
```
