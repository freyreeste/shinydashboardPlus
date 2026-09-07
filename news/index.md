# Changelog

## shinydashboardPlus 2.0.6

CRAN release: 2025-08-25

- Fix NOTES in CRAN checks.

## shinydashboardPlus 2.0.5

CRAN release: 2024-08-18

- Add shinylive to support the different demo apps.

### Minor change

- Fix NOTE in CRAN checks.

## shinydashboardPlus 2.0.4

CRAN release: 2024-04-09

### Minor change

- Fix
  [\#181](https://github.com/RinteRface/shinydashboardPlus/issues/181).
- Update github actions.
- Icon
  [change](https://github.com/RinteRface/shinydashboardPlus/commit/0abe127a1ce0e7f8cb74883968c83b796cc9c73e)
  in [`dashboardHeader()`](../reference/dashboardHeader.md). Thanks
  [@zhanxw](https://github.com/zhanxw).
- Allow
  [hyperlink](https://github.com/RinteRface/shinydashboardPlus/commit/12fab3b92b2b5e459304b385e7ed7a94cb9dbd98)
  in User block. Thanks [@robertkck](https://github.com/robertkck).
- Fix multiple fontawesome icon issues (deprecated names in fontawesome
  6).

## shinydashboardPlus 2.0.3

CRAN release: 2021-09-15

This release is a patch to fix an
[issue](https://github.com/RinteRface/shinydashboardPlus/pull/151)
preventing the release of Shiny 1.7.0. Thanks
[@wch](https://github.com/wch).

### Minor change

- Internal change regarding the [waiter](https://waiter.john-coene.com/)
  package but no user impact. Thanks
  [@JohnCoene](https://github.com/JohnCoene).

### Bug fix

- Fix
  [\#150](https://github.com/RinteRface/shinydashboardPlus/issues/150):
  Warning when using controlbarMenu.

## shinydashboardPlus 2.0.2

CRAN release: 2021-07-16

- Simple patch to fix wrong .Rbuildignore
  [rule](https://github.com/DivadNojnarg/outstanding-shiny-ui/issues/52).
- Update internal file structure.
- Clean NOTE:
  <https://CRAN.R-project.org//web/checks/check_results_shinydashboardPlus.html>

## shinydashboardPlus 2.0.1

CRAN release: 2021-04-26

This release is a patch without major changes.

### Minor change

- Fix
  [\#132](https://github.com/RinteRface/shinydashboardPlus/issues/132):
  Option to disable the “scroll to top” button in
  [`dashboardPage()`](../reference/dashboardPage.md)

### Bug fix

- Fix
  [\#127](https://github.com/RinteRface/shinydashboardPlus/issues/127):
  [`shiny::navlistPanel()`](https://rdrr.io/pkg/shiny/man/navlistPanel.html)
  in [`dashboardControlbar()`](../reference/controlbar.md) not behaving
  as expected.
- Fix
  [\#112](https://github.com/RinteRface/shinydashboardPlus/issues/112):
  [`userBox()`](../reference/userBox.md) is not working. Introduced in
  2.0.0.

## shinydashboardPlus 2.0.0

CRAN release: 2021-03-07

This release is a major step for shinydashboardPlus. It is also a
significant breaking change compared to the latest CRAN version. Overall
this release will simplify the transition from shinydashboard to
shinydashboardPlus and bring more consistency, more interactivity
between components. Below is the changelog.

### Breaking changes

- Change *maxstar* and *grade* in
  [`starBlock()`](../reference/starBlock.md) to `max` and `value`.
- Remove *footerPadding* from `boxPlus()` to align with
  [bs4Dash](https://github.com/RinteRface/bs4Dash)
- Remove all sidebar related parameters from `boxPlus()`. This is now
  part of the new `boxPlusSidebar()`
- remove *dropdownIcon* parameter from `boxPlus()`. It is now part of
  the `dropdownItemList()`
- Remove all label params from `boxPlus()`. This is to reduce the number
  of parameters of cards. Now part of `boxPlusLabel()`
- In `dropdownItemList()` *icon* must be provided as
  [`shiny::icon()`](https://rdrr.io/pkg/shiny/man/icon.html) and not a
  simple string containing the icon name. This is to be consistent with
  {shinydashboard}
- Replace *left_text* and *right_text* by *left* and *right*,
  respectively in [`dashboardFooter()`](../reference/dashboardFooter.md)
- Remove all sidebar related parameters of `dashboardPagePlus()`. They
  now belong to `dashboardSidebarPlus()` to Align with {shinydashboard}
- In `dashboardSidebarPlus()`: replace *rightSidebar* by *controlbar*
  (align with {bs4Dash}). Rename *enable_preloader* to *preloader* and
  *loading_duration* to *duration*
- Rename `rightSidebar()` to
  [`dashboardControlbar()`](../reference/controlbar.md) to align with
  {bs4Dash}
- Remove *enable_rightSidebar* from `dashboardHeaderPlus()`. This is now
  part of [`dashboardControlbar()`](../reference/controlbar.md) as
  *disable* like in {shinydashboard}. *rightSidebarIcon* becomes
  *controlbarIcon* that accepts
  [`shiny::icon`](https://rdrr.io/pkg/shiny/man/icon.html) instead of a
  simple string containing the icon name to be consistent with
  {shinydashboard}. *left_menu* becomes *leftUi* like in {bs4Dash}
- Remove `rightSiderbarMenu()`, `rightSidebarTablist()`,
  `rightSidebarTabItem()`, `rightSidebarPanel()` and
  `rightSidebarTabContent()`. They are now replaces by
  [`dashboardControlbar()`](../reference/controlbar.md),
  [`controlbarMenu()`](../reference/controlbar.md) and
  [`controlbarItem()`](../reference/controlbar.md)
- Remove `rightSidebarMenuItem()`, `menuIcon()` and `menuInfo()`
- Rename `boxPlus()` to [`box()`](../reference/box.md),
  `dashboardPagePlus()` to
  [`dashboardPage()`](../reference/dashboardPage.md) and
  `dashboardHeaderPlus()` to
  [`dashboardHeader()`](../reference/dashboardHeader.md)
- [`dropdownBlock()`](../reference/dropdownBlock.md) *icon* expects a
  [`shiny::icon()`](https://rdrr.io/pkg/shiny/man/icon.html) and not a
  simple string containing the icon name. This is to be consistent with
  {shinydashboard}
- In `gradientBox()` *icon* expects a
  [`shiny::icon()`](https://rdrr.io/pkg/shiny/man/icon.html) and not a
  simple string containing the icon name. This is to be consistent with
  {shinydashboard}
- In [`descriptionBlock()`](../reference/box.md) *icon* expects a
  [`shiny::icon()`](https://rdrr.io/pkg/shiny/man/icon.html) and not a
  simple string containing the icon name. This is to be consistent with
  {shinydashboard}
- Rework [`navPillsItem()`](../reference/navPills.md): *pillName*
  becomes *left*, *pillText* becomes *right*, *pillColor* becomes
  *color*, *pillIcon* becomes *icon* and expects a
  [`shiny::icon()`](https://rdrr.io/pkg/shiny/man/icon.html). Add
  *inputId* so that the item behaves like an action button
- Rework [`productListItem()`](../reference/productList.md):
  *productTitle* becomes *title*, *productPrice* becomes *subtitle*,
  *priceColor* becomes *color*
- In [`timelineItem()`](../reference/timeline.md),
  [`timelineStart()`](../reference/timeline.md) and
  [`timelineEnd()`](../reference/timeline.md), *icon* expects a
  [`shiny::icon()`](https://rdrr.io/pkg/shiny/man/icon.html) and not a
  simple string containing the icon name. This is to be consistent with
  {shinydashboard}
- In [`userListItem()`](../reference/userList.md), *user_name* becomes
  *title*, *description* becomes *subtitle*
- `dropdownItemList()` becomes [`boxDropdown()`](../reference/box.md).
  `dropdownItem()` becomes [`boxDropdownItem()`](../reference/box.md)
- `userPostToolItemList()` becomes
  [`userPostTagItems()`](../reference/userPost.md). `userPostToolItem()`
  becomes [`userPostTagItem()`](../reference/userPost.md)
- Remove `boxProfileItemList()`.
  [`boxProfile()`](../reference/boxProfile.md) gets a new parameter
  *bordered*, inherited from the old `boxProfileItemList()`
- In [`boxProfile()`](../reference/boxProfile.md), *title* becomes
  mandatory
- *title* and *description* mandatory in
  [`boxProfileItem()`](../reference/boxProfile.md)
- In [`boxComment()`](../reference/socialBox.md): *src* and *title* are
  mandatory
- `widgetUserBox()` becomes [`userBox()`](../reference/userBox.md) for
  more naming consistency
- Remove `gradientBox()` for consistency with {bs4Dash}
- Add *icon*, *gradient* and *boxToolSize* to
  [`box()`](../reference/box.md)
- *title* mandatory in [`userBox()`](../reference/userBox.md). Remove
  *background*. Replace *backgroundUrl* by *backgroundImage*. Reworked
  *type* parameter
- Restore [`accordion()`](../reference/accordion.md) id. We should
  distinguish between TRUE inputs (sliderInput) and secondary inputs
  (that you can use for interactivity)…
- *color* becomes *status* in
  [`accordionItem()`](../reference/accordion.md). This is to be
  consistent with AdminLTE2 classes and {shinydashboard}
- In [`attachmentBlock()`](../reference/attachmentBlock.md): *src*
  becomes *image* and *titleUrl* becomes *href*. *image* is mandatory
- In [`socialButton()`](../reference/socialButton.md): *url* becomes
  *href* and *type* becomes *icon* (expect
  [`shiny::icon`](https://rdrr.io/pkg/shiny/man/icon.html))
- In [`productListItem()`](../reference/productList.md): *src* becomes
  *image* to be consistent with {shinydashboard}
- In [`timelineItemMedia()`](../reference/timeline.md): *src* becomes
  *image* to be consistent with {shinydashboard}
- In [`userListItem()`](../reference/userList.md): *src* becomes *image*
  to be consistent with {shinydashboard}
- In [`userPost()`](../reference/userPost.md): *src* becomes *image* to
  be consistent with {shinydashboard}. *image* and *author* are
  mandatory
- In [`userPostMedia()`](../reference/userPost.md): *src* becomes
  *image* to be consistent with {shinydashboard}. *image* is mandatory
- Reworked `verticalProgress()` to
  [`progressBar()`](../reference/progressBar.md)
- In [`userMessage()`](../reference/userMessage.md): *src* becomes
  *image* to be consistent with {shinydashboard}. *side* becomes *type*
  (semantic)
- In [`dashboardUser()`](../reference/dashboardUser.md): *src* becomes
  *image* to be consistent with {shinydashboard}
- In [`userBox()`](../reference/userBox.md): *src* becomes *image* to be
  consistent with {shinydashboard}
- In [`socialBox()`](../reference/socialBox.md): *src* becomes *image*
  to be consistent with {shinydashboard}
- In [`boxComment()`](../reference/socialBox.md): *src* becomes *image*
  to be consistent with {shinydashboard}
- In [`boxProfile()`](../reference/boxProfile.md): *src* becomes *image*
  to be consistent with {shinydashboard}
- In [`boxDropdownItem()`](../reference/box.md): *url* becomes *href* to
  be consistent with {shinydashboard}. *name* is removed
- Rework preloader feature: remove *duration* and *preloader* now
  expects a list…
- In [`navPillsItem()`](../reference/navPills.md): *active* becomes
  *selected*

### New features

- Completely redesigned pkgdown website with much better documentation
- New [`updateUserMessages()`](../reference/userMessage.md) function
- New [`updateAccordion()`](../reference/accordion.md) to toggle
  [`accordion()`](../reference/accordion.md) on the client
- Automatic “scroll to top” feature to quickly go to the top of the
  dashboard
- Use [waiter](https://waiter.john-coene.com/) for custom preloaders
- Add *inputId* to [`taskItem()`](../reference/taskItem.md),
  [`notificationItem()`](../reference/notificationItem.md) and
  [`messageItem()`](../reference/messageItem.md)
- New *id* and *icon* to [`boxDropdownItem()`](../reference/box.md),
  that behaves like an action button if passed
- New [`updateNavPills()`](../reference/navPills.md) to programmatically
  change the selected item in [`navPills()`](../reference/navPills.md)
- Add *freshTheme* parameter to
  [`dashboardPage()`](../reference/dashboardPage.md). This allows to use
  the awsesome [fresh](https://github.com/dreamRs/fresh) package. See
  [here](https://dreamrs.github.io/fresh/articles/vars-shinydashboard.html)
  for more details.
- Add [`skinSelector()`](../reference/skinSelector.md) to allow
  dynamically change the dashboard skin on the client side.
- Add [`updateControlbarMenu()`](../reference/controlbar.md) to
  programmatically change the selected controlbar item
- Add *id* to [`dashboardControlbar()`](../reference/controlbar.md) to
  be able to use [`updateControlbar()`](../reference/controlbar.md)
- Add *id* to [`dashboardSidebar()`](../reference/sidebar.md) to be able
  to use [`updateSidebar()`](../reference/sidebar.md)
- New [`dashboardSidebar()`](../reference/sidebar.md) (reworked
  shinydashboard sidebar)
- New [`boxLabel()`](../reference/boxLabel.md) to add text labels in
  [`box()`](../reference/box.md)
- New [`boxSidebar()`](../reference/boxSidebar.md): access the status
  via input\$id. Add [`updateBoxSidebar()`](../reference/boxSidebar.md)
  to toggle the box sidebar
- new `options` parameter to
  [`dashboardPage()`](../reference/dashboardPage.md). See
  [here](https://adminlte.io/themes/AdminLTE/documentation/index.html#adminlte-options)
  for the list of available options
- Toggle [`box()`](../reference/box.md) with
  [`updateBox()`](../reference/box.md) (see
  [\#10](https://github.com/RinteRface/shinydashboardPlus/issues/10) and
  [\#69](https://github.com/RinteRface/shinydashboardPlus/issues/69),
  [@happyshows](https://github.com/happyshows) and
  [@daatali](https://github.com/daatali))

### Minor change

- Add *headerBorder* to [`box()`](../reference/box.md)
- add *width* to [`accordion()`](../reference/accordion.md) (default to
  12)
- Simplified dependencies code (No end-user impact)

### Bug fixes

- Fix
  [\#102](https://github.com/RinteRface/shinydashboardPlus/issues/102):
  dashboardUser not displayed when using
  shinydashboard::sidebarMenuOutput. ensureActivatedTab was not in the
  global scope, whereas it was needed by the output binding code
- Fix
  [\#107](https://github.com/RinteRface/shinydashboardPlus/issues/107):
  `collapsed = FALSE` not working for dashboardControlbar.
- Fix
  [\#56](https://github.com/RinteRface/shinydashboardPlus/issues/56):
  When controlbar is expanded/collapsed, a plot does not fit in body.
- Fix
  [\#78](https://github.com/RinteRface/shinydashboardPlus/issues/78):
  Menu Item with Sub Menu Item Arrow Not Rotating.
- Fix
  [\#105](https://github.com/RinteRface/shinydashboardPlus/issues/105):
  box animation speed. Allow user defined options to prevail over
  internals.
- Fix
  [\#57](https://github.com/RinteRface/shinydashboardPlus/issues/57):
  broken default `input$sidebarCollapsed`.
- Fix
  [\#86](https://github.com/RinteRface/shinydashboardPlus/issues/86):
  controlbar should also trigger a window resize, like the left
  shinydashboard sidebar. Thanks
  [@ajfisher83](https://github.com/ajfisher83)
- Fix ugly layout of the box body (wrong padding and margins) when one
  puts a sidebar in [`box()`](../reference/box.md)…
- *title* is mandatory in [`accordionItem()`](../reference/accordion.md)
  (Setting title to NULL would prevent the item to be able to collapse
  …)

## shinydashboardPlus 0.7.5

CRAN release: 2020-07-15

### Experimental

- New dark theme: midnight (still work in progress, some elements are
  missing)

### Breaking Changes

- [`accordion()`](../reference/accordion.md) id becomes inputId.
  [`accordionItem()`](../reference/accordion.md) id parameter is removed
- rework [`appButton()`](../reference/appButton.md) : this is a classic
  shiny actionButton, with improved styling.
- change title_url in titleUrl in
  [`attachmentBlock()`](../reference/attachmentBlock.md) change
  number_color, number_icon, margin_bottom and rightBorder to camelcase
  params in [`descriptionBlock()`](../reference/box.md)
- numberIcon in [`descriptionBlock()`](../reference/box.md) only need
  the name of the icon (‘times’) instead of the full class (like fa
  fa-times)

### New features

- add [`userMessages()`](../reference/userMessage.md) and
  [`userMessage()`](../reference/userMessage.md)
- add [`dashboardBadge()`](../reference/dashboardBadge.md): use in
  elements like [`appButton()`](../reference/appButton.md). This is
  different from [`dashboardLabel()`](../reference/dashboardLabel.md)

### Minor Change

- Fix
  [\#52](https://github.com/RinteRface/shinydashboardPlus/issues/52):
  add collapsed arg to `widgetUserBox()`. Thanks
  [@terpsrule](https://github.com/terpsrule)
- Fix
  [\#40](https://github.com/RinteRface/shinydashboardPlus/issues/40):
  add sidebar_icon argument to `boxPlus()`. Thanks
  [@jmw86069](https://github.com/jmw86069) for the suggestion

### Bug Fixes

- Fix
  [\#61](https://github.com/RinteRface/shinydashboardPlus/issues/61):
  uniqueness of [`accordion()`](../reference/accordion.md) id. Thanks
  [@RegaCaska](https://github.com/RegaCaska)
- Fix
  [\#23](https://github.com/RinteRface/shinydashboardPlus/issues/23):
  rework id arg in [`flipBox()`](../reference/flipbox.md). Thanks
  [@vinpogo](https://github.com/vinpogo)
- Add class btn-box-tool to close button in `widgetUserBox()`. Prevent
  from ugly rendering
- Fix
  [\#51](https://github.com/RinteRface/shinydashboardPlus/issues/51):
  change card sidebar z-index so that it is not displayed on top of the
  page preloader. Thanks [@leungi](https://github.com/leungi)
- Fix
  [\#53](https://github.com/RinteRface/shinydashboardPlus/issues/53):
  missing title in demo message card
- Fix
  [\#55](https://github.com/RinteRface/shinydashboardPlus/issues/55):
  when no image is provided, no circle is displayed. Thanks
  [@nschwamm](https://github.com/nschwamm)
- Replace http links by https
- Fix
  [\#36](https://github.com/RinteRface/shinydashboardPlus/issues/36):
  make sure that a [`carousel()`](../reference/carousel.md) item is
  displayed when it is generated via a shiny Output function. Thanks
  [@daattali](https://github.com/daattali) for the report

## shinydashboardPlus 0.7.0

CRAN release: 2019-04-08

### Breaking Changes

- remove all CSS functions, namely
  [`setShadow()`](https://dreamrs.github.io/shinyWidgets/reference/deprecated.html),
  `setPulse()`, `setShake()` and `setZoom()`, since they are contained
  in [shinyEffects](https://github.com/RinteRface/shinyEffects)

### New features

- 6 new color statuses for `boxPlus()` headers: navy, teal, orange,
  maroon, black and purple
- add new argument .items to `rightSidebar()`: useful if we do not want
  to embed elements in tabs.
- add [`dashboardFooter()`](../reference/dashboardFooter.md)
- add [`dashboardUser()`](../reference/dashboardUser.md),
  [`dashboardUserItem()`](../reference/dashboardUserItem.md),
  [`renderUser()`](../reference/renderUser.md) and
  [`userOutput()`](../reference/userOutput.md)
- add [`carousel()`](../reference/carousel.md) and
  [`carouselItem()`](../reference/carousel.md)
- new argument to dashboardPagePlus: sidebar_fullCollapse enable the
  sidebar to be fully collapsed as in shinydashboard. Fix
  [\#24](https://github.com/RinteRface/shinydashboardPlus/issues/24),
  thanks [@serkserk](https://github.com/serkserk)
- by default, opening the right sidebar shifts the body content to the
  left, similarly as the left sidebar

### major changes

- shindashboardPlus is now moved on
  [RinteRface](https://github.com/RinteRface/shinydashboardPlus)

### Minor changes

- new hex icons
- update gallery
- update vignettes (RinteRface)

### Fixes

- fix issue when the `dashboardHeaderPlus()` title was NULL
- fix [\#22](https://github.com/RinteRface/shinydashboardPlus/issues/22)
  thanks to [@trallard](https://github.com/trallard) (missing licence)

## shinydashboardPlus 0.6.0

CRAN release: 2018-09-20

### New features

- add new [`flipBox()`](../reference/flipbox.md)
- new sidebar in the `boxPlus()` function: set up with the following
  arguments “enable_sidebar”, “sidebar_content”, “sidebar_width”,
  “sidebar_background” and “sidebar_start_open”
- new “left_menu” argument in the `dashboardHeaderPlus()` to include
  elements in the left part of the navbar. (In addition to what you can
  already do in the right part with shinydashboard)
- new [`dropdownBlock()`](../reference/dropdownBlock.md) to include
  shiny input elements in a navbar left menu (optimized for all screen
  sizes)
- new “fixed” argument to the navbar (`dashboardHeaderPlus()`). If TRUE,
  the navbar is fixed-top. (static-top by default)
- new `setZoom()` function (similar as
  [`setShadow()`](https://dreamrs.github.io/shinyWidgets/reference/deprecated.html))
- new `setPulse()` function
- new `setShake()` function
- add “enable_preloader” and “loading_duration” to `dashboardPagePlus()`
  (custom preloader)
- update the
  [`shinydashboardPlusGallery()`](../reference/shinydashboardPlusGallery.md)
- add a “style” argument to
  [`dashboardLabel()`](../reference/dashboardLabel.md)
- change the website images
- add “collapsed argument” to [`userPost()`](../reference/userPost.md)
  to show or hide comments when the application starts.

### Bug fixes

- now [`appButton()`](../reference/appButton.md) open a new window when
  clicked
- now [`socialButton()`](../reference/socialButton.md) open a new window
  when clicked
- do not show comments when there are no comments in
  [`socialBox()`](../reference/socialBox.md)
- do not show the footer when it is NULL in
  [`socialBox()`](../reference/socialBox.md)
- add style overflow-y auto to
  [`socialBox()`](../reference/socialBox.md) in case there are more than
  2 comments (avoid “infinite” height boxes)
- on mobiles (or small screens), navbar left menu items display inline,
  instead of column…
- disable [`timelineItem()`](../reference/timeline.md) footer when NULL
- center images in [`userPostMedia()`](../reference/userPost.md)
- fix [\#8](https://github.com/RinteRface/shinydashboardPlus/issues/8)
  thanks to [@scottyraymond](https://github.com/scottyraymond)
  ([`dropdownBlock()`](../reference/dropdownBlock.md) icon not
  displaying)

## shinydashboardPlus 0.5.0

CRAN release: 2018-07-05

### Bug fixes

- Fix an important issue in the `rightSidebar()`. When the function was
  called without any element, it triggered an error because the number
  of items was 0
- clicking on [`starBlock()`](../reference/starBlock.md),
  [`navPillsItem()`](../reference/navPills.md) and the `socialBlock()`
  title does not reload or redirect at the top of the page
- clicking on the [`attachmentBlock()`](../reference/attachmentBlock.md)
  link open a new page in a new tab (target = “\_blank”)
- correct vignettes title
  (<https://cran.r-project.org/package=shinydashboardPlus>)

### Breaking changes

- change argument name in `dropdownItem()` (`boxPlus()`): “target” is
  replaced by “url”.
- Widely simplify the `rightSidebar()` function: remove
  `rightSidebarTabList()`, `rightSidebarTabItem()` and
  `rightSidebarPanel()` from the user interface. See
  [here](https://shinydashboardplus.rinterface.com/articles/controlbar#controlbar)
  to discover how to set up a new `rightSidebar()`

### Major changes

- add a “width” argument to the `rightSidebar()` (set to 230 pixels by
  default) to improve customization.
- new function
  [`setShadow()`](https://dreamrs.github.io/shinyWidgets/reference/deprecated.html)
  to set shadow and hover effects on any elements
- add an “active” argument to `rightSidebarTabContent()`: see
  [\#4](https://github.com/RinteRface/shinydashboardPlus/issues/4)
- add a “sidebar_background” argument to `dashboardPagePlus()`
- new `verticalProgress()` bars!
- new functions in the `rightSidebar()`: `rightSidebarMenu()`,
  `rightSidebarMenuItem()`, `menuIcon()` and `menuInfo()` (see
  [`shinydashboardPlusGallery()`](../reference/shinydashboardPlusGallery.md))
- new dropdown menu for `boxPlus()`: add `dropdownItemList()`,
  `dropdownItem()` and [`dropdownDivider()`](../reference/box.md)
  functions (see
  [`shinydashboardPlusGallery()`](../reference/shinydashboardPlusGallery.md))
- add “width” and “height” args to
  [`timelineItemMedia()`](../reference/timeline.md) and
  [`userPostMedia()`](../reference/userPost.md)
- remove useless content

### New Side content

- add a pkgdown website
- add cran downloads to readme

## shinydashboardPlus 0.2.0

CRAN release: 2018-05-08

- new timelines: `timeLineBlock()` either inside or outside a box
- new userPost function: `userPostToolItemList()`, `userPostToolItem()`,
  [`userPostMedia()`](../reference/userPost.md), `userPostToolItem()`
- new boxProfile function: `boxProfileItemList()`,
  [`boxProfileItem()`](../reference/boxProfile.md)
- update
  [`shinydashboardPlusGallery()`](../reference/shinydashboardPlusGallery.md)
- add
  [`shinydashboardPlusGallery()`](../reference/shinydashboardPlusGallery.md)
- update all examples
- some minor fixes
- NOTE: mailForm is not working at the moment!

## shinydashboardPlus 0.1.0

- new right sidebar: `rightSidebar()`
- improved classic boxes: `boxPlus()`
- new boxes: `gradientBox()`, `widgetUserBox()`,
  [`socialBox()`](../reference/socialBox.md)
- new box elements: [`boxPad()`](../reference/box.md),
  [`attachmentBlock()`](../reference/attachmentBlock.md),
  [`descriptionBlock()`](../reference/box.md),
  [`productList()`](../reference/productList.md),
  [`navPills()`](../reference/navPills.md),
  [`todoList()`](../reference/todoList.md),
  [`userList()`](../reference/userList.md),
  [`boxComment()`](../reference/socialBox.md)
- new buttons: [`appButton()`](../reference/appButton.md) and
  [`socialButton()`](../reference/socialButton.md) (NOTE: these are not
  inputButtons!)
- additional elements: [`starBlock()`](../reference/starBlock.md),
  [`loadingState()`](../reference/loadingState.md),
  [`blockQuote()`](../reference/blockQuote.md),
  [`dashboardLabel()`](../reference/dashboardLabel.md)
- switch between shinydashboard and shinydashboardPlus:
  `dashboardHeaderPlus()`, `dashboardPagePlus()`
