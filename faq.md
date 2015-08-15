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


2. How do I restrict editting with Guided Access?
  * Enable [Guided Access](https://support.apple.com/en-us/HT202612) in the Settings app. 
<img src="{{ "img/guided-access-overview.png" | prepend: site.baseurl }}" width="300"  alt="Guided Access overview">
  * Triple click the home button to view Guide Access options
<img src="{{ "img/guided-access-options.png" | prepend: site.baseurl }}" width="300"  alt="Guided Access options">
  * Press the Options button to view available options for the devices. 
    * Geometry Stash currently allows disabling of slide toggle (☰) and the Slide Management view (📂). 