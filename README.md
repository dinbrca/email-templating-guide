# Definitive HTML Email Templating Guide [Transactional / Marketing Email Templating]

## Introduction
Some general email guidelines:
- https://stackoverflow.com/questions/127498/what-guidelines-for-html-email-design-are-there
- https://www.pinpointe.com/blog/email-campaign-html-and-css-support
- https://graphicdesign.stackexchange.com/questions/5118/is-there-a-standard-sizewidth-for-email-newsletter-design-or-something-like-a
- https://www.sitepoint.com/how-to-code-html-email-newsletters/
- Use Litmus for email testing


Some Pre-made Templates Sources:

- https://foundation.zurb.com/emails/email-templates.html

- https://github.com/mailgun/transactional-email-templates


## Guide
General:

- Direct email and forwarded email are totally different and receive different styling by email clients

Responsive design:

CSS Styling:


Problems:
- Outlook ignores fonts: <https://stackoverflow.com/questions/30057404/outlook-2013-ignores-font-family> - to fix - any nested table needs to have a `font-family`
- Outlook ignores direction in rtl: to fix- any nested table needs to `dir="rtl"`
- Outlook have extra white border: <https://stackoverflow.com/questions/8015773/table-style-border-outlook-2010-adds-an-extra-space> - fix - use ` style="border-collapse:collapse; mso-table-lspace:0pt; mso-table-rspace:0pt;"` on each table
- Outlook doesn't center: <https://stackoverflow.com/questions/2426072/is-there-an-equivalent-of-css-max-width-that-works-in-html-emails> - fix - use hack in the link
- Outlook and images not using max-width property: <https://stackoverflow.com/questions/20989897/image-style-height-and-width-not-taken-in-outlook-mails> - fix - use a parent with fixed width and then half width in images
- Images on mobile are pixelized - to fix - create an image with a size of 2x and resize the image to half of it in the html
- Gmail showing a download image button: <https://stackoverflow.com/questions/26970661/gmail-shows-download-icon-on-images-of-html-email>, <https://www.emailonacid.com/blog/article/email-development/prevent-gmail-from-displaying-image-download-button-in-email>, <https://stackoverflow.com/questions/28565323/disable-gmails-image-download-popup> - fix - wrap the image with an href `<a href="#"><img width="260" height="196" style="pointer-events:none !important" src="https://cdn.greeninvoice.co.il/files/ugc/e/8/8/e88b74294ed84f8eb76471c5f83b7e26.png" alt="ברוכים הבאים לחשבונית ירוקה"/></a>`
- Avoid using padding - Outlook doesn't like padding, Outlook 2013 / 2016 doesn't support padding at all - fix - for new lines - use `<br/>`, for padding from sides - tables with fixed width
- Avoid margins in images - Outlook.com doesn't like it and removes margins from images as seen in the logo - use `<br/>` for top and bottom margins if you can
- Outlook (for Window) doesn't respect line-height - fix - use `mso-line-height-rule: exactly;line-height:110%;` for `line-height:24px;` effect, `mso-line-height-rule: exactly;line-height: 245%` for almost `line-height:36px;` effect: https://stackoverflow.com/questions/8980956/line-height-not-working-in-outlook-2010-for-html-email
- Border Radius isn't supported in lots of mail, fix: https://www.campaignmonitor.com/forums/topic/7666/borderradius-support-in-email/
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
Instead of the solution of td before and after
- Don't put margin on tables - on outlook the margin is parsed down to each td instead of the table itself - fix - make a wrapper div and put the margin on it.
- if you are using `<p>` - you should add `style="margin:1em 0;"` as fix for outlook - because chrome user agent css adds that.
- If you are using font-size or font-family - use it on every `table`, every `p` tag - because else the client will override you
- use `border="0"` on images and hrefs or else you will get blue or black borders over images as stated in (see picture of the problem): https://litmus.com/blog/prevent-borders-linked-images

## Tools
### Current available tools
- Litmus <https://www.litmus.com/>
- Email on Acid <https://www.emailonacid.com/>

### Tools notes
Litmus:

- Use compiled sources and don't send emails - because this will be a forwarded email
