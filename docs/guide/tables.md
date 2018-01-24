### Tables:
- Outlook have extra white border: <https://stackoverflow.com/questions/8015773/table-style-border-outlook-2010-adds-an-extra-space> - fix - use ` style="border-collapse:collapse; mso-table-lspace:0pt; mso-table-rspace:0pt;"` on each table
- Outlook doesn't center: <https://stackoverflow.com/questions/2426072/is-there-an-equivalent-of-css-max-width-that-works-in-html-emails> - fix - use hack in the link
- `width="100%"` can create problems in tables with outlook that adds a side border, see one of the images, happened when I wanted to center a table inside table so I used https://stackoverflow.com/questions/10137536/center-div-in-microsoft-outlook
I used a wrapper div which centers like:
```
<div align="center">
    <table dir="rtl" style="font-family: Arial, Helvetica, sans-serif !important;width:450px;border-top:3px solid #18C746;border-bottom:3px solid #18C746;text-align:center">
        <tr>
            <td width="450">
                <p style="margin:2em auto;mso-line-height-rule: exactly;line-height: 160%;">
                    <strong>לגלות את כל מה שחשבונית ירוקה יכולה לתרום לך</strong>
                    <br/><br/>
                    בשבועות הקרובים נשלח לך מיילים עם טיפים איך לנצל את מקסימום היכולות: לחסוך זמן, לתת שירות טוב יותר ללקוחות שלך ולהגדיל רווחיות.
                </p>
            </td>
        </tr>
    </table>
</div>
```
![Image](https://github.com/dinbrca/email-templating-guide/raw/master/ol2016-vertical-allowed-1366%20(3).png)
Instead of the solution of td before and after
- Don't put margin on tables - on outlook the margin is parsed down to each td instead of the table itself - fix - make a wrapper div and put the margin on it.
![Image](https://github.com/dinbrca/email-templating-guide/raw/master/ol2016-vertical-allowed-1366%20(2).png)