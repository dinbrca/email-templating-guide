### Other:
- You can use conditions for Outlook, although it's preferable to just fine another way because it makes the code clutered, example:
```
<!--[if mso]>
<style type="text/css">
    body, table, td {
        font-family: Arial, Helvetica, sans-serif !important;
    }
</style>
<![endif]-->
```
- use `<br/>`, for padding from sides - tables with fixed width
- Don't use `<hr/>` - use tables instead.
```
<td style="border-bottom: 2px solid red;margin: 0;padding: 0;width: 680px;max-width: 680px;"></td>
```