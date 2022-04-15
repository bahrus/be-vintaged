# be-vintaged [TO-DO]

Applies "scalable" ShadowDOM styling dynamically.

There are some scenarios where a web component needs to provide the ability of the consumer to pass in styles to apply within its shadow DOM.

This component is designed to do that in a performant way (should the browser support it).

Uses constructible stylesheets for those browsers that have adopted it.  

```html
<template be-vintaged="my-styles">
    <style>
        div{
            color: green;
        }
    </style>
</template>
```

src can be specified on style tag, in which case style is imported via CSS Modules (when available).

Generates web component with name my-styles.

Now, if we add my-styles to a tag:

```html
<xtal-vlist>
    <my-styles></my-styles>
</xtal-vlist>
```

Then by default the style above gets "adopted" into the constructed stylesheet of xtal-vlist's shadow DOM.

Can also apply styles within the shadow DOM realm of the tag itself:

```html
<my-web-component>
    <template shadowroot=open>
        <my-styles apply-to=host></my-styles>
    </template>
</my-web-component>
```

which might be helpful with declarative Shadow DOM.