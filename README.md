# Component library for Common Design

These components are also included in the common_design base theme [https://github.com/UN-OCHA/common_design/pull/110](v2) and some have a Drupal twig equivalent. If so, the component is visible on [the Feature site](https://feature.commondesign-unocha-org.ahconu.org/demo#cd-component-toc), with the exception of some utility components which are used in other components.

Updating the components is a manual process so changes made to components in this repo need to be copy and pasted to the common_design repo in order to be included in the base theme. We endeavour to keep the two component directories synced as closely as possible. If in doubt, ask in the Common Design Flowdock channel for the current status of a specific component.

---

# What makes a component?

## Criteria
- Each component should have a clear purpose and a name to reflect.
- Each component should be defined by purpose, not visual style. *This may be difficult sometimes. Discuss with team members.
- The component name should start with `cd-`.
- Each component should be in its own folder.
- Each component should include a README.md and guidelines for use.
- If a similar component already exists, discuss as a team whether to modify and extend, or create a new component.

### HTML
- Each component should include an html file with example markup and dummy text, to best demonstrate its use and variants.
- If there are multiple variants, each should be displayed for illustration purposes. Use `<hr>` to separate if needed.
- The components CSS and JS files should be included. For CSS, the component's CSS is usually placed last.
- Each component should link to the `cd-base.css` which has the CSS custom properties and other generic rules.
This is found in the [common_design_system repo](https://github.com/UN-OCHA/common_design_system/blob/master/cd-base.css)
- Any dependency components' CSS or JS should be linked to.

Eg. For cd-alert component
```
<link rel=stylesheet href="../cd-base.css" type="text/css" media=screen>
<link rel=stylesheet href="../cd-flow/cd-flow.css" type="text/css" media=screen>
<link rel=stylesheet href="../cd-typography/cd-typography.css" type="text/css" media=screen>
<link rel=stylesheet href="cd-alert.css" type="text/css" media=screen>
```
- Markup should be simple and semantic.
- Use nested BEM naming for selectors.

Eg. BEM
```
<ul class="cd-title-list">
  <li class="cd-title-list__item">
    <a href="/#" class="cd-title-list__link">
      <span class="cd-title-list__title">Title</span>
      <svg class="cd-icon cd-icon--arrow-right" width="16" height="16" aria-hidden="true" focusable="false">
        <use xlink:href="#cd-icon--arrow-right"></use>
      </svg>
    </a>
  </li>
   ...
```
- If the component requires a "page" layout for composition, add the standard layout divs from the base theme.
The layout styles are included in cd-base.css.

Eg. Layout markup
```
<div class="cd-layout-container">
  <main role="main" id="main-content" class="cd-container">
    <div class="cd-layout-content">
```

### CSS
- A component will likely have its own CSS stylesheet. Some components might be CSS only.
- There should be no hexidecimal colour values. We should use CSS custom properties for colour management.
- If variants exist, multiple stylesheets can be used to distinguish and organise.
- Variants should build on existing "base" rules. If that is not possible, it is likely not a good candidate for a variant.

Eg. For cd-hero component
```
{{ attach_library('common_design/cd-hero') }}
{{ attach_library('common_design/cd-hero--style-one') }}
```
- Each component should be tested and have applicable cross-browser and device fixes where required.
- Adopt a mobile-first approach by starting with generic rules and adding media queries with min-width values down the cascade.

### JS
- Each component should be tested and have applicable cross-browser and device fixes or polyfills where required.
- Adopt a content-first approach by ensuring all content is accessible and the site remains usable when JS is disabled.
*There may be exceptions.
- Add code comments to explain intent where relevant.

```
