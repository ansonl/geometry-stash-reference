---
layout: page
title: Bulk Import Info
permalink: /bulk-import/
---

Import multiple files at once into Geometry Stash using the bulk import file format. 

The bulk import file is a JSON file with a key value dictionary at its root. A sample bulk import file is shown below.

```json
{
  	"type":"bulk",
    "description":"Sample bulk import file for Geometry Stash",
    "filenameBase":"customBaseFilenameForDownloadedFiles",
    "1.0": [
        "http://example.com/oldSlide1.slide",
        "http://example.com/oldSlide3.slide",
        "http://example.com/oldSlide3slide"
    ],
    "1.1": [
        "http://example.com/currentSlide1.slide",
        "http://example.com/currentSlide2.slide",
        "http://example.com/currentSlide3slide"
      ]
}
```

The root level dictionary contains keys
  * **type**
  * description
  * **filenameBase**
  * ***decimal version number***
Keys in **bold** are required.

Type
------

The `type` key value must be `bulk`.

Description
------

The `description` key value can be a string description of what is bulk import file contains. Providing a description is optional. 

FilenameBase
------

The `filenameBase` key value must be a string value. All downloaded files will be saved with this string as the filename with a integer value appended. The above sample will save three files named
  * customBaseFilenameForDownloadedFiles1
  * customBaseFilenameForDownloadedFiles2
  * customBaseFilenameForDownloadedFiles3

*Decimal version number*
------

This key is a decimal version number. Geometry Stash will **only** download files from the highest version number. 
  * 1.0 - *valid*
  * 1.1 - *valid*
  * 1.0.1 - *bad*
  * 1.1.1 - *bad*

The value of this key is an array of strings. These strings are URLs of files to download.
`1.1` is the highest version number in the above sample. Geometry Stash will download files
  * http://example.com/currentSlide1.slide
  * http://example.com/currentSlide2.slide
  * http://example.com/currentSlide3.slide
