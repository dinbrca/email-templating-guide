### Responsive design:
- Use Tables
- Some clients - mainly mobile support media queries:

The following CSS helped achieving responsive tables on mobile:
```
@media only screen and (max-width: 600px) {
    table {
        width: auto !important;
    }
}
```

Before:

![Image](../../images/guide/responsive-design/before-media-queries-android4.png)

After:

![Image](../../images/guide/responsive-design/after-media-queries-android4.png)

- Add some side margins so that the text won't be close to the screen border to each element using `margin:0 1em;` as example:

Before:

![Image](../../images/guide/responsive-design/before-side-margins-androidoutlook.png)

After:

![Image](../../images/guide/responsive-design/after-side-margins-androidoutlook.png)