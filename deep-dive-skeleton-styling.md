[Tutorials](/tag/tutorials/)

# A comprehensive guide to styling Skeleton

This guide provides an in-depth exploration of styling options available in Skeleton. Whether you're creating a unique theme, customizing elements, or adjusting component props. You'll find a variety of useful tips and techniques for customizing your project.

*   [![Chris Simmons](/content/images/size/w100/2022/11/avatar.jpeg)](/author/chris/)

#### [Chris Simmons](/author/chris/)

Dec 27, 2022 • 13 min read

![A comprehensive guide to styling Skeleton](/content/images/size/w2000/2022/12/styling.jpg)

This guide provides an in-depth exploration of styling options available in Skeleton. Whether you're creating a unique theme, customizing elements, or adjusting component props. You'll find a variety of useful tips and techniques for customizing your project.

## Themes

Themes have a major impact into the overall design process in Skeleton. This is accomplished using [CSS properties](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties) (aka CSS variables) that define your color palette, fonts, border sizes, and other useful settings.

The Skeleton library provides both preset themes, as well as a theme generator, allowing you to create custom themes from scratch. Let's being by reviewing theme options.

### Preset Themes

![](https://skeleton.ghost.io/content/images/2022/12/Screen-Shot-2022-12-23-at-1.21.59-PM.png)

By default, Skeleton comes with a curated set of preset themes. Each theme is hand crafted to balance visual aesthetics, provide support for both light and dark modes, as well as provide adequate color contrast for accessibility. Furthermore each preset contains optional features to extend and augment your app design, such as a background mesh gradients. If you're in a hurry to get started, preset theme provide a quick and effortless way to import the style of your app out of the box.

Please be aware you can test each preset using the "Theme" drop down at the top-right of the [Skeleton documentation](https://www.skeleton.dev/). Select any preset theme option and you'll immediately see a live preview that carries through the entire site.

![](https://skeleton.ghost.io/content/images/2022/12/Screen-Shot-2022-12-26-at-3.19.27-PM.png)

Once you've decided on the theme, visit the **[Guides > Themes](https://dev.skeleton.dev/guides/themes)** to learn how to implement a theme in your project. Prese themes are imported into your project's root layout in `/src/routes/+layout.svelte`.

```ts
import '@skeletonlabs/skeleton/themes/theme-skeleton.css';
```

This imports the default "Skeleton" theme.

If you wish to swap to another theme, change from `theme-skeleton.css` to any other preset, such as `theme-seafoam.css`. Save your changes and you'll see the them applied right away.

### Theme Generator

In most cases presets are a great starting point, but if you're designing your project for a company, you may wish to adhere to certain brand colors and aesthetics. Thankfully Skeleton provides a robust Theme Generator to help get you started.

> Note the generator has recently received several major updates to expand the color palette, improved a11y color ratios, as well as make the UI and UX more intuitive and useful.

You can find the newly revamped Theme Generator here:

[

Skeleton — UI Toolkit for Svelte + Tailwind

Skeleton is a fully featured Svelte UI component library that allows you to build fast and reactive web UI using Svelte + Tailwind.

![](https://www.skeleton.dev/favicon.png)Skeleton



](https://www.skeleton.dev/guides/themes/generator)

![](https://skeleton.ghost.io/content/images/2022/12/Screen-Shot-2022-12-23-at-1.33.01-PM.png)

The theme generator.

Simply toggle ON the "Live Preview Mode" option and begin editing the colors and settings. You'll note the entire documentation site updates to reflect your changes. Custom styles will even persist as you browse to other pages on the site, providing an excellent way to preview changes to components and other features right away. Use this to test color balance between light and dark modes as well.

If you're not design savvy, don't worry, we've provided a "Randomize Colors" button to quickly generate a palette for you. For best results we recommend randomizing until you find a nice foundation, then fine tune each color to your preference. Be mindful not to make colors too light or dark. Each row and shade should have a unique value.

Here's a quick reference for what each color represents in your theme:

![](https://skeleton.ghost.io/content/images/2022/12/Screen-Shot-2022-12-23-at-1.56.01-PM.png)

[

Skeleton — UI Toolkit for Svelte + Tailwind

Skeleton is a fully featured Svelte UI component library that allows you to build fast and reactive web UI using Svelte + Tailwind.

![](https://www.skeleton.dev/favicon.png)Skeleton



](https://www.skeleton.dev/guides/themes/colors)

The process for implementing a custom theme is very similar to using a presets. Generate your theme, copy the generated CSS, then add this to a new file in `/src/theme-name.postcss`. You can then import this in your root layout in `/src/routes/+layout.svelte`. Take care to replace any existing preset theme.

```ts
import '../theme-name.postcss';
```

Feel free to replace the word "name" with your preferred theme name.

## Dark Mode

Skeleton provides support for light and dark modes for all themes by default. This feature is enabled directly by Tailwind. We highly recommend reviewing their official documentation if you wish to learn more about how this works.

![](https://skeleton.ghost.io/content/images/2022/12/light-dark-mode.jpg)

[

Dark Mode - Tailwind CSS

Using Tailwind CSS to style your site in dark mode.

![](https://tailwindcss.com/favicons/apple-touch-icon.png?v=3)Tailwind CSS

![](https://tailwindcss.com/api/og?path=/docs/dark-mode)

](https://tailwindcss.com/docs/dark-mode)

## Utility Classes

Skeleton includes a Tailwind Plugin that is used to create a [set of Tailwind utility classes](https://tailwindcss.com/docs/utility-first) for your theme's color palette. For example, here's how the _primary_ color shade 500 is represented in the default Skeleton theme:

```css
--color-primary-500: 15 186 129;
```

These are RGB (red green blue) color values for the hex color **#0FBA81**

Skeleton follows the official Tailwind recommendation for [implementing CSS properties with RGB values](https://tailwindcss.com/docs/customizing-colors#using-css-variables). This allows for [color opacity](https://tailwindcss.com/docs/text-color#changing-the-opacity) via the alpha channel. We've provided a few examples of these generate classes below:

```html
<!-- background utility class -->
<div class="bg-primary-500">Skeleton</div>

<!-- background with 50% transparency utility class -->
<div class="bg-primary-500/50">Skeleton</div>

<!-- text color utilty class -->
<div class="text-primary-500">Skeleton</div>

<!-- border utility class -->
<div class="border border-primary-500">Skeleton</div>

<!-- @apply syntax in <style> blocks -->
<style lang="postcss"
    .example { @apply text-primary-500; }
</style>
```

Utility color classes provide a quick and easy way to implement your custom theme colors in custom elements and components in your project.

## Design Tokens

If you're not familiar with design tokens, we highly recommend the the following conference talk by [Brad Frost](https://twitter.com/brad_frost). He does an excellent job of explaining the concept.

Design tokens are reminiscent of utility classes. However, tokens go well beyond what Tailwind provides out of the box, with a focus on reusability and consumption of the CSS properties set in your theme.

Design tokens take in your theme CSS properties, then apply this in a set of reusable classes that serve as the building blocks for many of the elements and components found in Skeleton.

![](https://skeleton.ghost.io/content/images/2022/12/image-5.png)

The design token lifecycle.

Let's walk through the process of creating a design token. Here we have the light and dark text color set in our theme configuration:

```css
--theme-font-color-base: 0 0 0;
--theme-font-color-dark: 255 255 255;
```

The light theme (base) text color is black, while the dark theme is white.

However, by default, Tailwind doesn't know about these custom property values or provide utility classes for them. This is where Skeleton introduces a set of design token CSS classes use the property setting:

```css
.text-base-token {
	color: rgba(var(--theme-font-color-base));
}
.text-dark-token {
	color: rgba(var(--theme-font-color-dark));
}
.text-token {
	@apply text-base-token dark:text-dark-token;
}
```

*   `.text-base-token` provides only the light theme text color.
*   `.text-dark-token` provides only the dark theme text color.
*   `.text-token` combines both tokens above to handle light and dark modes.

By using `.text-token` in a custom component, you can ensure the text color always conforms to your appropriate theme values in both light and dark modes automatically.

Here's another quick example using the border radius setting from your theme:

```css
.rounded-token {
	border-radius: var(--theme-rounded-base);
}
.rounded-tl-token {
	border-top-left-radius: var(--theme-rounded-base);
}
.rounded-tr-token {
	border-top-right-radius: var(--theme-rounded-base);
}
.rounded-bl-token {
	border-bottom-left-radius: var(--theme-rounded-base);
}
.rounded-br-token {
	border-bottom-right-radius: var(--theme-rounded-base);
}
```

This covers all colors, plus each of the four available corner positions (ex: top-left)

The exciting part of design tokens, is if any of the base theme values are modified, every design token class that utilizes those setting will be updated, which means every component using that class will update as well.

See the clip below to see this in action. Note how the button colors, fonts, and border radius all update when we switch between preset themes:

![](https://skeleton.ghost.io/content/images/2022/12/Kapture-2022-12-23-at-14.33.49.gif)

The best part about design tokens is they're not just available to us, the creators of Skeleton, but you and your projects as well. This allows you to construct custom elements and components using the same tools we do, and take advantage of all the same benefits!

To learn more about design tokens, please see the dedicated documentation section linked below:

[

Skeleton — UI Toolkit for Svelte + Tailwind

Skeleton is a fully featured Svelte UI component library that allows you to build fast and reactive web UI using Svelte + Tailwind.

![](https://www.skeleton.dev/favicon.png)Skeleton

![](https://user-images.githubusercontent.com/1509726/206284722-3aee216b-f2ac-4281-b3c4-fd07e8c18b0c.png)

](https://www.skeleton.dev/elements/tokens)

## Color Pairings

The visualization below displays what we call _color parings_. This is an important concept to learn if you wish to understand how Skeleton balances colors - specifically for light and dark mode.

![](https://skeleton.ghost.io/content/images/2022/12/image-6.png)

Each color shade has a matching pair as you swap between light and dark mode.

For example, the _surface_ color swatch 50 is the lightest available color, so we automatically utilize that for your light theme background color. Swatch 900 is the darkest, so vice versa. These two colors form a pair.

Skeleton provides a set of design tokens such as `.bg-surface-50-900-token` and `bg-surface-900-50-token` which automatically toggles between these in light/dark mode respectively. Again, see the design token documentation for more information on what styles pairings are available.

## Customizing Elements

While Skeleton is designed with Svelte in mind, not every feature can or should be implemented as a component. Instead, in most cases it's much easier to utilize semantic elements created via HTML and CSS. In Skeleton we call these "elements". These provide styles for the default [background color](https://www.skeleton.dev/elements/core), [typography](https://www.skeleton.dev/elements/typography), and [form styles](https://www.skeleton.dev/elements/forms), as well as specific elements such as [buttons](https://www.skeleton.dev/elements/buttons), [lists](https://www.skeleton.dev/elements/lists), and [cards](https://www.skeleton.dev/elements/cards).

For example, click the link below to view the source for button styles:

[

skeleton/buttons.css at master · skeletonlabs/skeleton

A fully featured UI toolkit for Svelte + Tailwind. - skeleton/buttons.css at master · skeletonlabs/skeleton

![](https://github.com/fluidicon.png)GitHubskeletonlabs

![](https://opengraph.githubassets.com/ba79a95c55a50a36e5450dcd7e54ac8369465b1fdf2fa2bfd5b7065971a8ded3/skeletonlabs/skeleton)

](https://github.com/skeletonlabs/skeleton/blob/master/src/lib/styles/elements/buttons.css)

View the Buttons stylesheet

This following snippet shows the base styles for the `.btn` (button) class. You'll note that it's just CSS written in the Tailwind `@apply` format.

```css
.btn {
    /* Size (match base)  */
    @apply text-base px-5 py-[9px];
    /* Core */
    @apply text-center whitespace-nowrap;
    /* Flex Columns */
    @apply inline-flex justify-center items-center space-x-2;
    /* Hover */
    @apply hover:brightness-110;
    /* Transitions */
    @apply transition-all active:scale-90;
    /* Theme: Rounded */
    @apply rounded-token;
}
```

By pairing element classes together, we can can easily mix and match to create interesting combinations, such as this filled button style:

```html
<button class="btn btn-filled-primary">💀 Skeleton</button>
```

![](https://skeleton.ghost.io/content/images/2022/12/Screen-Shot-2022-12-23-at-2.54.19-PM.png)

The important take away here is that elements are _just_ CSS. If you're familiar with CSS, then you should understand the concept of [cascading](https://developer.mozilla.org/en-US/docs/Web/CSS/Cascade#:~:text=The%20cascade%20is%20an%20algorithm,a%20property%20on%20an%20element.), which allows you to easily override and extend styles. Here's a trivial example:

```css
/* The background will initially be red */
.example { background: red; }

/* The background cascades to green and font is set bold */
.example { background: green; font-weight: bold; }
```

Styles that come later in the flow take precedence.

Given this information, we advise a very strict order for importing stylesheets in Skeleton, as shown below:

1.  Your theme (ex: `theme-skeleton.css`)
2.  The `all.css` file containing all the Skeleton-provided styles
3.  Your app's global stylesheet in `/src/app.postcss`

In doing this, any classes defined in your global stylesheet will occur last and take precedence! This means we can easily modify Skeleton elements in global scope.

For example, this is the source for the button class of `.btn-filled-primary`:

```css
.btn-filled-primary {
    @apply bg-primary-500 text-on-primary-token;
}
```

Now let's modify the default background color as well as make the font bold. Add the following to your global stylesheet in `/src/app.postcss` in your project:

```css
.btn-filled-primary {
    @apply bg-purple-500 font-bold;
}
```

![](https://skeleton.ghost.io/content/images/2022/12/Screen-Shot-2022-12-23-at-4.41.11-PM.png)

Every instance of this class will now use the new styles.

If you wish to go further, we recommend consulting the stylesheet source code for each element in the **[Tailwind > Elements](https://www.skeleton.dev/elements/buttons)** section. Just tap the "view source" link at the top of each element documentation page.

![](https://skeleton.ghost.io/content/images/2022/12/Screen-Shot-2022-12-23-at-4.30.34-PM.png)

Note that when overriding these inherent styles you may need to modify BOTH the light and dark mode color variations or append `!` ([important](https://tailwindcss.com/docs/configuration#important-modifier)) as shown below:

```css
/* Override the light and dark mode values */
.example-element { @apply bg-blue-500 dark:bg-purple-500; }

/* Set !important to override both modes */
.example-element { @apply !bg-green-500; }
```

## Customizing Components

One of the most powerful features in Svelte and Skeleton is the ability to modify styles and settings per each component instance. We'll review a few techniques for customizing component in this manner.

### Via Style Props

Unlike other UI libraries, Skeleton doesn't rely on canned options for props (ex: small, medium, large), but instead allows you to pass one or more CSS classes that directly override a style. Take this [App Bar](https://www.skeleton.dev/components/app-bar) component for example:

```html
<AppBar background="bg-red-500 dark:bg-orange-500">Skeleton</AppBar>
```

Here we've used the `background` prop and provided Tailwind utility classes to modify the appearance in both light and dark modes. In light mode the background will appear _red_, while in dark mode the background will be _orange_.

![](https://skeleton.ghost.io/content/images/2022/12/Screen-Shot-2022-12-23-at-4.45.52-PM.png)

Our orange header in dark mode.

We can take this a step further by using design tokens to provide a more compact and reusable format for this kind of change:

```html
<AppBar background="bg-primary-400-500-token">Skeleton</AppBar>
```

This specific design token represents the following styles:

```css
.bg-primary-400-500-token {
	@apply bg-primary-400 dark:bg-primary-500;
}
```

Your not limited to just background colors though. Each component documentation page provides a "Props" tab, which covers available properties, their default setting, along with a brief description. This is one of the most important resources available in the documentation when it comes to modifying components:

![](https://skeleton.ghost.io/content/images/2022/12/Screen-Shot-2022-12-23-at-3.14.11-PM.png)

You can modify background, border, padding, and more for the App Bar.

### Via the Classes Attribute

These "style props" cover common customization targets, however, if a property is not available, don't fret - you can still provide custom classes. Each component in Skeleton supports a standardized `class` attribute. Which allows you to pass arbitrary Tailwind classes as shown:

```html
<ExampleComponent class="border-4 border-red-500">Skeleton</ExampleComponent>
```

Please note these classes are applied ONLY to the parent element in the component template. To understand this, imagine the following is the contents of our fake component called `ExampleComponent`. This represents the HTML template within the `.svelte` file:

```html
<div class="{customClassesAddedHere}">
    <header><slot /></header>
<div>
```

But what if you need to go deeper and target that `header` element? Thankfully Tailwind provides a solution via the [arbitrary variant syntax](https://tailwindcss.com/blog/tailwindcss-v3-1#arbitrary-values-but-for-variants):

```html
<ExampleComponent class="[&>header]:p-4">...</ExampleComponent>
```

This would provide a `.p-4` padding class to the header element.

### Via a Global Stylesheet

If the change you're trying to make should be applied to ALL instances of a particular component, the best way to do this is to modify the component with your global stylesheet. You'll find this process is very similar to styling Skeleton elements.

Each component constructed in Skeleton implements uniquely named "selector" classes, such as `.avatar-image` for the [Avatar component](https://www.skeleton.dev/components/avatars). These classes are implemented with one purpose - to provide semantic handles for global styles.

```html
<img class="avatar-image ..." />
```

Note the the `.avatar-image` class in the Avatar component markup.

To modify a portion of our component template, all we need to do is provide a class in our application's global stylesheet as shown:

```css
.avatar-image { @apply invert; }
```

This global style will invert the colors of the avatar image.

The quickest way to find a particular selector class is either to view the component source on GitHub, or utilize your browser's _Inspect_ tool to locate the class directly in the DOM.

For most browsers you can right-clicking on the item you wish to modify, then choose the "Inspect" option in the popup. This will launch your browser's dev tools. Make sure the Elements tab is selected, then navigate the DOM tree until you find the element you wish to modify.

![](https://skeleton.ghost.io/content/images/2023/01/image.png)

Note the selector class is always the first in the set to ensure they are easy to locate!

## Customizing Utilities

Skeleton provides a wide assortment of utility features. These are created using a combination of Skeleton's element styles, components, actions, and in some cases introduce third party libraries. Given this, you can utilize many of the techniques described above.

For example, let's take a look at how we might modify styles for the Drawer utility.

### Styling Drawers

The Skeleton [drawer](https://www.skeleton.dev/utilities/drawers) allows you to create slide out overlays attached to any window edge. Drawers can be customized in a couple different ways.

First, you can adjust the style props on the Drawer component itself. Our tips regarding style props for components will apply here.

```html
<Drawer bgDrawer="bg-primary-100-800-token" bgBackdrop="bg-surface-primary-token"/>
```

All instances of the drawer will now have a primary color for the backdrop and window.

Second, you can style each instance of the drawer dynamically by providing available style props as key/value pairs in the DrawerSettings object:

```ts
function drawerOpenStyled(): void {
	const settings: DrawerSettings = {
		// ...
		bgDrawer: 'bg-primary-500 text-on-primary-token',
		bgBackdrop: 'bg-primary-500/50',
	};
	drawerStore.open(settings);
}
```

We use the same `bgDrawer` and `bgBackdrop` settings here.

> Note that Skeleton [Modals](https://www.skeleton.dev/utilities/modals) and [Toasts](https://www.skeleton.dev/utilities/toasts) use the same conventions as well! Please consult the documentation for each utility feature to learn more about how to customize each one.

## Wrapping Up

Given the amount of options provided, we feel confident in saying that Skeleton provides one of the most extensible design systems. We encourage you to test these techniques in your own projects. However, if you need more help, don't be afraid to reach out via the Skeleton [GitHub](https://github.com/skeletonlabs/skeleton) or [Discord](https://discord.gg/EXqV7W8MtY).
