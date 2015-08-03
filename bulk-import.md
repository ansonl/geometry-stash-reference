---
layout: page
title: Bulk Import Info
permalink: /bulk-import/
---

Import multiple files at once into Geometry Stash using the bulk import file format. There are two types of bulk import files:
  * [Aggregate](#aggregate-bulk-import)
  * [URL](#url-bulk-import)

The bulk import file is a JSON file with a key value dictionary at its root. 

The root level dictionary contains keys
  * [**type**](#type)
  * [description](#description)
  * [**filenameBase**](#filenamebase)
  * [***decimal version number***](#decimal-version-number)
All keys **besides** `description` are required.

Type
------

The `type` key value must be `bulkAggregateFile` or `bulkURLFile` depending on the type of file being imported.

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


Aggregate Bulk Import
------

All imported slide's contents (slide root dictionaries) are elements of the ***decimal version number*** key value array. An example of an aggregate bulk import file:

```json
{
  "type": "bulkAggregateFile",
  "description": "Sample bulk import file for Geometry Stash",
  "filenameBase": "customBaseFilenameForDownloadedFiles",
  "1.0": [
    {
      "elements": [
        {
          "comment": "title",
          "shapeType": "text",
          "originx": 100,
          "originy": 100,
          "width": 3800,
          "height": 300,
          "fontHeight": 250,
          "fillColor": "#000000",
          "text": "Sample Slide 1",
          "alignment": "center"
        },
        {
          "comment": "vertical separator line",
          "shapeType": "line",
          "originx": 2700,
          "originy": 500,
          "thickness": 10,
          "endx": 2700,
          "endy": 2900,
          "strokeColor": "#000000"
        },
        {
          "comment": "description text",
          "shapeType": "text",
          "originx": 100,
          "originy": 500,
          "width": 2500,
          "height": 700,
          "fontHeight": 150,
          "fillColor": "#000000",
          "text": "sample text",
          "alignment": "center"
        }
      ],
      "bgcolor": "#E4C29B",
      "title": "Sample Slide 1",
      "author": "Anson Liu",
      "desc": "Sample Slide 1"
    }
  ],
  "1.1": [
    {
      "elements": [
        {
          "comment": "title",
          "shapeType": "text",
          "originx": 100,
          "originy": 100,
          "width": 3800,
          "height": 300,
          "fontHeight": 250,
          "fillColor": "#000000",
          "text": "Sample Slide 1",
          "alignment": "center"
        },
        {
          "comment": "vertical separator line",
          "shapeType": "line",
          "originx": 2700,
          "originy": 500,
          "thickness": 10,
          "endx": 2700,
          "endy": 2900,
          "strokeColor": "#000000"
        },
        {
          "comment": "description text",
          "shapeType": "text",
          "originx": 100,
          "originy": 500,
          "width": 2500,
          "height": 700,
          "fontHeight": 150,
          "fillColor": "#000000",
          "text": "sample text",
          "alignment": "center"
        }
      ],
      "bgcolor": "#E4C29B",
      "title": "Sample Slide 1",
      "author": "Anson Liu",
      "desc": "Sample Slide 1"
    },
    {
      "elements": [
        {
          "comment": "title",
          "shapeType": "text",
          "originx": 100,
          "originy": 100,
          "width": 3800,
          "height": 300,
          "fontHeight": 250,
          "fillColor": "#000000",
          "text": "Sample Slide 2",
          "alignment": "center"
        },
        {
          "comment": "vertical separator line",
          "shapeType": "line",
          "originx": 2700,
          "originy": 500,
          "thickness": 10,
          "endx": 2700,
          "endy": 2900,
          "strokeColor": "#000000"
        },
        {
          "comment": "description text",
          "shapeType": "text",
          "originx": 100,
          "originy": 500,
          "width": 2500,
          "height": 700,
          "fontHeight": 150,
          "fillColor": "#000000",
          "text": "sample text",
          "alignment": "center"
        }
      ],
      "bgcolor": "#E4C29B",
      "title": "Sample Slide 2",
      "author": "Anson Liu",
      "desc": "Sample Slide 2"
    }
  ]
}
```

URL Bulk Import
------

Imported slides' URLs (strings) are elements of the ***decimal version number*** key value array. An example of a URL bulk import file:

```json
{
  "type": "bulkURLFile",
  "description": "Sample bulk URL import file for Geometry Stash",
  "filenameBase": "customBaseFilenameForDownloadedFiles",
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