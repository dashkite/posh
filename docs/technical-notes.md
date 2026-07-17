# Technical Notes

When working with Posh, it helps to understand the underlying philosophy driving its architectural choices. Rather than imposing a heavy framework, Posh leans into the highly compositional nature of CSS to offer a universal styling ruleset. This approach provides a solid baseline for DashKite projects, establishing a shared language for styling low-level structures through small, frequently occurring patterns. 

### Stylus as a Core Language

We chose Stylus for its clean and expressive syntax, which strips away the usual CSS boilerplate. By removing brackets and semicolons, Stylus allows creators to focus on the logic of the styles. This elegant syntax makes it straightforward to rapidly develop mixins and generate clear, maintainable CSS without syntactic noise getting in the way.

### CSS Custom Properties

To ensure Posh remains adaptable at runtime, we manage visual aspects—from color palettes to typographic scales—using [CSS custom properties](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties). By shifting this responsibility to the browser, developers can implement dynamic theming and transition between light and dark modes without needing to recompile the stylesheet.

Crucially, custom properties serve as a configurable styling interface for Web Components. While Web Components generally prioritize strict encapsulation and style isolation, the web platform provides specific affordances to create opportunities for configuration and structured composition. CSS custom properties are one such interface, acting as a deliberate mechanism to pass design tokens into isolated component internals.

### Layered Architecture

Modern CSS provides tools to elegantly manage specificity, and Posh takes full advantage of this by grouping related styles into native [`@layer` directives](https://developer.mozilla.org/en-US/docs/Web/CSS/@layer). Foundational styles reside in layers like `base`, `lexicon`, and `universal`. This organization prevents frustrating specificity wars, guaranteeing that application-specific components can cleanly override the foundation whenever necessary.

### Semantic HTML and Utility Classes

A strong design system starts with meaningful markup. Posh encourages developers to establish document structure using [semantic HTML elements](https://developer.mozilla.org/en-US/docs/Glossary/Semantics#semantics_in_html) whenever possible. When those elements need targeted styling adjustments, you can augment them with utility classes. We intentionally craft the names of these classes to be semantically inspired, keeping the markup logical and accessible—an important consideration for meeting [WAI-ARIA](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA) and general accessibility standards—while offering fine-grained design controls.

### Emergent Properties and Rhythm

A core goal of Posh is to cultivate [emergent properties](https://en.wikipedia.org/wiki/Emergence)—where individual styling rules combine to form a cohesive visual rhythm. For instance, the typography module dynamically calculates font sizes and spacing to establish a page rhythm that isn't explicitly hardcoded into the raw CSS. We also leverage quarter-rem spacing to build consistent spatial relationships. Together, these techniques generate a sense of visual expectation, gently guiding the eye and enhancing the overall Human Experience (HX).

### Architecture Decoupling

Since Posh is fundamentally a collection of CSS rules, it remains strictly [decoupled](https://en.wikipedia.org/wiki/Coupling_(computer_programming)) from DashKite web components. This intentional separation keeps the library lightweight and focused solely on presentation. At the same time, we design libraries like Wayland to consume standard stylesheets. By relying on shared open web standards, Posh and Wayland achieve a unified purpose and work beautifully together without being entangled by explicit dependencies.
