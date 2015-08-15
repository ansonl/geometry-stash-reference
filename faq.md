---
layout: page
title: Frequently Asked Questions
permalink: /faq/
weight: 8
---

FAQ
======

1. Exporting a slide as an image cuts off some of the text.
  * Text cutoff is a known issue, the iOS system does not correctly determine the height of a [UITextView](https://developer.apple.com/library/ios/documentation/UIKit/Reference/UITextView_Class/) if it is rendered off screen. We are working to fix this bug. 
  * **Workaround:** Adding extra newline characters `\n` at the end of the text key value will artificially increase the rendered UITextView height. 

2. How do I use Guided Access?
  * Enable [Guided Access](https://support.apple.com/en-us/HT202612) in the Settings app. 
  * Triple click the home button to view Guide Access options
  <img src="{{ "img/guided-access-overview.jpg" | prepend: site.baseurl }}" width="330" align="left" style="margin-bottom:0" alt="#Shape Element Drawing Demo">
  <img src="{{ "img/guided-access-options.jpg" | prepend: site.baseurl }}" width="330" align="left" style="margin-bottom:0" alt="#Shape Element Drawing Demo">