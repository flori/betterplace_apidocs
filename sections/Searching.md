
# Searching entities to donate to

```Cirru
GET https://api.betterplace.org/de/api_v4/search.json?bounds=52.6754542%2C13.7611175%2C52.338234%2C13.08834&q=Katze
```

TODO


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
    <td><code>Katze</code></td>
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
      <td><code></code></td>
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
  "total_entries": 337,
  "offset": 0,
  "total_pages": 113,
  "current_page": 1,
  "per_page": 3,
  "data": [
    {
      "id": 72206,
      "created_at": "2019-08-17T09:01:36+02:00",
      "updated_at": "2022-06-11T15:01:20+02:00",
      "latitude": 51.18564980000001,
      "longitude": 10.4207755,
      "title": "Tiere auf Lebenshof Gut Weidensee benötigen dringend Hilfe!",
      "type": "Project",
      "contact": {
        "id": 576646,
        "name": "Anisa Pietsch (display)",
        "picture": {
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://betterplace-assets.betterplace.org/uploads/user/profile_picture/000/576/646/fill_100x100_bp1584600717_Videoprint_37.jpg"
            },
            {
              "rel": "original",
              "href": "https://betterplace-assets.betterplace.org/uploads/user/profile_picture/000/576/646/crop_original_bp1584600717_Videoprint_37.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.org/de/users/576646"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/de/api_v4/users/576646/contact_data.json"
          }
        ]
      },
      "progress_percentage": 93,
      "profile_picture": {
        "links": [
          {
            "rel": "fill_960x500",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/072/206/fill_960x500_bp1651574817_DSC_2132.jpg"
          },
          {
            "rel": "fill_730x380",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/072/206/fill_730x380_bp1651574817_DSC_2132.jpg"
          },
          {
            "rel": "fill_618x322",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/072/206/fill_618x322_bp1651574817_DSC_2132.jpg"
          },
          {
            "rel": "fill_410x214",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/072/206/fill_410x214_bp1651574817_DSC_2132.jpg"
          },
          {
            "rel": "fill_270x141",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/072/206/fill_270x141_bp1651574817_DSC_2132.jpg"
          },
          {
            "rel": "original",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/072/206/crop_original_bp1651574817_DSC_2132.jpg"
          }
        ]
      },
      "donated_amount_in_cents": 39873906,
      "country": "Deutschland",
      "city": "Mühlhausen",
      "carrier": {
        "id": 38291,
        "name": "Lebenshof Gut Weidensee",
        "city": "Mühlhausen",
        "country": "Deutschland",
        "picture": {
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://betterplace-assets.betterplace.org/uploads/organisation/profile_picture/000/038/291/fill_100x100_bp1566147543_index.png"
            },
            {
              "rel": "original",
              "href": "https://betterplace-assets.betterplace.org/uploads/organisation/profile_picture/000/038/291/crop_original_bp1566147543_index.png"
            }
          ]
        },
        "links": [
          {
            "rel": "self",
            "href": "https://api.betterplace.org/de/api_v4/organisations/38291.json"
          }
        ]
      },
      "donations_count": 11060,
      "open_amount_in_cents": 2877694,
      "links": [
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/projects/72206-tiere-auf-lebenshof-gut-weidensee-benoetigen-dringend-hilfe"
        },
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/projects/72206.json"
        },
        {
          "rel": "pictures",
          "href": "https://api.betterplace.org/de/api_v4/projects/72206/pictures.json"
        }
      ]
    },
    {
      "id": 39455,
      "created_at": "2021-10-26T09:14:29+02:00",
      "updated_at": "2022-06-11T13:01:16+02:00",
      "title": "Hilfe für die Samtpfoten - Stream für die Arche",
      "type": "FundraisingEvent",
      "contact": {
        "id": 615002,
        "name": "Emil Mack (display)",
        "picture": {
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://betterplace-assets.betterplace.org/uploads/user/profile_picture/000/615/002/fill_100x100_bp1646242482_001_Benjamin.png"
            },
            {
              "rel": "original",
              "href": "https://betterplace-assets.betterplace.org/uploads/user/profile_picture/000/615/002/crop_original_bp1646242482_001_Benjamin.png"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.org/de/users/615002"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/de/api_v4/users/615002/contact_data.json"
          }
        ]
      },
      "progress_percentage": 0,
      "profile_picture": {
        "links": [
          {
            "rel": "fill_960x500",
            "href": "https://betterplace-assets.betterplace.org/uploads/fundraising_event/profile_picture/000/039/455/fill_960x500_bp1639043024_arche_kanaum_logo_v2-1_betterplace.png"
          },
          {
            "rel": "fill_730x380",
            "href": "https://betterplace-assets.betterplace.org/uploads/fundraising_event/profile_picture/000/039/455/fill_730x380_bp1639043024_arche_kanaum_logo_v2-1_betterplace.png"
          },
          {
            "rel": "fill_618x322",
            "href": "https://betterplace-assets.betterplace.org/uploads/fundraising_event/profile_picture/000/039/455/fill_618x322_bp1639043024_arche_kanaum_logo_v2-1_betterplace.png"
          },
          {
            "rel": "fill_410x214",
            "href": "https://betterplace-assets.betterplace.org/uploads/fundraising_event/profile_picture/000/039/455/fill_410x214_bp1639043024_arche_kanaum_logo_v2-1_betterplace.png"
          },
          {
            "rel": "fill_270x141",
            "href": "https://betterplace-assets.betterplace.org/uploads/fundraising_event/profile_picture/000/039/455/fill_270x141_bp1639043024_arche_kanaum_logo_v2-1_betterplace.png"
          },
          {
            "rel": "original",
            "href": "https://betterplace-assets.betterplace.org/uploads/fundraising_event/profile_picture/000/039/455/crop_original_bp1639043024_arche_kanaum_logo_v2-1_betterplace.png"
          }
        ]
      },
      "donated_amount_in_cents": 530500,
      "donations_count": 133,
      "links": [
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/fundraising-events/39455-hilfe-fuer-die-samtpfoten-stream-fuer-die-arche"
        },
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/fundraising_events/39455.json"
        },
        {
          "rel": "pictures",
          "href": "https://api.betterplace.org/de/api_v4/projects/39455/pictures.json"
        }
      ]
    },
    {
      "id": 11289,
      "created_at": "2012-10-30T21:20:22+01:00",
      "updated_at": "2022-06-11T00:02:08+02:00",
      "latitude": 52.3333333,
      "longitude": 12.35,
      "title": "Ein Monat Futter und Medikamente",
      "type": "Project",
      "contact": {
        "id": 283731,
        "name": "Jasmin Geyer (display)",
        "picture": {
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://betterplace-assets.betterplace.org/uploads/user/profile_picture/000/283/731/fill_100x100_bp1584574960_2.jpg"
            },
            {
              "rel": "original",
              "href": "https://betterplace-assets.betterplace.org/uploads/user/profile_picture/000/283/731/crop_original_bp1584574960_2.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.org/de/users/283731"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/de/api_v4/users/283731/contact_data.json"
          }
        ]
      },
      "progress_percentage": 99,
      "profile_picture": {
        "links": [
          {
            "rel": "fill_960x500",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/011/289/fill_960x500_bp1584534965_original_IMG_1129.JPG"
          },
          {
            "rel": "fill_730x380",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/011/289/fill_730x380_bp1584534965_original_IMG_1129.JPG"
          },
          {
            "rel": "fill_618x322",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/011/289/fill_618x322_bp1584534965_original_IMG_1129.JPG"
          },
          {
            "rel": "fill_410x214",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/011/289/fill_410x214_bp1584534965_original_IMG_1129.JPG"
          },
          {
            "rel": "fill_270x141",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/011/289/fill_270x141_bp1584534965_original_IMG_1129.JPG"
          },
          {
            "rel": "original",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/011/289/crop_original_bp1584534965_original_IMG_1129.JPG"
          }
        ]
      },
      "donated_amount_in_cents": 9641751,
      "country": "Deutschland",
      "city": "Rosenau",
      "carrier": {
        "id": 12201,
        "name": "Ein Zuhause für Tiere e. V.",
        "city": "Rosenau",
        "country": "Deutschland",
        "picture": {
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://betterplace-assets.betterplace.org/uploads/organisation/profile_picture/000/012/201/fill_100x100_bp1645803436_85766EB5-6DE4-4693-BA4B-C114E9564B22.jpeg"
            },
            {
              "rel": "original",
              "href": "https://betterplace-assets.betterplace.org/uploads/organisation/profile_picture/000/012/201/crop_original_bp1645803436_85766EB5-6DE4-4693-BA4B-C114E9564B22.jpeg"
            }
          ]
        },
        "links": [
          {
            "rel": "self",
            "href": "https://api.betterplace.org/de/api_v4/organisations/12201.json"
          }
        ]
      },
      "donations_count": 4593,
      "open_amount_in_cents": 84049,
      "links": [
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/projects/11289-ein-monat-futter-und-medikamente"
        },
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/projects/11289.json"
        },
        {
          "rel": "pictures",
          "href": "https://api.betterplace.org/de/api_v4/projects/11289/pictures.json"
        }
      ]
    }
  ]
}
```

