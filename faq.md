---
layout: page
title: Frequently Asked Questions
permalink: /faq/
weight: 8
---

FAQ
======
  * [Opening a Bulk Import File is crashing/not importing](#opening-a-bulk-import-filebulk-import-is-crashingnot-importing)
  * [Exporting a slide as an image cuts off some of the text.](#exporting-a-slide-as-an-image-cuts-off-some-of-the-text)
  * [How do I control access to editing with Guided Access?](#how-do-i-control-access-to-editing-with-guided-access)


#### Opening a [Bulk Import File](bulk-import/) is crashing/not importing. 

  * Make sure you have specified the correct [`type` key value](http://geometrystash.com/bulk-import/#type) in the import file's root dictionary. Geometry Stash will treat files according to this value. 
  * Null values in a JSON file can cause problems for Geometry Stash. You verify that your JSON file is in the correct format with a web app such as [JSON Editor Online](http://www.jsoneditoronline.org).


#### Exporting a slide as an image cuts off some of the text.

  * Text cutoff is a known issue, the iOS system does not correctly determine the height of a [UITextView](https://developer.apple.com/library/ios/documentation/UIKit/Reference/UITextView_Class/) if it is rendered off screen. We are working to fix this bug. 
  * **Workaround:** Adding extra newline characters `\n` at the end of the text key value will artificially increase the rendered UITextView height. 


#### How do I control access to editing with Guided Access?

  * Enable [Guided Access](https://support.apple.com/en-us/HT202612) in the Settings app. 
<img src="{{ "img/guided-access-overview.png" | prepend: site.baseurl }}" width="300"  alt="Guided Access overview">
  * Triple click the home button to view Guide Access options
<img src="{{ "img/guided-access-options.png" | prepend: site.baseurl }}" width="300"  alt="Guided Access options">
  * Press the Options button to view available options for the devices. 
    * Geometry Stash currently allows disabling of slide toggle (☰) and the Slide Management view (📂). 

#### More Questions

  * Please contact me at [anson@geometrystash.com](mailto:anson@geometrystash.com?subject=Geometry Stash FAQ question). 