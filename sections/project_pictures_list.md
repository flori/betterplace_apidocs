
# Project Pictures List ⇄ [Details](project_picture_details.md)

```Cirru
GET https://api.betterplace.org/de/api_v4/projects/3/pictures.json
```

A list of pictures of a betterplace.org project (donate money).
Results are contained in a *data* attribute.

*Custom picture-sizes:* This API will only deliver the original image.
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
    <td><code>3</code></td>
    <td>yes</td>
<td>

Project id as an integer number.

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

limit_620x323

</th>
<td>

Link to a small version (max 620x323 px) of the image

</td>
    </tr>
    <tr>
<th align="left">

limit_620x323_2x

</th>
<td>

Link to a small version (max 620x323 px) of the image @2x

</td>
    </tr>
    <tr>
<th align="left">

limit_450x235

</th>
<td>

Link to a small version (max 450x235 px) of the image

</td>
    </tr>
    <tr>
<th align="left">

limit_450x235_2x

</th>
<td>

Link to a small version (max 450x235 px) of the image @2x

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
  "current_page": 1,
  "offset": 0,
  "per_page": 3,
  "total_entries": 1,
  "total_pages": 1,
  "data": [
    {
      "id": 1,
      "created_at": "2025-06-26T13:12:11+02:00",
      "updated_at": "2025-06-26T13:12:11+02:00",
      "description": null,
      "links": [
        {
          "rel": "image",
          "href": ""
        },
        {
          "rel": "limit_620x323",
          "href": "https://betterplace-assets.betterplace.org/uploads/project/image/000/000/003/1/limit_620x323_image.jpg"
        },
        {
          "rel": "limit_620x323_2x",
          "href": "https://betterplace-assets.betterplace.org/uploads/project/image/000/000/003/1/limit_620x323_2x_image.jpg"
        },
        {
          "rel": "limit_450x235",
          "href": "https://betterplace-assets.betterplace.org/uploads/project/image/000/000/003/1/limit_450x235_image.jpg"
        },
        {
          "rel": "limit_450x235_2x",
          "href": "https://betterplace-assets.betterplace.org/uploads/project/image/000/000/003/1/limit_450x235_2x_image.jpg"
        },
        {
          "rel": "self",
          "href": "https://api.betterplace.dev/de/api_v4/projects/3/pictures/1.json"
        },
        {
          "rel": "parent",
          "href": "https://api.betterplace.dev/de/api_v4/projects/3.json"
        }
      ]
    }
  ]
}
```

