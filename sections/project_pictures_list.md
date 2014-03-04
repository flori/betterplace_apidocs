
# Project Pictures List ⇄ [Details](project_picture_details.md)

```nginx
GET https://api.betterplace.org/en/api_v4/projects/1114/pictures.json
```

A list of pictures of a betterplace.org project (donate money).
Results are contained in a *data* attribute.

*Custom picture-sizes:* This API will only deliver the orginal image.
That is the largest image betterplace.org can provide.
Please use an image-transformation-service of your choice to resize this
image to your liking. Note howevers that some have non-url-save characters
that might break services like Sencha Source.

We are working on a better solution. Please contact us for more information.

In the meantime, the following links might help:

* [Sencha Source](http://docs.sencha.io/current/index.html#!/guide/src) provides a easy URL-based solution
* [adaptive-images.com](http://adaptive-images.com/) is a self-hosted solution
* [Google mod_pagespeed "image resizing"](https://developers.google.com/speed/docs/mod_pagespeed/filter-image-optimize)
  should also help – and give you more performance-goodies as well

*For [betterplace.org clients](../README.md#client-api):*
If you request data for a project that is not part of the client
projects, the API will return a `404` HTTP code.


## Input Parameter

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Required/Optional</th>
    <th>Description</th>
  </tr>
  <tr>
    <th align="left">project_id</th>
    <td><code>1114</code></td>
    <td>required</td>
    <td>Project-id as an integer number ≥ 14.</td>
  </tr>
</table>

## Response Attributes

### Root Attributes

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">width</th>
      <td>number</td>
      <td>1024</td>
      <td>Width of the image</td>
    </tr>
    <tr>
      <th align="left">height</th>
      <td>number</td>
      <td>768</td>
      <td>Height of the image</td>
    </tr>
    <tr>
      <th align="left">size</th>
      <td>number</td>
      <td>100234</td>
      <td>Size of the image in bytes</td>
    </tr>
    <tr>
      <th align="left">description</th>
      <td>string</td>
      <td>Yada…</td>
      <td>Description of the picture</td>
    </tr>
    <tr>
      <th align="left">created_at</th>
      <td>string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone) of creation</td>
    </tr>
    <tr>
      <th align="left">updated_at</th>
      <td>string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone) of last update</td>
    </tr>
  </table>
</table>

## Response Links

<table>
  <tr>
    <th>Linkname</th>
    <th>Description</th>
  </tr>

    <tr>
      <th align="left">image</th>
      <td>Link to the original image as uploaded by the user</td>
    </tr>
    <tr>
      <th align="left">self</th>
      <td>The single resource for this picture</td>
    </tr>
    <tr>
      <th align="left">parent</th>
      <td>The parent object of this picture.</td>
    </tr>
</table>

## Response Example

```json
{
  "total_entries": 18,
  "offset": 3,
  "total_pages": 6,
  "current_page": 2,
  "per_page": 3,
  "data": [
    {
      "width": 132,
      "height": 99,
      "description": "Kids practice to jump at Mekroyan Fountain, Kabul",
      "created_at": "2012-07-23T12:25:15Z",
      "updated_at": "2012-07-23T12:29:41Z",
      "links": [
        {
          "rel": "image",
          "href": "/paperclip/000/286/511/original_skateistan%20print_37.jpg"
        },
        {
          "rel": "self",
          "href": "https://api.betterplace.org/en/api_v4/projects/1114/pictures/286511.json"
        },
        {
          "rel": "parent",
          "href": "https://api.betterplace.org/en/api_v4/projects/1114.json"
        }
      ]
    },
    {
      "width": 132,
      "height": 99,
      "description": "Afghan Skate Instructor Merza showing his skills at an old Soviet swimming pool on Bibi Maru Hill, Kabul",
      "created_at": "2012-07-23T12:30:13Z",
      "updated_at": "2012-07-23T12:34:05Z",
      "links": [
        {
          "rel": "image",
          "href": "/paperclip/000/286/512/original_wais%20ollies%20into%20the%20empty%20pool.jpg"
        },
        {
          "rel": "self",
          "href": "https://api.betterplace.org/en/api_v4/projects/1114/pictures/286512.json"
        },
        {
          "rel": "parent",
          "href": "https://api.betterplace.org/en/api_v4/projects/1114.json"
        }
      ]
    },
    {
      "width": 132,
      "height": 99,
      "created_at": "2012-07-23T12:45:29Z",
      "updated_at": "2012-07-23T12:45:30Z",
      "links": [
        {
          "rel": "image",
          "href": "/paperclip/000/286/515/original_IMG_1462.JPG"
        },
        {
          "rel": "self",
          "href": "https://api.betterplace.org/en/api_v4/projects/1114/pictures/286515.json"
        },
        {
          "rel": "parent",
          "href": "https://api.betterplace.org/en/api_v4/projects/1114.json"
        }
      ]
    }
  ]
}
```

