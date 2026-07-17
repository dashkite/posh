# Reference

This document details the public API and exported modules provided by the Posh library. 

## Understanding Posh Modules

Posh delivers a comprehensive set of baseline CSS rules. Developers can interact with Posh either by importing the exported JavaScript properties—which return the CSS as raw strings—or by including the underlying Stylus files directly into a stylesheet. These modules are meticulously layered and rely on CSS custom properties to ensure highly composable, dynamic styling without specificity wars.

## Exported Modules

The Posh package exports various modules, providing granular access to different facets of the styling ruleset.

### reset

$reset \to stylesheet$

To strip away inconsistent browser defaults and establish a level playing field, you can use the reset property. It yields a foundational CSS reset stylesheet as a raw string, ensuring subsequent application styles behave predictably across environments.

<example>
This illustrates importing the reset module directly to inject base styles.
```coffeescript
import { reset } from "@dashkite/posh"

document.head.innerHTML += "<style>#{reset}</style>"
```
</example>

### normalize

$normalize \to stylesheet$

For minor but critical CSS normalizations, the normalize property supplies rules to handle anchor link resets and list indentations. This ensures that fundamental semantic HTML elements render elegantly and predictably.

<example>
This illustrates including the normalize module alongside a reset.
```coffeescript
import { normalize } from "@dashkite/posh"
```
</example>

### typography

$typography \to stylesheet$

The typography property gives you access to the base typography definitions. By establishing scale variables for headings and text across the application, it dynamically calculates font sizes and spacing to create a pleasing, emergent visual rhythm.

<example>
This illustrates configuring the typography scale using custom properties after importing the typography module.
```stylus
@import "@dashkite/posh/typography"

:root
  --base-font "Inter", sans-serif
  --first-level-heading-font-size 3rem
```
</example>

### color

$color \to stylesheet$

Whenever you need to set up the core color variables, the color property provides the necessary tokens. It establishes the primary, secondary, and tertiary foreground and background values, natively supporting both light and dark color schemes via media queries.

<example>
This illustrates overriding the primary color tokens for a custom theme.
```stylus
@import "@dashkite/posh/color"

:root
  --light-primary-background #ffffff
  --light-primary-foreground #111111
```
</example>

### forms

$forms \to stylesheet$

To deliver consistent styling for interactive controls, the forms property normalizes inputs, textareas, and buttons. This ensures that user interaction elements feel cohesive and respond logically to state changes like focus and validation errors.

<example>
This illustrates applying the forms module within a UI framework.
```coffeescript
import { forms } from "@dashkite/posh"
```
</example>

### component

$component \to stylesheet$

The component property provides generic utility styles targeting common component structures. By supplying a baseline layout rhythm for generic UI components, it abstracts away repetitive structural boilerplate so creators can focus on logic.

<example>
This illustrates importing the component styles to establish a structural baseline.
```coffeescript
import { component } from "@dashkite/posh"
```
</example>

### animations

$animations \to stylesheet$

When an application requires standardized micro-interactions, the animations property yields a set of predefined CSS keyframes and transition definitions. Applying these smooth, standard animations significantly enhances the overall human experience.

<example>
This illustrates incorporating standard animations into the styling layer.
```coffeescript
import { animations } from "@dashkite/posh"
```
</example>

### icons

$icons \to url$

Unlike the other CSS string exports, the icons property returns the URL string for the Remix Icon stylesheet CDN. This offers a straightforward way to embed a robust, open-source icon set without manually hosting the font assets.

<example>
This illustrates dynamically injecting the icon stylesheet into the document head.
```coffeescript
import { icons } from "@dashkite/posh"

link = document.createElement "link"
link.rel = "stylesheet"
link.href = icons
document.head.appendChild link
```
</example>

### compact

$compact \to stylesheet$

For tight UI layouts requiring density adjustments, the compact property modifies spatial relationships and quarter-rem spacing. It creates a denser layout rhythm that is ideal for complex dashboards or data-heavy views.

<example>
This illustrates importing the compact styles for dense interfaces.
```coffeescript
import { compact } from "@dashkite/posh"
```
</example>

### hints

$hints \to stylesheet$

The hints property exposes the layout hint classes. By enabling semantically-inspired utility classes like `.layout.horizontal` or `.layout.narrow`, it allows developers to control alignment, flex orientations, and structural constraints directly from the markup.

<example>
This illustrates applying structural hints to a container.
```html
<div class="layout horizontal justify-center">
  <!-- Content -->
</div>
```
</example>

### application

$application \to stylesheet$

When you need a complete foundation, the application property aggregates the core modules into a single base application stylesheet. It meticulously combines the reset, normalize, color, typography, layout, and navigation modules into a cleanly layered structure, serving as the perfect starting point for new projects.

<example>
This illustrates pulling in the entire foundation at once.
```coffeescript
import { application } from "@dashkite/posh"
```
</example>
