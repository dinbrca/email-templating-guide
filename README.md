# Definitive HTML Email Templating Guide [Transactional / Marketing Email Templating]

This guide was created after having issues while working at Green Invoice to refactor our transaction email system.

This guide was built upon my experiences and others.

## Contribution
Contribution is welcomed, we will merge any pull request happily.

## Introduction
Some general email guidelines:

- Consider as it's 1997

- Use Litmus for email testing


Some Pre-made Templates Sources:

- https://foundation.zurb.com/emails/email-templates.html

- https://github.com/mailgun/transactional-email-templates

- https://github.com/wildbit/postmark-templates


## Guide
### General:

- Direct email and forwarded email are totally different and receive different styling by email clients

- Use tables and not divs

- Check your email distribution statistics to see which email clients are used the most. example:
![Image](https://github.com/dinbrca/email-templating-guide/raw/master/35093055-e136e7e4-fc49-11e7-8ec5-ccd0ef2afa89.png)

- You should also check versions distribution of operating systems:
    - Android distribution: <https://developer.android.com/about/dashboards/index.html#Platform>

- Prefered width of email is between 550-600 pixels, although I myself have used 680 pixels and it was fine.

- Allow users to view the email in browser and not in email client.
![Image](https://github.com/dinbrca/email-templating-guide/raw/master/Screen%20Shot%202018-01-22%20at%2011.52.11%20AM.png)

- Although `<html>`, `<body>`, etc.. tags aren't a must - the recommended base for an email template is as the following:
```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
    <meta name="viewport" content="width=device-width"/>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"/>
    <title>Email Title</title>
    <style type="text/css">
    </style>
    <!--[if mso]>
    <style type="text/css">
    </style>
    <![endif]-->
</head>

<body itemscope itemtype="http://schema.org/EmailMessage">

</body>
</html>
```

### Responsive design:
- Use Tables

### Images:
- Images on mobile are pixelized - to fix - create an image with a size of 2x and resize the image to half of it in the html
- Gmail showing a download image button: <https://stackoverflow.com/questions/26970661/gmail-shows-download-icon-on-images-of-html-email>, <https://www.emailonacid.com/blog/article/email-development/prevent-gmail-from-displaying-image-download-button-in-email>, <https://stackoverflow.com/questions/28565323/disable-gmails-image-download-popup> - fix - wrap the image with an href `<a href="#"><img width="260" height="196" style="pointer-events:none !important" src="https://cdn.greeninvoice.co.il/files/ugc/e/8/8/e88b74294ed84f8eb76471c5f83b7e26.png" alt="ברוכים הבאים לחשבונית ירוקה"/></a>`
- Avoid margins in images - Outlook.com doesn't like it and removes margins from images as seen in the logo - use `<br/>` for top and bottom margins if you can

### RTL (Right to Left):
- Outlook ignores direction in rtl: to fix- any nested table needs to `dir="rtl"`

### Fonts:
- Outlook ignores fonts: <https://stackoverflow.com/questions/30057404/outlook-2013-ignores-font-family> - to fix - any nested table needs to have a `font-family`
- If you are using font-size or font-family - use it on every `table`, every `p` tag - because else the client will override you

### CSS Styling:
- Use Inline CSS to override email client CSS
- You can use condition styling for Outlook like this:
```
<!--[if mso]>
<style type="text/css">
</style>
<![endif]-->
```
- Outlook and images not using max-width property: <https://stackoverflow.com/questions/20989897/image-style-height-and-width-not-taken-in-outlook-mails> - fix - use a parent with fixed width and then half width in images
- Avoid using padding - Outlook doesn't like padding, Outlook 2013 / 2016 doesn't support padding at all - fix - for new lines 
- Outlook (for Window) doesn't respect line-height - fix - use `mso-line-height-rule: exactly;line-height:110%;` for `line-height:24px;` effect, `mso-line-height-rule: exactly;line-height: 245%` for almost `line-height:36px;` effect: https://stackoverflow.com/questions/8980956/line-height-not-working-in-outlook-2010-for-html-email
- Border Radius isn't supported in lots of mail, fix: https://www.campaignmonitor.com/forums/topic/7666/borderradius-support-in-email/

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

### Hrefs / Anchors / Links:
- use `border="0"` on images and hrefs or else you will get blue or black borders over images as stated in (see picture of the problem): https://litmus.com/blog/prevent-borders-linked-images
![Image](https://github.com/dinbrca/email-templating-guide/raw/master/ol2000-vertical-allowed-1366.png)

### Paragraphs (`<p>`):
- if you are using `<p>` - you should add `style="margin:1em 0;"` as fix for outlook - because chrome user agent css adds that.

### Other Problems:
- use `<br/>`, for padding from sides - tables with fixed width

## General Tools
### Current available tools
- Litmus <https://www.litmus.com/>
- Email on Acid <https://www.emailonacid.com/>

### Tools notes
Litmus:

- Use compiled sources and don't send emails - because this will be a forwarded email

## Dev Tools
### Current available tools
- Inlining CSS tools: https://github.com/imlucas/gulp-juice

## Other Information
- Litmus has a great blog with information on fixing problems: https://litmus.com/blog/
- https://stackoverflow.com/questions/127498/what-guidelines-for-html-email-design-are-there
- https://www.pinpointe.com/blog/email-campaign-html-and-css-support
- https://graphicdesign.stackexchange.com/questions/5118/is-there-a-standard-sizewidth-for-email-newsletter-design-or-something-like-a
- https://www.sitepoint.com/how-to-code-html-email-newsletters/
