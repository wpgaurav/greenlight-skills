# GL Page Builder Slider/Carousel Patterns

Create Swiper-based carousels and sliders using GL Page Builder.

## Basic Slider Structure

```html
<!-- wp:greenshift-blocks/swiper {"id":"gsbp-slider1","tabs":3,"slidesPerView":[1],"spaceBetween":[20],"speed":400,"loop":true,"autoplay":true,"autodelay":4000,"navigationarrows":true,"bullets":true,"styleAttributes":{}} -->
<div class="wp-block-greenshift-blocks-swiper gs-swiper gs-swiper-init gspb_slider-id-gsbp-slider1" style="position:relative" data-slidesperview="1" data-spacebetween="20" data-speed="400" data-loop="true" data-autoplay="true" data-autodelay="4000">
  <div class="swiper">
    <div class="swiper-wrapper">
      <!-- Slides go here -->
    </div>
  </div>
  <div class="swiper-pagination"></div>
  <div class="swiper-button-prev"></div>
  <div class="swiper-button-next"></div>
</div>
<!-- /wp:greenshift-blocks/swiper -->
```

## Individual Slide Structure

```html
<!-- wp:greenshift-blocks/swipe {"imageurl":"https://placehold.co/1200x600","imagealt":"Slide description","overlayBg":"#000000","id":"gsbp-slide1"} -->
<div class="swiper-slide">
  <div class="wp-block-greenshift-blocks-swipe swiper-slide-inner gspb_sliderinner-id-gsbp-slide1">
    <!-- Slide content blocks -->
    <div class="slider-bg">
      <div class="slider-overlaybg"></div>
      <div class="slider-image-wrapper">
        <img src="https://placehold.co/1200x600" alt="Slide description" width="100%" height="100%" loading="lazy"/>
      </div>
    </div>
  </div>
</div>
<!-- /wp:greenshift-blocks/swipe -->
```

## Slider Parameters

### Core Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `tabs` | integer | Number of slides |
| `slidesPerView` | array | Slides visible `[desktop, tablet, mobile_l, mobile_p]` |
| `spaceBetween` | array | Gap between slides (px) |
| `speed` | integer | Transition speed (ms) |
| `loop` | boolean | Infinite loop |
| `autoplay` | boolean | Auto-advance slides |
| `autodelay` | integer | Autoplay delay (ms) |

### Navigation

| Parameter | Type | Description |
|-----------|------|-------------|
| `navigationarrows` | boolean | Show prev/next arrows |
| `bullets` | boolean | Show pagination dots |
| `scrollbar` | boolean | Show scrollbar |
| `clicktoslide` | boolean | Click pagination to navigate |

### Behavior

| Parameter | Type | Description |
|-----------|------|-------------|
| `centered` | boolean | Center active slide |
| `freemode` | boolean | Momentum-based sliding |
| `grabcursor` | boolean | Show grab cursor |
| `vertical` | boolean | Vertical direction |
| `autoHeight` | boolean | Auto-adjust height |
| `enableKeyboard` | boolean | Keyboard navigation |
| `enableMousewheel` | boolean | Mousewheel navigation |

### Effects

| Parameter | Type | Description |
|-----------|------|-------------|
| `effect` | string | `""`, `"fade"`, `"cube"`, `"coverflow"`, `"flip"` |
| `parallax_enable` | boolean | Enable parallax |
| `kenBurnsEnable` | boolean | Ken Burns zoom effect |

## Complete Hero Slider

```html
<!-- wp:greenshift-blocks/swiper {"id":"gsbp-hero123","tabs":3,"slidesPerView":[1],"spaceBetween":[0],"speed":600,"loop":true,"autoplay":true,"autodelay":5000,"navigationarrows":true,"bullets":true,"effect":"fade","styleAttributes":{"height":["80vh","70vh","60vh","50vh"]}} -->
<div class="wp-block-greenshift-blocks-swiper gs-swiper gs-swiper-init gspb_slider-id-gsbp-hero123" style="position:relative" data-slidesperview="1" data-spacebetween="0" data-speed="600" data-loop="true" data-autoplay="true" data-autodelay="5000" data-effect="fade">
  <div class="swiper">
    <div class="swiper-wrapper">

<!-- Slide 1 -->
<!-- wp:greenshift-blocks/swipe {"imageurl":"https://placehold.co/1920x1080","imagealt":"Hero slide 1","overlayBg":"rgba(0,0,0,0.4)","id":"gsbp-herosl1"} -->
<div class="swiper-slide">
  <div class="wp-block-greenshift-blocks-swipe swiper-slide-inner gspb_sliderinner-id-gsbp-herosl1">
    <!-- wp:greenshift-blocks/element {"id":"gsbp-herocnt1","type":"inner","localId":"gsbp-herocnt1","styleAttributes":{"position":["relative"],"zIndex":["2"],"display":["flex"],"flexDirection":["column"],"justifyContent":["center"],"alignItems":["center"],"height":["100%"],"textAlign":["center"],"padding":["var(--wp--preset--spacing--60, 2.25rem)"]}} -->
    <div class="gsbp-herocnt1">
      <!-- wp:greenshift-blocks/element {"id":"gsbp-herottl1","textContent":"Welcome to Our Site","tag":"h1","localId":"gsbp-herottl1","styleAttributes":{"fontSize":["var(--wp--preset--font-size--giga, clamp(3rem, 5vw, 4.5rem))"],"color":["#ffffff"],"marginBottom":["var(--wp--preset--spacing--40, 1rem)"]}} -->
      <h1 class="gsbp-herottl1">Welcome to Our Site</h1>
      <!-- /wp:greenshift-blocks/element -->

      <!-- wp:greenshift-blocks/element {"id":"gsbp-herosub1","textContent":"Discover amazing things with us","tag":"p","localId":"gsbp-herosub1","styleAttributes":{"fontSize":["var(--wp--preset--font-size--l, 1.55rem)"],"color":["#ffffff"],"opacity":["0.9"],"marginBottom":["var(--wp--preset--spacing--50, 1.5rem)"]}} -->
      <p class="gsbp-herosub1">Discover amazing things with us</p>
      <!-- /wp:greenshift-blocks/element -->

      <!-- wp:greenshift-blocks/element {"id":"gsbp-herobtn1","textContent":"Get Started","tag":"a","localId":"gsbp-herobtn1","href":"#","styleAttributes":{"display":["inline-block"],"padding":["var(--wp--preset--spacing--40, 1rem) var(--wp--preset--spacing--60, 2.25rem)"],"backgroundColor":["var(--wp--preset--color--brand, #33EFAB)"],"color":["#000"],"borderRadius":["var(--wp--custom--border-radius--medium, 15px)"],"textDecoration":["none"],"fontWeight":["600"]}} -->
      <a class="gsbp-herobtn1" href="#">Get Started</a>
      <!-- /wp:greenshift-blocks/element -->
    </div>
    <!-- /wp:greenshift-blocks/element -->
    <div class="slider-bg">
      <div class="slider-overlaybg" style="background:rgba(0,0,0,0.4)"></div>
      <div class="slider-image-wrapper">
        <img src="https://placehold.co/1920x1080" alt="Hero slide 1" width="100%" height="100%" loading="lazy"/>
      </div>
    </div>
  </div>
</div>
<!-- /wp:greenshift-blocks/swipe -->

<!-- Slide 2 -->
<!-- wp:greenshift-blocks/swipe {"imageurl":"https://placehold.co/1920x1080","imagealt":"Hero slide 2","overlayBg":"rgba(0,0,0,0.4)","id":"gsbp-herosl2"} -->
<div class="swiper-slide">
  <div class="wp-block-greenshift-blocks-swipe swiper-slide-inner gspb_sliderinner-id-gsbp-herosl2">
    <!-- wp:greenshift-blocks/element {"id":"gsbp-herocnt2","type":"inner","localId":"gsbp-herocnt2","styleAttributes":{"position":["relative"],"zIndex":["2"],"display":["flex"],"flexDirection":["column"],"justifyContent":["center"],"alignItems":["center"],"height":["100%"],"textAlign":["center"],"padding":["var(--wp--preset--spacing--60, 2.25rem)"]}} -->
    <div class="gsbp-herocnt2">
      <!-- wp:greenshift-blocks/element {"id":"gsbp-herottl2","textContent":"Our Services","tag":"h1","localId":"gsbp-herottl2","styleAttributes":{"fontSize":["var(--wp--preset--font-size--giga, clamp(3rem, 5vw, 4.5rem))"],"color":["#ffffff"],"marginBottom":["var(--wp--preset--spacing--40, 1rem)"]}} -->
      <h1 class="gsbp-herottl2">Our Services</h1>
      <!-- /wp:greenshift-blocks/element -->

      <!-- wp:greenshift-blocks/element {"id":"gsbp-herosub2","textContent":"Professional solutions for your needs","tag":"p","localId":"gsbp-herosub2","styleAttributes":{"fontSize":["var(--wp--preset--font-size--l, 1.55rem)"],"color":["#ffffff"],"opacity":["0.9"],"marginBottom":["var(--wp--preset--spacing--50, 1.5rem)"]}} -->
      <p class="gsbp-herosub2">Professional solutions for your needs</p>
      <!-- /wp:greenshift-blocks/element -->
    </div>
    <!-- /wp:greenshift-blocks/element -->
    <div class="slider-bg">
      <div class="slider-overlaybg" style="background:rgba(0,0,0,0.4)"></div>
      <div class="slider-image-wrapper">
        <img src="https://placehold.co/1920x1080" alt="Hero slide 2" width="100%" height="100%" loading="lazy"/>
      </div>
    </div>
  </div>
</div>
<!-- /wp:greenshift-blocks/swipe -->

    </div>
  </div>
  <div class="swiper-pagination"></div>
  <div class="swiper-button-prev"></div>
  <div class="swiper-button-next"></div>
</div>
<!-- /wp:greenshift-blocks/swiper -->
```

## Testimonials Carousel

Multiple slides visible with responsive settings:

```html
<!-- wp:greenshift-blocks/swiper {"id":"gsbp-testimonials","tabs":4,"slidesPerView":[3,2,1,1],"spaceBetween":[30,20,15,15],"speed":500,"loop":true,"autoplay":true,"autodelay":4000,"bullets":true,"centered":true,"styleAttributes":{"paddingTop":["var(--wp--preset--spacing--50)"],"paddingBottom":["var(--wp--preset--spacing--70)"]}} -->
<div class="wp-block-greenshift-blocks-swiper gs-swiper gs-swiper-init gspb_slider-id-gsbp-testimonials" style="position:relative" data-slidesperview="3" data-slidesperviewmd="2" data-slidesperviewsm="1" data-slidesperviewxs="1" data-spacebetween="30" data-spacebetweenmd="20" data-spacebetweensm="15" data-speed="500" data-loop="true" data-autoplay="true" data-autodelay="4000" data-centered="true">
  <div class="swiper">
    <div class="swiper-wrapper">

<!-- Testimonial 1 -->
<!-- wp:greenshift-blocks/swipe {"id":"gsbp-test1"} -->
<div class="swiper-slide">
  <div class="wp-block-greenshift-blocks-swipe swiper-slide-inner gspb_sliderinner-id-gsbp-test1">
    <!-- wp:greenshift-blocks/element {"id":"gsbp-testcard1","type":"inner","localId":"gsbp-testcard1","styleAttributes":{"backgroundColor":["#ffffff"],"padding":["var(--wp--preset--spacing--50)"],"borderRadius":["var(--wp--custom--border-radius--medium, 15px)"],"boxShadow":["var(--wp--preset--shadow--soft)"],"textAlign":["center"]}} -->
    <div class="gsbp-testcard1">
      <!-- wp:greenshift-blocks/element {"id":"gsbp-testavt1","tag":"img","localId":"gsbp-testavt1","src":"https://placehold.co/80x80","alt":"Customer photo","originalWidth":80,"originalHeight":80,"styleAttributes":{"width":["80px"],"height":["80px"],"borderRadius":["50%"],"objectFit":["cover"],"marginBottom":["var(--wp--preset--spacing--40)"]}} -->
      <img class="gsbp-testavt1" src="https://placehold.co/80x80" alt="Customer photo" width="80" height="80" loading="lazy"/>
      <!-- /wp:greenshift-blocks/element -->

      <!-- wp:greenshift-blocks/element {"id":"gsbp-testquote1","textContent":"This product changed my life! Highly recommended to everyone.","tag":"p","localId":"gsbp-testquote1","styleAttributes":{"fontSize":["var(--wp--preset--font-size--r, 1.2rem)"],"fontStyle":["italic"],"marginBottom":["var(--wp--preset--spacing--40)"],"lineHeight":["1.6"]}} -->
      <p class="gsbp-testquote1">This product changed my life! Highly recommended to everyone.</p>
      <!-- /wp:greenshift-blocks/element -->

      <!-- wp:greenshift-blocks/element {"id":"gsbp-testname1","textContent":"John Doe","tag":"strong","localId":"gsbp-testname1","styleAttributes":{"display":["block"],"marginBottom":["4px"]}} -->
      <strong class="gsbp-testname1">John Doe</strong>
      <!-- /wp:greenshift-blocks/element -->

      <!-- wp:greenshift-blocks/element {"id":"gsbp-testrole1","textContent":"CEO, Company","tag":"span","localId":"gsbp-testrole1","styleAttributes":{"fontSize":["var(--wp--preset--font-size--xs)"],"opacity":["0.7"]}} -->
      <span class="gsbp-testrole1">CEO, Company</span>
      <!-- /wp:greenshift-blocks/element -->
    </div>
    <!-- /wp:greenshift-blocks/element -->
  </div>
</div>
<!-- /wp:greenshift-blocks/swipe -->

<!-- Add more testimonials... -->

    </div>
  </div>
  <div class="swiper-pagination"></div>
</div>
<!-- /wp:greenshift-blocks/swiper -->
```

## Logo Carousel

Auto-playing logo slider:

```html
<!-- wp:greenshift-blocks/swiper {"id":"gsbp-logos","tabs":6,"slidesPerView":[5,4,3,2],"spaceBetween":[40,30,20,15],"speed":3000,"loop":true,"autoplay":true,"autodelay":0,"freemode":true,"grabcursor":true,"styleAttributes":{"paddingTop":["var(--wp--preset--spacing--50)"],"paddingBottom":["var(--wp--preset--spacing--50)"]}} -->
<div class="wp-block-greenshift-blocks-swiper gs-swiper gs-swiper-init gspb_slider-id-gsbp-logos" style="position:relative" data-slidesperview="5" data-slidesperviewmd="4" data-slidesperviewsm="3" data-slidesperviewxs="2" data-spacebetween="40" data-speed="3000" data-loop="true" data-autoplay="true" data-autodelay="0" data-freemode="true">
  <div class="swiper">
    <div class="swiper-wrapper">

<!-- Logo slides -->
<!-- wp:greenshift-blocks/swipe {"id":"gsbp-logo1"} -->
<div class="swiper-slide">
  <div class="wp-block-greenshift-blocks-swipe swiper-slide-inner">
    <!-- wp:greenshift-blocks/element {"id":"gsbp-logoimg1","tag":"img","localId":"gsbp-logoimg1","src":"https://placehold.co/200x80","alt":"Partner logo","styleAttributes":{"width":["100%"],"height":["auto"],"opacity":["0.6"],"opacity_hover":["1"],"transition":["opacity 0.3s ease"],"filter":["grayscale(100%)"],"filter_hover":["grayscale(0%)"]}} -->
    <img class="gsbp-logoimg1" src="https://placehold.co/200x80" alt="Partner logo" loading="lazy"/>
    <!-- /wp:greenshift-blocks/element -->
  </div>
</div>
<!-- /wp:greenshift-blocks/swipe -->

<!-- Add more logos... -->

    </div>
  </div>
</div>
<!-- /wp:greenshift-blocks/swiper -->
```

## Product Carousel

E-commerce style with multiple visible products:

```html
<!-- wp:greenshift-blocks/swiper {"id":"gsbp-products","tabs":8,"slidesPerView":[4,3,2,1],"spaceBetween":[24,20,16,12],"speed":400,"navigationarrows":true,"styleAttributes":{}} -->
<div class="wp-block-greenshift-blocks-swiper gs-swiper gs-swiper-init gspb_slider-id-gsbp-products" style="position:relative" data-slidesperview="4" data-slidesperviewmd="3" data-slidesperviewsm="2" data-slidesperviewxs="1" data-spacebetween="24" data-speed="400">
  <div class="swiper">
    <div class="swiper-wrapper">

<!-- Product Slide -->
<!-- wp:greenshift-blocks/swipe {"id":"gsbp-prod1"} -->
<div class="swiper-slide">
  <div class="wp-block-greenshift-blocks-swipe swiper-slide-inner">
    <!-- wp:greenshift-blocks/element {"id":"gsbp-prodcard1","type":"inner","localId":"gsbp-prodcard1","styleAttributes":{"backgroundColor":["#ffffff"],"borderRadius":["var(--wp--custom--border-radius--small)"],"overflow":["hidden"],"boxShadow":["var(--wp--preset--shadow--soft)"],"transition":["var(--wp--custom--transition--ease)"],"transform_hover":["translateY(-4px)"]}} -->
    <div class="gsbp-prodcard1">
      <!-- wp:greenshift-blocks/element {"id":"gsbp-prodimg1","tag":"img","localId":"gsbp-prodimg1","src":"https://placehold.co/400x400","alt":"Product image","styleAttributes":{"width":["100%"],"aspectRatio":["1/1"],"objectFit":["cover"]}} -->
      <img class="gsbp-prodimg1" src="https://placehold.co/400x400" alt="Product image" loading="lazy"/>
      <!-- /wp:greenshift-blocks/element -->

      <!-- wp:greenshift-blocks/element {"id":"gsbp-prodinfo1","type":"inner","localId":"gsbp-prodinfo1","styleAttributes":{"padding":["var(--wp--preset--spacing--40)"]}} -->
      <div class="gsbp-prodinfo1">
        <!-- wp:greenshift-blocks/element {"id":"gsbp-prodname1","textContent":"Product Name","tag":"h3","localId":"gsbp-prodname1","styleAttributes":{"fontSize":["var(--wp--preset--font-size--r)"],"marginBottom":["8px"]}} -->
        <h3 class="gsbp-prodname1">Product Name</h3>
        <!-- /wp:greenshift-blocks/element -->

        <!-- wp:greenshift-blocks/element {"id":"gsbp-prodprice1","textContent":"$99.00","tag":"span","localId":"gsbp-prodprice1","styleAttributes":{"fontSize":["var(--wp--preset--font-size--m)"],"fontWeight":["700"],"color":["var(--wp--preset--color--brand)"]}} -->
        <span class="gsbp-prodprice1">$99.00</span>
        <!-- /wp:greenshift-blocks/element -->
      </div>
      <!-- /wp:greenshift-blocks/element -->
    </div>
    <!-- /wp:greenshift-blocks/element -->
  </div>
</div>
<!-- /wp:greenshift-blocks/swipe -->

<!-- Add more products... -->

    </div>
  </div>
  <div class="swiper-button-prev"></div>
  <div class="swiper-button-next"></div>
</div>
<!-- /wp:greenshift-blocks/swiper -->
```

## Vertical Slider

```html
<!-- wp:greenshift-blocks/swiper {"id":"gsbp-vertical","tabs":4,"slidesPerView":[1],"spaceBetween":[20],"speed":500,"vertical":true,"verticalheight":"500px","navigationarrows":true,"styleAttributes":{"height":["500px"]}} -->
```

## Coverflow Effect

```html
<!-- wp:greenshift-blocks/swiper {"id":"gsbp-coverflow","tabs":5,"slidesPerView":[3,2,1,1],"spaceBetween":[30],"speed":500,"loop":true,"centered":true,"effect":"coverflow","coverflowshadow":true,"styleAttributes":{}} -->
```

## Slider Data Attributes Reference

The HTML output uses data attributes for Swiper initialization:

| Data Attribute | Description |
|---------------|-------------|
| `data-slidesperview` | Desktop slides per view |
| `data-slidesperviewmd` | Tablet slides per view |
| `data-slidesperviewsm` | Mobile landscape slides |
| `data-slidesperviewxs` | Mobile portrait slides |
| `data-spacebetween` | Gap between slides |
| `data-speed` | Transition speed |
| `data-loop` | Enable loop |
| `data-autoplay` | Enable autoplay |
| `data-autodelay` | Autoplay delay |
| `data-vertical` | Vertical mode |
| `data-effect` | Transition effect |
| `data-centered` | Center active slide |
| `data-freemode` | Free mode |
