# Recipes

This document provides usage guides and recipes for implementing application styles with Posh. The examples advance from establishing basic global foundations to integrating styles within encapsulated web components.

## How to establish a baseline design foundation?

A creator typically begins a project by establishing a consistent, cross-browser starting point for the application's visual language. Posh enables this task by bundling its most common requirements—such as resets, normalizations, typography, and color—into a single `application` module. Alternatively, developers can compose individual modules directly within a Stylus pipeline.

To establish this foundation, follow these steps:
1. Identify the main entry point for your application's global styles.
2. Import the `application` module to normalize browser defaults and establish the layered architecture.
3. Assign the core foreground and background variables to the document body.

```stylus
@import "@dashkite/posh/application"

body
  background var(--background)
  color var(--foreground)
```

## How to rapidly prototype structural layouts?

When building complex user interfaces, writing bespoke CSS for every new container significantly slows down development. Posh solves this by providing the `hints` and `component` modules, which offer a set of semantically-inspired utility classes. These classes hook into the underlying custom properties to rapidly apply consistent flexbox behaviors and spacing rhythms.

To structure a new layout, follow these steps:
1. Determine the directional flow of your content (horizontal or vertical).
2. Wrap the content elements in a container using the `layout` class alongside the directional hint.
3. Apply alignment hints to manage spatial relationships within the container.

```html
<!-- We use standard HTML structures with specific Posh utility classes -->
<div class="layout horizontal justify-between align-center">
  <div class="layout vertical narrower">
    <p>Flexible alignment and constraints are built in.</p>
  </div>
</div>
```

## How to manage dynamic color and typography themes?

Applications frequently require runtime adaptability to handle user preferences, such as switching between light and dark modes or scaling text for accessibility. Because Posh is built entirely on CSS custom properties, it enables this adaptability without requiring stylesheet recompilation. The `color` and `typography` modules define a rich vocabulary of design tokens that the browser evaluates dynamically.

To configure a custom theme, follow these steps:
1. Select the `:root` selector or a specific high-level container to scope your theme.
2. Override the default Posh variables with your specific design tokens.
3. Rely on native media queries or class toggles to redefine those variables on the fly.

```stylus
@import "@dashkite/posh/typography"
@import "@dashkite/posh/color"

:root
  --base-font "Inter", sans-serif
  --first-level-heading-font-size 2.5rem
  
  --light-primary-background #ffffff
  --light-primary-foreground #111111
  
  --dark-primary-background #111111
  --dark-primary-foreground #eeeeee
```

## How to inject styling into a Wayland component?

Modern web architecture often relies on encapsulated web components, which isolate their internal DOM and styles from the rest of the application. Developers need a way to pass global design tokens and baseline structures into this isolated boundary. Posh enables this integration effortlessly by exporting its stylesheets as raw JavaScript strings. This design choice pairs beautifully with Wayland, a library specifically designed to consume external stylesheets to define component visuals.

To style an encapsulated Wayland component using Posh, follow these steps:
1. Import the necessary CSS string export from the Posh package.
2. Define the Wayland component and its internal template.
3. Inject the imported Posh string directly into the component's style definition array.
4. Utilize Posh's layout hints and semantic classes within the isolated template.

```coffeescript
import { application } from "@dashkite/posh"
# Assume Wayland provides a component definition function
import { component } from "@dashkite/wayland"

export default component
  name: "custom-dashboard"
  # Inject the Posh application stylesheet into the component's encapsulated scope
  styles: [ application ]
  template: ->
    """
    <div class="layout vertical narrower">
      <h1>Dashboard</h1>
      <p class="primary">This component inherits Posh baseline styles cleanly.</p>
    </div>
    """
```
