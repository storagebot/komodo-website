---
title: Multi-row Editor Tabs for Komodo
author: Todd Whiteman
date: 2014-10-22
tags: [macro, javascript, tabs]
description: This little macro will wrap Komodo's editor tabs into multiple rows of tabs when there is not enough space to display all of them.
layout: blog
---

## The Macro

This is a JavaScript macro (best to set the macro to trigger on the Komodo
startup event) that wraps your editor tabs into multiple rows, making all the
tabs visible at once:

https://github.com/Komodo/macros/blob/master/editor_tabs_multiple_rows.js

## Screenshot

Here's what is looks like with multiple tab rows:

<img src="/images/blog/2014-10/multi-row-editor-tabs.png" style="vertical-align: middle">

## Developer Notes

The JavaScript code that finds the correct UI elements is a little ugly - but it
shows some interesting techniques for accessing the anonymous DOM nodes (XBL) in
Komodo's UI. [XBL][] is an algamation of multiple UI elements, but it condenses
(hides) these elements so it just behaves like one individual DOM node.

Note that it's actually a lot simpler to implement this directly using CSS
(using [Stylish][] or [userChrome.css][] with the following rules:

```CSS
/* Make the editor scroll tabs wrap around. */
#topview .arrowscrollbox-scrollbox {
	overflow: visible;
}
#topview .arrowscrollbox-scrollbox > box {
	display: inline-block;
}
```

## Installation

To install the macro simply hit the "View Resource" and "Install Instructions"
links below.

Once installed - invoke the macro on demand or set the macro to run on the
Komodo startup event.

<div class="centered">
    <div class="spacer"></div>
    <a href="http://komodoide.com/resources/macros/toddw-as--multiroweditortabs/" class="button big primary">
        <i class="icon icon-eye"></i>
        View Resource
    </a>
    <div class="spacer-half"></div>
    <span>
        <i class="icon icon-question"></i>
        <a href="http://komodoide.com/resources/install-instructions/#pane-macro" target="_blank">Install Instructions</a>
    </span>
</div>

## Related Materials

* [Komodo Developer Extension][] - play around with JavaScript or Python code in
  the context of the Komodo window
* [Komodo Macro API][] - to programatically interact with the Komodo editor -
  available to both Python and JavaScript
* [Editor API][] - the Komodo editor provides a wrapper around the Scintilla API


[XBL]: https://developer.mozilla.org/en-US/docs/XBL
[Stylish]: http://komodoide.com/resources/addons/jasonbarnabe--stylish/
[userChrome.css]: http://community.activestate.com/faq/customizing-the-komodo-ui
[Komodo Developer Extension]: /framed/?http://community.activestate.com/node/1824
[Komodo Macro API]: /framed/?http://docs.activestate.com/komodo/latest/macroapi.html
[Editor API]: http://www.scintilla.org/ScintillaDoc.html
