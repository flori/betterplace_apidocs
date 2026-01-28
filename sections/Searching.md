
# Searching entities to donate to

```Cirru
GET https://api.betterplace.org/de/api_v4/search.json?bounds=52.6754542%2C13.7611175%2C52.338234%2C13.08834&facets=state%3Aactivated&q=Berlin
```

This endpoint allows users to search for donation entities such as
projects and fundraising events. The search can be refined using various
parameters including full-text queries, geographic bounds, and facet filters.
The results are optimized for frontend display and include metadata necessary
for user interaction.

**Key Features:**
- Full-text search across entity titles, descriptions, and related fields.
- Geographic filtering to show entities within a specified bounding box.
- Facet-based filtering to narrow down results based on state, activity
  levels, and visibility.
- Pagination support for handling large result sets efficiently.

**Use Cases:**
- Users searching for donation opportunities in a specific geographic area.
- Nonprofits looking to discover active projects that meet certain criteria.

The endpoint is designed to handle high volumes of requests efficiently.


## URL Parameters

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <th align="left">q</th>
    <td><code>Berlin</code></td>
    <td>no</td>
<td>

Fulltext search query.

</td>
  </tr>
  <tr>
    <th align="left">bounds</th>
    <td><code>52.6754542,13.7611175,52.338234,13.08834</code></td>
    <td>no</td>
<td>

A string of four comma-seperated floating point geo coordinates in
range of -180…180 for <code>sw_lat,sw_lng,ne_lat,ne_lng</code>
describing a bounding box around the search results' geo coordinates.


</td>
  </tr>
  <tr>
    <th align="left">facets</th>
    <td><code>state:activated</code></td>
    <td>no</td>
<td>

Filter the result set.
<br>
It is strongly recommended to <strong>specify facets</strong> with each request.
A recommended set of facets is <code>state:activated| min_activity_threshold_reached:true|
hidden_from_platform:false</code> (without the spaces) which
only shows active projects and fundraising events that can receive donations.
<br>
<em>Supported filters are:</em>
<ul>
<li><code>state:activated</code> –For active projects and fundraising events
<li><code>min_activity_threshold_reached:true/false</code> Project has received some attention and donations
<li><code>hidden_from_platform:true/false</code> – Incomplete or blocked projects
</ul>
It is possible to set multiple facet filters.
<a href="../README.md#request-parameter-format">Learn how to format the parameter</a>.


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
      <th align="left">latitude</th>
      <td><code>number</code></td>
      <td><code>52.499007</code></td>
<td>

Decimal degrees based on user input

</td>
    </tr>
    <tr>
      <th align="left">longitude</th>
      <td><code>number</code></td>
      <td><code>13.44947</code></td>
<td>

Decimal degrees based on user input

</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="matching_events-ref" href="#matching_events">
            ↓matching_events
          </a>
        </th>
      <td><code>array</code></td>
      <td><code>TODO</code></td>
<td>

Data on matching events including this resource

</td>
    </tr>
    <tr>
      <th align="left">title</th>
      <td><code>string</code></td>
      <td><code>Katzenspass</code></td>
<td>

Name of the entity

</td>
    </tr>
    <tr>
      <th align="left">type</th>
      <td><code>string</code></td>
      <td><code>Project</code></td>
<td>

Type of the entity, either Project or FundraisingEvent

</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="contact-ref" href="#contact">
            ↓contact
          </a>
        </th>
      <td><code>object</code></td>
      <td><code>TODO</code></td>
<td>

The public face of this entity

</td>
    </tr>
    <tr>
      <th align="left">progress_percentage</th>
      <td><code>number</code></td>
      <td><code>82</code></td>
<td>

% financed.


</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="profile_picture-ref" href="#profile_picture">
            ↓profile_picture
          </a>
        </th>
      <td><code>null &#124; object</code></td>
      <td><code>//betterplace-assets.betterplace.org ↪/uploads/user/profile_picture ↪/000/000/001 ↪/fill_100x100_original_tb.jpg</code></td>
<td>

TODO

</td>
    </tr>
    <tr>
      <th align="left">donated_amount_in_cents</th>
      <td><code>number</code></td>
      <td><code>232323</code></td>
<td>

How many cents were already raised with the fundraising event

</td>
    </tr>
    <tr>
      <th align="left">country</th>
      <td><code>null &#124; string</code></td>
      <td><code>Berlin</code></td>
<td>

Name where this entity is located

</td>
    </tr>
    <tr>
      <th align="left">city</th>
      <td><code>null &#124; string</code></td>
      <td><code>Berlin</code></td>
<td>

Name where this entity is located

</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="carrier-ref" href="#carrier">
            ↓carrier
          </a>
        </th>
      <td><code>null &#124; object</code></td>
      <td><code>TODO</code></td>
<td>

The organisation that carries this project

</td>
    </tr>
    <tr>
      <th align="left">donations_count</th>
      <td><code>number</code></td>
      <td><code>42</code></td>
<td>

Count of confirmed donations for this entity

</td>
    </tr>
    <tr>
      <th align="left">open_amount_in_cents</th>
      <td><code>number</code></td>
      <td><code>12382</code></td>
<td>

How many cents are needed to complete the project

</td>
    </tr>
  </table>

### <a id="matching_events" href="#matching_events-ref">↑Nested Attributes: matching_events</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">matching_events.id</th>
      <td><code>number</code></td>
      <td><code>1</code></td>
<td>

An integer number ≥ 1

</td>
    </tr>
    <tr>
      <th align="left">matching_events.matching_percentage</th>
      <td><code>number</code></td>
      <td><code>25.0</code></td>
<td>

A number greater than 0.01

</td>
    </tr>
    <tr>
      <th align="left">matching_events.banner_background_color</th>
      <td><code>string</code></td>
      <td><code>#F6CE46</code></td>
<td>

The HEX representation of the banner's background color

</td>
    </tr>
    <tr>
      <th align="left">matching_events.banner_text_color</th>
      <td><code>string</code></td>
      <td><code>#282828</code></td>
<td>

The HEX representation of the banner's color

</td>
    </tr>
  </table>

### <a id="contact" href="#contact-ref">↑Nested Attributes: contact</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">contact.id</th>
      <td><code>number</code></td>
      <td><code>1</code></td>
<td>

An integer number ≥ 1

</td>
    </tr>
    <tr>
      <th align="left">contact.name</th>
      <td><code>null &#124; string</code></td>
      <td><code>"Till B."</code></td>
<td>

Display name of a betterplace.org user.
Possible formats: "Till B.", "T. Behnke", "Till Behnke".

In the case of donation-opinions the name might also be
empty/null for anonymous donations for anonymous donations.


</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="contact.picture-ref" href="#contact.picture">
            ↓contact.picture
          </a>
        </th>
      <td><code>object</code></td>
      <td><code>//betterplace-assets.betterplace.org ↪/uploads/user/profile_picture ↪/000/000/001 ↪/fill_100x100_original_tb.jpg</code></td>
<td>

User profile picture or a fallback image

</td>
    </tr>
  </table>

### <a id="contact.picture" href="#contact.picture-ref">↑Nested Attributes: contact.picture</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">contact.picture.fallback</th>
      <td><code>boolean</code></td>
      <td><code>true</code></td>
<td>

Specifies whether a fallback image is given or not

</td>
    </tr>
  </table>

### <a id="profile_picture" href="#profile_picture-ref">↑Nested Attributes: profile_picture</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">profile_picture.fallback</th>
      <td><code>boolean</code></td>
      <td><code>true</code></td>
<td>

Specifies whether a fallback image is given or not

</td>
    </tr>
  </table>

### <a id="carrier" href="#carrier-ref">↑Nested Attributes: carrier</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">carrier.id</th>
      <td><code>number</code></td>
      <td><code>1</code></td>
<td>

An integer number ≥ 1

</td>
    </tr>
    <tr>
      <th align="left">carrier.name</th>
      <td><code>string</code></td>
      <td><code>"Till B."</code></td>
<td>

The carrier can be an organisation or user.

</td>
    </tr>
    <tr>
      <th align="left">carrier.city</th>
      <td><code>string</code></td>
      <td><code>"Berlin"</code></td>
<td>

The city in which the carrier resides

</td>
    </tr>
    <tr>
      <th align="left">carrier.country</th>
      <td><code>string</code></td>
      <td><code>"Deutschland"</code></td>
<td>

The country in which the carrier resides

</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="carrier.picture-ref" href="#carrier.picture">
            ↓carrier.picture
          </a>
        </th>
      <td><code>object</code></td>
      <td><code></code></td>
<td>

The organisation logo, user profile picture or a fallback image

</td>
    </tr>
  </table>

### <a id="carrier.picture" href="#carrier.picture-ref">↑Nested Attributes: carrier.picture</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">carrier.picture.fallback</th>
      <td><code>boolean</code></td>
      <td><code>true</code></td>
<td>

Specifies whether a fallback image is given or not

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

platform

</th>
<td>

Permalink to betterplace.org

</td>
    </tr>
    <tr>
<th align="left">

self

</th>
<td>

Link to this resource itself


</td>
    </tr>
    <tr>
<th align="left">

pictures

</th>
<td>

Link to <a href="project_pictures_list.md">project pictures list</a>


</td>
    </tr>
    <tr>
<th align="left">

contact.platform

</th>
<td>

The user's profile on betterplace.org.
To view a user profile you have to be logged in.
This array is empty if the user has no useraccount
with betterplace.org but donated via one of our partner.


</td>
    </tr>
    <tr>
<th align="left">

contact.contact_data

</th>
<td>

The user's contact data. Please note that you need to be
<a href="../README.md#client-api">authenticated as a client</a> with matching
access rights in order to see this information.


</td>
    </tr>
    <tr>
<th align="left">

contact.picture.fill_100x100

</th>
<td>

100×100 Pixel

</td>
    </tr>
    <tr>
<th align="left">

contact.picture.original

</th>
<td>

Maximum sized image. This is the original image with default-cropping or user-cropping applied.

</td>
    </tr>
    <tr>
<th align="left">

profile_picture.fill_960x500

</th>
<td>

950×500 Pixel

</td>
    </tr>
    <tr>
<th align="left">

profile_picture.fill_730x380

</th>
<td>

730×380 Pixel

</td>
    </tr>
    <tr>
<th align="left">

profile_picture.fill_618x322

</th>
<td>

618×322 Pixel / DEPRECATED, will be removed after 5/2015

</td>
    </tr>
    <tr>
<th align="left">

profile_picture.fill_410x214

</th>
<td>

410×214 Pixel

</td>
    </tr>
    <tr>
<th align="left">

profile_picture.fill_270x141

</th>
<td>

270×141 Pixel / DEPRECATED, will be removed after 5/2015

</td>
    </tr>
    <tr>
<th align="left">

profile_picture.original

</th>
<td>

Maximum sized image. This is the original image with default-cropping or user-cropping applied.

</td>
    </tr>
    <tr>
<th align="left">

carrier.self

</th>
<td>

Link to this resource itself
(<a href="organisation_details.md">organisation details</a>)
Note: Since the there is no api for users yet, this is only
set for organisations.


</td>
    </tr>
    <tr>
<th align="left">

carrier.picture.fill_100x100

</th>
<td>

100×100 Pixel

</td>
    </tr>
    <tr>
<th align="left">

carrier.picture.original

</th>
<td>

Maximum sized image. This is the original image with default-cropping or user-cropping applied.

</td>
    </tr>
</table>

## Response Example

```json
{
  "current_page": 1,
  "offset": 0,
  "per_page": 3,
  "total_entries": 6,
  "total_pages": 2,
  "data": [
    {
      "id": 1,
      "created_at": "2025-11-10T12:29:10+01:00",
      "updated_at": "2025-11-10T13:00:03+01:00",
      "latitude": 52.49000000000001,
      "longitude": 13.45,
      "matching_events": [
        {
          "id": 1,
          "matching_percentage": 50.0,
          "banner_background_color": "#F6CE46",
          "banner_text_color": "#282828",
          "links": []
        }
      ],
      "title": "Project - my little project",
      "type": "Project",
      "contact": {
        "id": 1,
        "name": "u. X",
        "picture": {
          "fallback": true,
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://betterplace-assets.betterplace.org/assets/default/user_profile_picture/default.svg"
            },
            {
              "rel": "original",
              "href": "https://betterplace-assets.betterplace.org/assets/default/user_profile_picture/default.svg"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.dev/de/users/1"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.dev/de/api_v4/users/1/contact_data.json"
          }
        ]
      },
      "progress_percentage": 63,
      "profile_picture": {
        "fallback": true,
        "links": [
          {
            "rel": "fill_960x500",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/001/fill_960x500_9b11ca4f-e294-4d3b-b0db-2f4277d6f822.jpg"
          },
          {
            "rel": "fill_730x380",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/001/fill_730x380_9b11ca4f-e294-4d3b-b0db-2f4277d6f822.jpg"
          },
          {
            "rel": "fill_618x322",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/001/fill_618x322_9b11ca4f-e294-4d3b-b0db-2f4277d6f822.jpg"
          },
          {
            "rel": "fill_410x214",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/001/fill_410x214_9b11ca4f-e294-4d3b-b0db-2f4277d6f822.jpg"
          },
          {
            "rel": "fill_270x141",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/001/fill_270x141_9b11ca4f-e294-4d3b-b0db-2f4277d6f822.jpg"
          },
          {
            "rel": "original",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/001/crop_original_9b11ca4f-e294-4d3b-b0db-2f4277d6f822.jpg"
          }
        ]
      },
      "donated_amount_in_cents": 510000,
      "country": "Deutschland",
      "city": "Berlin",
      "carrier": {
        "id": 1,
        "name": "Organisation #1",
        "city": "Berlin",
        "country": "Deutschland",
        "picture": {
          "fallback": true,
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://betterplace-assets.betterplace.org/assets/default/square_profile_picture/fill_100x100_default.jpg"
            },
            {
              "rel": "original",
              "href": "https://betterplace-assets.betterplace.org/assets/default/square_profile_picture/crop_original_default.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "self",
            "href": "https://api.betterplace.dev/de/api_v4/organisations/1.json"
          }
        ]
      },
      "donations_count": 11,
      "open_amount_in_cents": 290100,
      "links": [
        {
          "rel": "platform",
          "href": "https://www.betterplace.dev/de/projects/1-project-my-little-project"
        },
        {
          "rel": "self",
          "href": "https://api.betterplace.dev/de/api_v4/projects/1.json"
        },
        {
          "rel": "pictures",
          "href": "https://api.betterplace.dev/de/api_v4/projects/1/pictures.json"
        }
      ]
    },
    {
      "id": 8,
      "created_at": "2025-11-10T12:29:25+01:00",
      "updated_at": "2025-11-10T13:00:03+01:00",
      "latitude": 52.49000000000001,
      "longitude": 13.45,
      "matching_events": [],
      "title": "Project - Some other little project",
      "type": "Project",
      "contact": {
        "id": 1,
        "name": "u. X",
        "picture": {
          "fallback": true,
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://betterplace-assets.betterplace.org/assets/default/user_profile_picture/default.svg"
            },
            {
              "rel": "original",
              "href": "https://betterplace-assets.betterplace.org/assets/default/user_profile_picture/default.svg"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.dev/de/users/1"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.dev/de/api_v4/users/1/contact_data.json"
          }
        ]
      },
      "progress_percentage": 12,
      "profile_picture": {
        "fallback": true,
        "links": [
          {
            "rel": "fill_960x500",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/008/fill_960x500_aef2413c-e7f6-4c04-9958-ecd4f1da41ad.jpg"
          },
          {
            "rel": "fill_730x380",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/008/fill_730x380_aef2413c-e7f6-4c04-9958-ecd4f1da41ad.jpg"
          },
          {
            "rel": "fill_618x322",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/008/fill_618x322_aef2413c-e7f6-4c04-9958-ecd4f1da41ad.jpg"
          },
          {
            "rel": "fill_410x214",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/008/fill_410x214_aef2413c-e7f6-4c04-9958-ecd4f1da41ad.jpg"
          },
          {
            "rel": "fill_270x141",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/008/fill_270x141_aef2413c-e7f6-4c04-9958-ecd4f1da41ad.jpg"
          },
          {
            "rel": "original",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/008/crop_original_aef2413c-e7f6-4c04-9958-ecd4f1da41ad.jpg"
          }
        ]
      },
      "donated_amount_in_cents": 50000,
      "country": "Deutschland",
      "city": "Berlin",
      "carrier": {
        "id": 1,
        "name": "Organisation #1",
        "city": "Berlin",
        "country": "Deutschland",
        "picture": {
          "fallback": true,
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://betterplace-assets.betterplace.org/assets/default/square_profile_picture/fill_100x100_default.jpg"
            },
            {
              "rel": "original",
              "href": "https://betterplace-assets.betterplace.org/assets/default/square_profile_picture/crop_original_default.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "self",
            "href": "https://api.betterplace.dev/de/api_v4/organisations/1.json"
          }
        ]
      },
      "donations_count": 2,
      "open_amount_in_cents": 350000,
      "links": [
        {
          "rel": "platform",
          "href": "https://www.betterplace.dev/de/projects/8-project-some-other-little-project"
        },
        {
          "rel": "self",
          "href": "https://api.betterplace.dev/de/api_v4/projects/8.json"
        },
        {
          "rel": "pictures",
          "href": "https://api.betterplace.dev/de/api_v4/projects/8/pictures.json"
        }
      ]
    },
    {
      "id": 5,
      "created_at": "2025-11-10T12:29:19+01:00",
      "updated_at": "2025-11-10T12:29:27+01:00",
      "latitude": 52.49000000000001,
      "longitude": 13.45,
      "matching_events": [],
      "title": "Project - Project with 0 donations",
      "type": "Project",
      "contact": {
        "id": 1,
        "name": "u. X",
        "picture": {
          "fallback": true,
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://betterplace-assets.betterplace.org/assets/default/user_profile_picture/default.svg"
            },
            {
              "rel": "original",
              "href": "https://betterplace-assets.betterplace.org/assets/default/user_profile_picture/default.svg"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.dev/de/users/1"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.dev/de/api_v4/users/1/contact_data.json"
          }
        ]
      },
      "progress_percentage": 0,
      "profile_picture": {
        "fallback": true,
        "links": [
          {
            "rel": "fill_960x500",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/005/fill_960x500_45c63a27-4971-4c8b-9a39-2ad7ae3578ea.jpg"
          },
          {
            "rel": "fill_730x380",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/005/fill_730x380_45c63a27-4971-4c8b-9a39-2ad7ae3578ea.jpg"
          },
          {
            "rel": "fill_618x322",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/005/fill_618x322_45c63a27-4971-4c8b-9a39-2ad7ae3578ea.jpg"
          },
          {
            "rel": "fill_410x214",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/005/fill_410x214_45c63a27-4971-4c8b-9a39-2ad7ae3578ea.jpg"
          },
          {
            "rel": "fill_270x141",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/005/fill_270x141_45c63a27-4971-4c8b-9a39-2ad7ae3578ea.jpg"
          },
          {
            "rel": "original",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/000/005/crop_original_45c63a27-4971-4c8b-9a39-2ad7ae3578ea.jpg"
          }
        ]
      },
      "donated_amount_in_cents": 0,
      "country": "Deutschland",
      "city": "Berlin",
      "carrier": {
        "id": 1,
        "name": "Organisation #1",
        "city": "Berlin",
        "country": "Deutschland",
        "picture": {
          "fallback": true,
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://betterplace-assets.betterplace.org/assets/default/square_profile_picture/fill_100x100_default.jpg"
            },
            {
              "rel": "original",
              "href": "https://betterplace-assets.betterplace.org/assets/default/square_profile_picture/crop_original_default.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "self",
            "href": "https://api.betterplace.dev/de/api_v4/organisations/1.json"
          }
        ]
      },
      "donations_count": 0,
      "open_amount_in_cents": 100000,
      "links": [
        {
          "rel": "platform",
          "href": "https://www.betterplace.dev/de/projects/5-project-project-with-0-donations"
        },
        {
          "rel": "self",
          "href": "https://api.betterplace.dev/de/api_v4/projects/5.json"
        },
        {
          "rel": "pictures",
          "href": "https://api.betterplace.dev/de/api_v4/projects/5/pictures.json"
        }
      ]
    }
  ]
}
```

