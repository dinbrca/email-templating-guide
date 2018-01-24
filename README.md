# Definitive HTML Email Templating Guide [Transactional / Marketing Email Templating]

This guide was created after having issues while working at Green Invoice to refactor our transaction email system.

This guide was built upon my experiences and others and comes to help solving most of the issues of email templating.

## Contributions
Contributions are welcomed, we will merge any pull request happily.

If you add a note please try to follow the way shown in here such as: before, after pictures, code examples.

## Introduction
Some general email guidelines:

- Consider yourself as a programmer in year 1999

- There is no standart to email templating

- Use email testing applications to resolve issues


Some Pre-made Templates Sources:

- https://foundation.zurb.com/emails/email-templates.html

- https://github.com/mailgun/transactional-email-templates

- https://github.com/wildbit/postmark-templates


## Guide

- **[General](docs/guide/general.md)**
- **[Responsive Design](docs/guide/responsive-design.md)**
- **[Images](docs/guide/images.md)**
- **[RTL (Right to Left)](docs/guide/rtl.md)**
- **[Fonts](docs/guide/fonts.md)**
- **[CSS Styling](docs/guide/css-styling.md)**
- **[CSS Support](docs/guide/css-support.md)**
- **[Tables](docs/guide/tables.md)**
- **[Hrefs / Anchors / Links](docs/guide/anchors.md)**
- **[Paragraphs](docs/guide/paragraphs.md)**
- **[Other](docs/guide/other.md)**

## General Tools
### Current available tools
- Litmus <https://www.litmus.com/>, Live example for Litmus rendering: <https://litmus.com/previews/public/d6d8342>
- Email on Acid <https://www.emailonacid.com/>
- BrowserStack

### Tools notes
Litmus:
- Currently the best tool for testing emails
- Sometimes have problems with rendering, see example (when this happens you might need to retry the render):
![Image](https://github.com/dinbrca/email-templating-guide/raw/master/ol2016-vertical-allowed-1366%20(2).png)
- Use compiled sources or send emails directly - do not forward emails


## Dev Tools
### Current available tools
- Inlining CSS tools:
    - Online Tools
         - http://zurb.com/ink/inliner.php
    - Code Tools
         - https://github.com/imlucas/gulp-juice
         - http://premailer.dialect.ca/

## Other Information
- Litmus has a great blog with information on fixing problems: https://litmus.com/blog/
- https://stackoverflow.com/questions/127498/what-guidelines-for-html-email-design-are-there
- https://www.pinpointe.com/blog/email-campaign-html-and-css-support
- https://www.sitepoint.com/how-to-code-html-email-newsletters/
- https://www.emailonacid.com/blog/article/email-development/12_things_you_must_know_when_developing_for_gmail_and_gmail_mobile_apps#gmail_tip1
- https://www.campaignmonitor.com/resources/guides/
