# GL Page Builder Dynamic Content

Create dynamic content blocks that pull data from WordPress posts, users, taxonomies, and custom fields.

## Dynamic Text Configuration

Dynamic content uses the `dynamictext` attribute:

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

Text content wraps in `<dynamictext>` tags:
```html
<div><dynamictext>Placeholder text</dynamictext></div>
```

## Query Grid Block

Display posts, products, or custom post types:

```html
<!-- wp:greenshift-blocks/querygrid {"id":"gsbp-qry1234","data_source":"query","query_filters":{"post_type":"post","posts_per_page":6,"orderby":"date","order":"DESC"},"styleAttributesWrapper":{"display":["flex"],"columnGap":["var(--wp--preset--spacing--50, 1.5rem)"],"rowGap":["var(--wp--preset--spacing--50, 1.5rem)"],"flexWrap":["wrap"],"flexColumns_Extra":3,"flexWidths_Extra":{"desktop":{"name":"33/33/33","widths":[33.33,33.33,33.33]},"tablet":{"name":"50/50/50","widths":[50,50,50]},"mobile":{"name":"100/100/100","widths":[100,100,100]}}},"styleAttributesItem":{"backgroundColor":["#ffffff"],"borderRadius":["var(--wp--custom--border-radius--small, 10px)"],"overflow":["hidden"],"boxShadow":["var(--wp--preset--shadow--soft)"]}} -->
<!-- Inner template blocks go here -->
<!-- /wp:greenshift-blocks/querygrid -->
```

### Query Filters (WP_Query args)

```json
{
  "query_filters": {
    "post_type": "post",
    "posts_per_page": 6,
    "orderby": "date",
    "order": "DESC",
    "post_status": "publish",
    "category__in": [1, 2, 3],
    "tag__in": [4, 5],
    "meta_key": "custom_field",
    "meta_value": "value",
    "meta_query": [
      {
        "key": "featured",
        "value": "1",
        "compare": "="
      }
    ]
  }
}
```

## Dynamic Data Types

### 1. Post Data (`dynamicType: "postdata"`)

Available `dynamicPostData` values:

| Value | Description |
|-------|-------------|
| `post_title` | Post title |
| `post_image` | Featured image |
| `ID` | Post ID |
| `post_date` | Publish date |
| `post_modified` | Last modified date |
| `post_excerpt` | Post excerpt |
| `comment_count` | Number of comments |
| `permalink` | Post URL |
| `fullcontent` | Full content (unformatted) |
| `fullcontentfilters` | Full content (formatted) |
| `post_author` | Author name |
| `post_name` | Post slug |
| `post_parent_title` | Parent post title |
| `post_parent_link` | Parent post link |

**Example - Post Title:**
```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-ttl1234","textContent":"<dynamictext>Post Title</dynamictext>","tag":"h2","dynamictext":{"dynamicEnable":true,"dynamicType":"postdata","dynamicSource":"latest_item","dynamicPostData":"post_title"},"localId":"gsbp-ttl1234","styleAttributes":{"fontSize":["var(--wp--preset--font-size--l, 1.55rem)"],"fontWeight":["600"]}} -->
<h2 class="gsbp-ttl1234"><dynamictext>Post Title</dynamictext></h2>
<!-- /wp:greenshift-blocks/element -->
```

**Example - Featured Image:**
```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-img1234","tag":"img","dynamiclink":{"dynamicEnable":true,"dynamicType":"postdata","dynamicSource":"latest_item","dynamicPostData":"post_image"},"localId":"gsbp-img1234","styleAttributes":{"width":["100%"],"height":["200px"],"objectFit":["cover"]}} -->
<img class="gsbp-img1234" loading="lazy"/>
<!-- /wp:greenshift-blocks/element -->
```

**Example - Post Date:**
```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-dte1234","textContent":"<dynamictext>January 1, 2025</dynamictext>","tag":"span","dynamictext":{"dynamicEnable":true,"dynamicType":"postdata","dynamicSource":"latest_item","dynamicPostData":"post_date"},"localId":"gsbp-dte1234","styleAttributes":{"fontSize":["var(--wp--preset--font-size--xs, 0.85rem)"],"opacity":["0.7"]}} -->
<span class="gsbp-dte1234"><dynamictext>January 1, 2025</dynamictext></span>
<!-- /wp:greenshift-blocks/element -->
```

### 2. Author Data (`dynamicType: "authordata"`)

Available `dynamicAuthorData` values:

| Value | Description |
|-------|-------------|
| `display_name` | Author display name |
| `description` | Author bio |
| `user_email` | Author email |
| `user_url` | Author website |
| `user_avatar_url` | Avatar image URL |
| `user_registered` | Registration date |
| `ID` | Author ID |
| `meta` | Custom author meta (needs `dynamicAuthorField`) |

**Example - Author Name:**
```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-aut1234","textContent":"<dynamictext>Author Name</dynamictext>","dynamictext":{"dynamicEnable":true,"dynamicType":"authordata","dynamicSource":"latest_item","dynamicAuthorData":"display_name"},"localId":"gsbp-aut1234"} -->
<div class="gsbp-aut1234"><dynamictext>Author Name</dynamictext></div>
<!-- /wp:greenshift-blocks/element -->
```

### 3. Current User Data (`dynamicType: "user_data"`)

Same options as Author Data but for logged-in user.

### 4. Taxonomy Value (`dynamicType: "taxonomyvalue"`)

Display post categories, tags, or custom taxonomies:

```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-tax1234","textContent":"<dynamictext></dynamictext>","dynamictext":{"dynamicEnable":true,"dynamicType":"taxonomyvalue","dynamicSource":"latest_item","dynamicTaxonomyValue":"category","dynamicTaxonomyLink":true,"dynamicTaxonomyDivider":", "},"localId":"gsbp-tax1234","styleAttributes":{"fontSize":["var(--wp--preset--font-size--xs, 0.85rem)"]}} -->
<div class="gsbp-tax1234"><dynamictext></dynamictext></div>
<!-- /wp:greenshift-blocks/element -->
```

Parameters:
- `dynamicTaxonomyValue`: Taxonomy name (`category`, `post_tag`, custom)
- `dynamicTaxonomyLink`: Show as links (true/false)
- `dynamicTaxonomyDivider`: Separator between terms

### 5. Custom Meta Field (`dynamicType: "custom"`)

```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-meta123","textContent":"<dynamictext></dynamictext>","dynamictext":{"dynamicEnable":true,"dynamicType":"custom","dynamicSource":"latest_item","dynamicField":"my_custom_field"},"localId":"gsbp-meta123"} -->
<div class="gsbp-meta123"><dynamictext></dynamictext></div>
<!-- /wp:greenshift-blocks/element -->
```

### 6. Site Data (`dynamicType: "sitedata"`)

Available `dynamicSiteData` values:

| Value | Description |
|-------|-------------|
| `name` | Site name |
| `description` | Site description |
| `year` | Current year |
| `month` | Current month |
| `today` | Today's date |
| `todayplus1` | Tomorrow |
| `todayplus7` | 1 week from now |
| `querystring` | URL query parameter |
| `siteoption` | WordPress option |
| `acfsiteoption` | ACF site option |
| `transient` | WordPress transient |

**Example - Current Year:**
```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-year123","textContent":"<dynamictext>2025</dynamictext>","dynamictext":{"dynamicEnable":true,"dynamicType":"sitedata","dynamicSiteData":"year"},"localId":"gsbp-year123"} -->
<div class="gsbp-year123"><dynamictext>2025</dynamictext></div>
<!-- /wp:greenshift-blocks/element -->
```

## Dynamic Links

Use `dynamiclink` for href attributes on links and src on images:

```html
<!-- wp:greenshift-blocks/element {"id":"gsbp-lnk1234","tag":"a","type":"inner","dynamiclink":{"dynamicEnable":true,"dynamicType":"postdata","dynamicSource":"latest_item","dynamicPostData":"permalink"},"localId":"gsbp-lnk1234","styleAttributes":{"textDecoration":["none"]}} -->
<a class="gsbp-lnk1234">
<!-- Inner content -->
</a>
<!-- /wp:greenshift-blocks/element -->
```

## Dynamic Placeholders

Use in query arguments or text content:

### Basic Placeholders

| Placeholder | Description |
|------------|-------------|
| `{{POST_ID}}` | Current post ID |
| `{{POST_TITLE}}` | Current post title |
| `{{POST_URL}}` | Current post URL |
| `{{AUTHOR_ID}}` | Post author ID |
| `{{AUTHOR_NAME}}` | Post author name |
| `{{CURRENT_USER_ID}}` | Logged-in user ID |
| `{{CURRENT_USER_NAME}}` | Logged-in user name |
| `{{CURRENT_DATE_YMD}}` | Current date (YYYY-MM-DD) |
| `{{SITE_URL}}` | Site URL |

### Advanced Placeholders

| Placeholder | Description |
|------------|-------------|
| `{{GET:param_name}}` | URL GET parameter |
| `{{META:meta_key}}` | Post meta value |
| `{{TERM_META:meta_key}}` | Term meta value |
| `{{TERM_LINKS:taxonomy}}` | Linked terms |
| `{{USER_META:meta_key}}` | User meta value |
| `{{COOKIE:cookie_name}}` | Cookie value |
| `{{SETTING:option_name}}` | WordPress option |
| `{{RANDOM:0-100}}` | Random number |
| `{{RANDOM:red\|blue\|green}}` | Random selection |
| `{{TIMESTRING:today+10days}}` | Date calculation |

## Data Formatting (postprocessor)

Format returned data with `postprocessor`:

| Value | Description |
|-------|-------------|
| `textformat` | WYSIWYG formatting |
| `mailto` | Email link |
| `tel` | Phone link |
| `postlink` | Post link |
| `idtofile` | ID to file link |
| `idtoimageurl` | ID to image URL |
| `ymd` | YYYYMMDD to WP date |
| `unixtowp` | Unix to WP date |
| `datecustom` | Custom date format |
| `numberformat` | Number formatting |

**Example with postprocessor:**
```json
{
  "dynamictext": {
    "dynamicEnable": true,
    "dynamicType": "custom",
    "dynamicField": "phone_number",
    "postprocessor": "tel"
  }
}
```

## Complete Query Grid Example

Blog post grid with image, category, title, excerpt, and date:

```html
<!-- wp:greenshift-blocks/querygrid {"id":"gsbp-blog123","data_source":"query","query_filters":{"post_type":"post","posts_per_page":6},"styleAttributesWrapper":{"display":["flex"],"columnGap":["var(--wp--preset--spacing--50, 1.5rem)"],"rowGap":["var(--wp--preset--spacing--50, 1.5rem)"],"flexWrap":["wrap"],"flexColumns_Extra":3,"flexWidths_Extra":{"desktop":{"name":"33/33/33","widths":[33.33,33.33,33.33]},"tablet":{"name":"50/50","widths":[50,50]},"mobile":{"name":"100","widths":[100]}}},"styleAttributesItem":{"backgroundColor":["#ffffff"],"borderRadius":["var(--wp--custom--border-radius--small, 10px)"],"overflow":["hidden"],"boxShadow":["var(--wp--preset--shadow--soft)"]}} -->

<!-- Featured Image with Link -->
<!-- wp:greenshift-blocks/element {"id":"gsbp-cardlnk","tag":"a","type":"inner","dynamiclink":{"dynamicEnable":true,"dynamicType":"postdata","dynamicSource":"latest_item","dynamicPostData":"permalink"},"localId":"gsbp-cardlnk"} -->
<a><!-- wp:greenshift-blocks/element {"id":"gsbp-cardimg","tag":"img","dynamiclink":{"dynamicEnable":true,"dynamicType":"postdata","dynamicSource":"latest_item","dynamicPostData":"post_image"},"localId":"gsbp-cardimg","styleAttributes":{"width":["100%"],"height":["180px"],"objectFit":["cover"]}} -->
<img class="gsbp-cardimg" loading="lazy"/>
<!-- /wp:greenshift-blocks/element --></a>
<!-- /wp:greenshift-blocks/element -->

<!-- Content Container -->
<!-- wp:greenshift-blocks/element {"id":"gsbp-cardcnt","type":"inner","localId":"gsbp-cardcnt","styleAttributes":{"padding":["var(--wp--preset--spacing--50, 1.5rem)"]}} -->
<div class="gsbp-cardcnt">

<!-- Category -->
<!-- wp:greenshift-blocks/element {"id":"gsbp-cardcat","textContent":"<dynamictext></dynamictext>","dynamictext":{"dynamicEnable":true,"dynamicType":"taxonomyvalue","dynamicSource":"latest_item","dynamicTaxonomyValue":"category","dynamicTaxonomyLink":true,"dynamicTaxonomyDivider":", "},"localId":"gsbp-cardcat","styleAttributes":{"fontSize":["var(--wp--preset--font-size--xs, 0.85rem)"],"marginBottom":["8px"],"opacity":["0.7"]}} -->
<div class="gsbp-cardcat"><dynamictext></dynamictext></div>
<!-- /wp:greenshift-blocks/element -->

<!-- Title with Link -->
<!-- wp:greenshift-blocks/element {"id":"gsbp-cardttl","tag":"a","type":"inner","dynamiclink":{"dynamicEnable":true,"dynamicType":"postdata","dynamicSource":"latest_item","dynamicPostData":"permalink"},"localId":"gsbp-cardttl","styleAttributes":{"textDecoration":["none"],"color":["inherit"],"display":["block"]}} -->
<a class="gsbp-cardttl"><!-- wp:greenshift-blocks/element {"id":"gsbp-ttltext","textContent":"<dynamictext>Post Title</dynamictext>","tag":"h3","dynamictext":{"dynamicEnable":true,"dynamicType":"postdata","dynamicSource":"latest_item","dynamicPostData":"post_title"},"localId":"gsbp-ttltext","styleAttributes":{"fontSize":["var(--wp--preset--font-size--r, 1.2rem)"],"fontWeight":["600"],"lineHeight":["1.4em"],"marginTop":["0px"],"marginBottom":["8px"]}} -->
<h3 class="gsbp-ttltext"><dynamictext>Post Title</dynamictext></h3>
<!-- /wp:greenshift-blocks/element --></a>
<!-- /wp:greenshift-blocks/element -->

<!-- Excerpt -->
<!-- wp:greenshift-blocks/element {"id":"gsbp-cardexc","textContent":"<dynamictext>Excerpt text...</dynamictext>","dynamictext":{"dynamicEnable":true,"dynamicType":"postdata","dynamicSource":"latest_item","dynamicPostData":"post_excerpt"},"localId":"gsbp-cardexc","styleAttributes":{"fontSize":["var(--wp--preset--font-size--s, 1rem)"],"lineHeight":["1.5em"],"marginBottom":["12px"],"opacity":["0.8"]}} -->
<div class="gsbp-cardexc"><dynamictext>Excerpt text...</dynamictext></div>
<!-- /wp:greenshift-blocks/element -->

<!-- Date -->
<!-- wp:greenshift-blocks/element {"id":"gsbp-carddte","textContent":"<dynamictext>January 1, 2025</dynamictext>","tag":"span","dynamictext":{"dynamicEnable":true,"dynamicType":"postdata","dynamicSource":"latest_item","dynamicPostData":"post_date"},"localId":"gsbp-carddte","styleAttributes":{"fontSize":["var(--wp--preset--font-size--xs, 0.85rem)"],"opacity":["0.5"]}} -->
<span class="gsbp-carddte"><dynamictext>January 1, 2025</dynamictext></span>
<!-- /wp:greenshift-blocks/element -->

</div>
<!-- /wp:greenshift-blocks/element -->

<!-- /wp:greenshift-blocks/querygrid -->
```

## Source Options

- `dynamicSource: "latest_item"` - Use within query loops
- `dynamicSource: "definite_item"` - Specific post by ID
  - Requires `dynamicPostId` with the post ID

## Additional Parameters

- `fallbackValue`: Default text when no data found
- `avatarSize`: Size for user avatars (pixels)
- `dynamicPostImageSize`: Image size name (`thumbnail`, `medium`, `large`, `full`)
- `dateformat`: Custom PHP date format string
