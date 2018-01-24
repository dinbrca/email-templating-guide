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

![Image](https://github.com/dinbrca/email-templating-guide/raw/master/android4-vertical-allowed-1366.png)

After:

![Image](https://github.com/dinbrca/email-templating-guide/raw/master/android4-vertical-allowed-1366%20(1).png)

- Add some side margins so that the text won't be close to the screen border to each element using `margin:0 1em;` as example:

Before:

![Image](https://github.com/dinbrca/email-templating-guide/raw/master/androidoutlook-vertical-allowed-1366.png)

After:

![Image](https://github.com/dinbrca/email-templating-guide/raw/master/androidoutlook-vertical-allowed-1366%20(1).png)