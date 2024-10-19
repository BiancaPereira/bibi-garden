[[ReadItLater]] [[Article]]

# [Introduction — Stitches](https://stitches.dev/docs/introduction)

The what and the why of Stitches.

![Stitches logo with a purple and blue gradient](ReadItLater%20Inbox/assets/Stitches%20logo%20with%20a%20purple%20and%20blue%20gradient..png)

Stitches is a lightweight, performant styling library with a focus on component architecture and developer experience.

[](https://stitches.dev/docs/introduction#performance)

## [Performance](https://stitches.dev/docs/introduction#performance)

[](https://stitches.dev/docs/introduction#performance)

[](https://stitches.dev/docs/introduction#near-zero-runtime)

### [Near-Zero Runtime](https://stitches.dev/docs/introduction#near-zero-runtime)

[](https://stitches.dev/docs/introduction#near-zero-runtime)

At Modulz, performance is paramount. So when designing Stitches, performance was a top priority.

Stitches avoids unnecessary prop interpolations at runtime, making it significantly more performant than other styling libraries.

Both `@stitches/core` and `@stitches/react` libraries weigh in at ~6kb gzipped.

[](https://stitches.dev/docs/introduction#server-side-rendering)

### [Server-Side Rendering](https://stitches.dev/docs/introduction#server-side-rendering)

[](https://stitches.dev/docs/introduction#server-side-rendering)

Many UI libraries document that responsive variants don't work with server-side rendering. Since popular frameworks like [Next.js](https://nextjs.org/) and [Gatsby](https://www.gatsbyjs.com/) have begun prioritising SSR, we wanted a solution that works well.

Stitches supports cross-browser [server-side rendering](https://stitches.dev/docs/server-side-rendering), even for responsive styles and variants.

[](https://stitches.dev/docs/introduction#key-features)

## [Key Features](https://stitches.dev/docs/introduction#key-features)

[](https://stitches.dev/docs/introduction#key-features)

[](https://stitches.dev/docs/introduction#variants)

### [Variants](https://stitches.dev/docs/introduction#variants)

[](https://stitches.dev/docs/introduction#variants)

Stitches introduces [variants](https://stitches.dev/docs/variants) as a first-class citizen, so you can design composable component APIs.

You can define a single variant, multiple variants, and even [compound variants](https://stitches.dev/docs/variants#compound-variants) which allow you to define styles based on a combination of variants.

Variants can be applied conditionally or responsively.

[](https://stitches.dev/docs/introduction#tokens)

### [Tokens](https://stitches.dev/docs/introduction#tokens)

[](https://stitches.dev/docs/introduction#tokens)

One of the most exciting features is the ability to define your own [tokens](https://stitches.dev/docs/tokens) and seamlessly apply them as CSS values. CSS Properties are automatically mapped to token scales. Tokens can even be used in shorthand CSS properties.

[](https://stitches.dev/docs/introduction#theming)

### [Theming](https://stitches.dev/docs/introduction#theming)

[](https://stitches.dev/docs/introduction#theming)

Stitches provides a simple [theming](https://stitches.dev/docs/theming) experience out of the box. Create as many themes as you need, and apply them wherever you want. Each theme generates a CSS class name which overrides the default tokens.

```
const darkTheme = createTheme({
  colors: {
    hiContrast: 'hsl(206,2%,93%)',
    loContrast: 'hsl(206,8%,8%)',
    gray100: 'hsl(206,8%,12%)',
    gray200: 'hsl(206,7%,14%)',
    gray300: 'hsl(206,7%,15%)',
    gray400: 'hsl(206,7%,24%)',
    gray500: 'hsl(206,7%,30%)',
    gray600: 'hsl(206,5%,53%)',
},
  space: {},
  fonts: {},
});
```

[](https://stitches.dev/docs/introduction#utils)

### [Utils](https://stitches.dev/docs/introduction#utils)

[](https://stitches.dev/docs/introduction#utils)

[Utils](https://stitches.dev/docs/utils) allow you to create your own custom CSS Properties, with your own API.

Use utils to create powerful combinations of properties, property aliases and to introduce restrictions when needed.

```
export const { styled, css } = createStitches({
  utils: {
marginX: (value) => ({
      marginLeft: value,
      marginRight: value,
}),
marginY: (value) => ({
      marginTop: value,
      marginBottom: value,
}),
},
});
```

[](https://stitches.dev/docs/introduction#responsive-variants)

### [Responsive Variants](https://stitches.dev/docs/introduction#responsive-variants)

[](https://stitches.dev/docs/introduction#responsive-variants)

Stitches lets you configure [breakpoints](https://stitches.dev/docs/responsive-styles) and apply variants responsively using the `css` prop. CSS at-rules can also be used inline if needed.

```
export const { styled, css } = createStitches({
  media: {
    bp1: '(min-width: 640px)',
    bp2: '(min-width: 768px)',
    bp3: '(min-width: 1024px)',
    bp4: '(min-width: 1280px)',
},
});
```

[](https://stitches.dev/docs/introduction#overrides)

### [Overrides](https://stitches.dev/docs/introduction#overrides)

[](https://stitches.dev/docs/introduction#overrides)

Stitches provides a `css` prop for overriding styles on any Stitches component. You can use this prop to define layout concerns and/or [overrides](https://stitches.dev/docs/overriding-styles). Tokens and breakpoints also work in the `css` prop.

```
<Button css={{ backgroundColor: 'red' }}>Button</Button>
```

Stitches also provides a polymorphic `as` prop for defining which tag a component renders.

```
<Text as="h1">Heading</Text>
<Text as="p">Paragraph</Text>
```

[](https://stitches.dev/docs/introduction#developer-experience)

### [Developer Experience](https://stitches.dev/docs/introduction#developer-experience)

[](https://stitches.dev/docs/introduction#developer-experience)

One of our main goals is to provide the best possible developer experience. Stitches provides a fully-typed API, so when using TypeScript, CSS properties, values, and breakpoints will be auto-completed for you.

Also, when using the `as` prop, the prop suggestions will update.

We're excited to see the community adopt Stitches, raise issues, and provide feedback. Whether it's a feature request, bug report, or a project to showcase, please get involved!

-   [Discord](https://discord.com/invite/H4eG3Mk)
    
-   [Twitter](https://twitter.com/stitchesjs)
    
-   [GitHub Discussions](https://github.com/stitchesjs/stitches/discussions)
    
-   [GitHub](https://github.com/stitchesjs/stitches)
    

[](https://stitches.dev/docs/introduction#credits)

## [Credits](https://stitches.dev/docs/introduction#credits)

[](https://stitches.dev/docs/introduction#credits)

We're grateful for everyone who contributed and provided feedback along the way.

Special thanks to [Jonathan Neal](https://twitter.com/jon_neal) for the commitment and dedication to building a best-in-class library, being true to current and future CSS specs.

Special thanks to [Pedro Duarte](https://twitter.com/peduarte) for the API design, thorough testing, roadmap and documentation.

Special thanks to [Abdulhadi Alhallak](https://twitter.com/hadi_hlk) for the relentless wars with TypeScript to provide the best possible developer experience.

Special thanks to [Colm Tuite](https://twitter.com/colmtuite) and [Stephen Haney](https://twitter.com/sdothaney) for bringing Stitches under the Modulz organisation and dedicating a team to maintaining it.