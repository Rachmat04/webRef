# WebRef

**WebRef** is a browser-based JavaScript tool that generates Wikipedia `{{Cite web}}` references from web pages. It automatically extracts article metadata, formats it into a citation template, and displays the result in a floating toolbar for quick copying and use on Wikipedia.

The script was originally based on WebRef by V111P and has been adapted for use on the Indonesian Wikipedia.

## Overview

WebRef analyses the current web page and attempts to collect information such as:

- Article title
- Publication date
- Author name(s)
- Website name
- Publisher
- Language code
- Canonical URL

The collected data is then converted into a ready-to-use Wikipedia citation.

Example output:

```wikitext
<ref>{{Cite web
| title = Example article
| last = Smith | first = John
| work = Example News
| date = 31 May 2026
| access-date = 31 May 2026
| url = https://example.com/article
| language = en
}}</ref>
```

---

## Main features

### Automatic metadata extraction

WebRef searches multiple metadata standards commonly used on websites:

- Open Graph (`og:title`, `og:site_name`, etc.)
- Twitter Card metadata
- Schema.org microdata
- Dublin Core metadata
- Citation metadata
- Standard HTML meta tags
- Page title and headings

This allows it to work on many news sites, blogs, and online publications without manual configuration.

### Citation template generation

The script automatically builds a complete `{{Cite web}}` template using the extracted information.

Supported parameters include:

- `title`
- `trans-title`
- `author`
- `last`
- `first`
- `work`
- `date`
- `access-date`
- `url`
- `publisher`
- `language`
- `quote`

### Author formatting

Author names can be automatically converted into Wikipedia citation format.

Example:

```text
John Smith
```

becomes:

```wikitext
| last = Smith
| first = John
```

Multiple authors are also supported.

### Date formatting

Dates can be converted between:

- DMY (Day Month Year)
- MDY (Month Day Year)
- YMD (Year Month Day)

Example:

```text
31 May 2026
2026-05-31
05/31/2026
```

### Quote support

If text is selected on the web page before running WebRef, the selected text can be inserted into the citation's `quote` parameter.

### One-click copy

Generated citations can be:

- Copied directly to the clipboard
- Selected automatically
- Converted into a compact single-line format before copying

### Reference name generator

WebRef can automatically generate reference names based on:

- Website domain
- Article title
- Current time

Example:

```wikitext
<ref name="example.com_ArticleTit_123456">
```

### Site-Ssecific configuration

The script supports custom extraction rules for individual websites.

Configuration data can be:

- Loaded from local storage
- Saved to local storage
- Imported temporarily
- Shared between pages on the same domain

---

## User interface

When activated, WebRef displays a toolbar at the top of the page.

Available controls include:

| Button | Function |
|----------|----------|
| Compact & Copy | Converts citation to compact format and copies it |
| Compact & Select | Converts citation to compact format and selects it |
| Authors | Formats author names |
| DMY | Formats dates as Day Month Year |
| YMD | Formats dates as Year Month Day |
| RefName | Generates a reference name |
| Horiz./Vertical | Switches between horizontal and vertical template layout |
| Reload | Re-scans the page |
| Close | Hides the toolbar |
| Site setup | Opens site configuration tools |

---

## Supported metadata sources

### Title

WebRef checks sources such as:

```html
<meta property="og:title">
<meta name="twitter:title">
<meta name="citation_title">
<title>
<h1>
```

### Date

WebRef checks sources such as:

```html
<meta itemprop="datePublished">
<meta property="article:published_time">
<meta name="citation_date">
<meta name="DC.date">
```

### Author

WebRef checks sources such as:

```html
<meta itemprop="author">
<meta property="article:author">
<meta name="citation_author">
<meta name="DC.creator">
```

### Site name

WebRef checks sources such as:

```html
<meta property="og:site_name">
<meta name="application-name">
<meta name="citation_publisher">
```

### Language

WebRef checks sources such as:

```html
<html lang="en">
<meta itemprop="inLanguage">
<meta name="citation_language">
```

---

## Localisation

The script is designed to be localised for different Wikipedias.

Localisable elements include:

- Month names
- Language codes
- User interface text
- Date formats
- Citation parameter names
- Author separators

The source code contains comments marked:

```javascript
// LOCALIZE
```

These indicate areas that should be modified when adapting the script for another language community.

---

## Site configuration system

WebRef includes a configuration tool that helps create extraction rules for websites that do not expose metadata consistently.

The setup interface allows users to:

1. Open an article page.
2. Search for article title, date, and author text.
3. Select matching page elements.
4. Generate extraction code.
5. Save settings locally.

Configuration is stored in the browser's local storage.

---

## Warnings and validation

WebRef can display warnings when:

### Ambiguous dates

Example:

```text
05/06/2026
```

The script may not know whether this means:

```text
5 June 2026
```

or

```text
6 May 2026
```

A warning is shown so the citation can be checked manually.

### Quote inserted

If selected text is added to the `quote` parameter, a warning indicator is displayed.

---

## Browser storage

WebRef uses browser local storage to save site-specific settings.

Stored information may include:

- Site extraction rules
- Language settings
- Publisher information
- Author formatting preferences

If local storage is unavailable, site-specific configuration cannot be saved.

---

## Limitations

- Metadata quality depends on the website.
- Some websites may not expose publication dates or authors.
- Author names may require manual correction.
- Dynamically generated content may not always be detected.
- Ambiguous numeric dates may require verification.
- Site-specific configuration may be needed for some websites.

---

## Compatibility

WebRef is designed to run in modern web browsers that support:

- JavaScript
- DOM APIs
- Local Storage
- JSON
- Clipboard commands

Older browsers may not support all features.

---

## Privacy

WebRef runs entirely within the user's browser.

The script:

- Does not send citation data to external servers.
- Does not upload page content.
- Stores site configuration locally in the browser.

---

## License

This script is adapted from the original WebRef project created by V111P.

Check the original source and local project documentation for licensing information before redistributing or modifying the code.

---

## Disclaimer

This script is provided as-is.

There is no warranty regarding:

- Accuracy of extracted metadata
- Correctness of generated citations
- Compatibility with all websites
- Availability of future updates

Users should review generated citations before publishing them on Wikipedia or other Wikimedia projects.