### Other:
- You can use conditions for Outlook, although it's preferable to just find another way because it makes the code clutered, example:
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
- Don't use `<hr/>` - use tables bottom border instead.
Do:
```
<td style="border-bottom: 2px solid red;margin: 0;padding: 0;width: 680px;max-width: 680px;"></td>
```
Don't:
```
<td width="680" style="background-color:#D1D6D9"></td>
```
Don't:
```
<hr/>
```

Before `<hr/>`:

![Image](../../images/guide/other/before-hr-fix-hr-ol2000)

![Image](../../images/guide/other/before-hr-fix-hr-ol2007)

Before - when using td - height inconsistency:

![Image](../../images/guide/other/before-hr-fix-table-ol2000)

![Image](../../images/guide/other/before-hr-fix-table-ol2007)

After - when using td with border-bottom:

![Image](../../images/guide/other/after-hr-fix-ol2000)

![Image](../../images/guide/other/after-hr-fix-ol2007)

![Image](../../images/guide/other/after-hr-fix-appmail9)

![Image](../../images/guide/other/after-hr-fix-appmail11)
