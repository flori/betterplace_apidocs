
# Project Pictures List ⇄ [Details](project_picture_details.md)

```Cirru
GET https://api.betterplace.org/de/api_v4/projects/1114/pictures.json
```

A list of pictures of a betterplace.org project (donate money).
Results are contained in a *data* attribute.

*Custom picture-sizes:* This API will only deliver the orginal image.
That is the largest image betterplace.org can provide.
Please use an image transformation service of your choice to resize this
image to your liking. Note, however, that some image names contain
non-url-safe characters that might break services such as Sencha Source.

We are working on a better solution. Please contact us for more information.

In the meantime, the following links might help:

* [Sencha Source](http://docs.sencha.io/current/index.html#!/guide/src) provides a simple URL-based solution
* [adaptive-images.com](http://adaptive-images.com/) is a self-hosted solution
* [Google mod_pagespeed "image resizing"](https://developers.google.com/speed/docs/mod_pagespeed/filter-image-optimize)
  should also help – and give you more performance goodies as well

**For [betterplace.org clients](../README.md#client-api):**
If you request data for a project that is not part of the client
projects, the API will return a `404` HTTP code.


## URL Parameters

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <th align="left">project_id</th>
    <td><code>1114</code></td>
    <td>yes</td>
<td>

Project id as an integer number ≥ 14.

</td>
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
      <th align="left">id</th>
      <td><code>number</code></td>
      <td><code>1</code></td>
<td>

An integer number ≥ 1

</td>
    </tr>
    <tr>
      <th align="left">created_at</th>
      <td><code>string</code></td>
      <td><code>"1994-11-05T13:15:30Z"</code></td>
<td>

DateTime (ISO8601 with Timezone)

</td>
    </tr>
    <tr>
      <th align="left">updated_at</th>
      <td><code>string</code></td>
      <td><code>"1994-11-05T13:15:30Z"</code></td>
<td>

DateTime (ISO8601 with Timezone)

</td>
    </tr>
    <tr>
      <th align="left">description</th>
      <td><code>string</code></td>
      <td><code>Yada…</code></td>
<td>

Description of the picture

</td>
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
<th align="left">

image

</th>
<td>

Link to the original image as uploaded by the user

</td>
    </tr>
    <tr>
<th align="left">

self

</th>
<td>

The single resource for this picture

</td>
    </tr>
    <tr>
<th align="left">

parent

</th>
<td>

The parent object of this picture.

</td>
    </tr>
</table>

## Response Example

```json
{
  "total_entries": 32,
  "offset": 3,
  "total_pages": 11,
  "current_page": 2,
  "per_page": 3,
  "data": [
    {
      "id": 230394,
      "created_at": "2020-07-02T09:36:14+02:00",
      "updated_at": "2020-11-19T12:22:38+01:00",
      "description": null,
      "links": [
        {
          "rel": "image",
          "href": "https://betterplace-assets.betterplace.org/uploads/project/image/000/001/114/230394/image.png"
        },
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114/pictures/230394.json"
        },
        {
          "rel": "parent",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114.json"
        }
      ]
    },
    {
      "id": 230396,
      "created_at": "2020-07-02T09:38:02+02:00",
      "updated_at": "2020-11-19T12:22:38+01:00",
      "description": null,
      "links": [
        {
          "rel": "image",
          "href": "https://betterplace-assets.betterplace.org/uploads/project/image/000/001/114/230396/image.jpg"
        },
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114/pictures/230396.json"
        },
        {
          "rel": "parent",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114.json"
        }
      ]
    },
    {
      "id": 230397,
      "created_at": "2020-07-02T09:38:32+02:00",
      "updated_at": "2020-11-19T12:22:38+01:00",
      "description": null,
      "links": [
        {
          "rel": "image",
          "href": "https://betterplace-assets.betterplace.org/uploads/project/image/000/001/114/230397/image.png"
        },
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114/pictures/230397.json"
        },
        {
          "rel": "parent",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114.json"
        }
      ]
    }
  ]
}
```

