
# Organisations List ⇄ [Details](organisation_details.md)

```nginx
GET https://api.betterplace.org/en/api_v4/organisations.json
```

A list of betterplace.org organisations.
Results are contained in a *data* attribute.
The details and list view show the same data per organisation.

*For [betterplace.org clients](../README.md#client-api):*
This resource is not avaliable at the moment.


## Input Parameter

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Required/Optional</th>
    <th>Description</th>
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
      <td>number</td>
      <td>4</td>
      <td>An integer number ≥ 1</td>
    </tr>
    <tr>
      <th align="left">slug</th>
      <td>string</td>
      <td>vivaconagua</td>
      <td><a href="http://en.wikipedia.org/wiki/Clean_URL#Slug">URL slug</a>
for the permalink
</td>
    </tr>
    <tr>
      <th align="left">created_at</th>
      <td>string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone)</td>
    </tr>
    <tr>
      <th align="left">updated_at</th>
      <td>string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone)</td>
    </tr>
    <tr>
      <th align="left">latitude</th>
      <td>number</td>
      <td>52.499007</td>
      <td>Decimal degrees based on user input</td>
    </tr>
    <tr>
      <th align="left">longitude</th>
      <td>number</td>
      <td>13.44947</td>
      <td>Decimal degrees based on user input</td>
    </tr>
    <tr>
      <th align="left">street</th>
      <td>null &#124; string</td>
      <td>"Schlesische Straße 26"</td>
      <td>Address of the organisation</td>
    </tr>
    <tr>
      <th align="left">zip</th>
      <td>null &#124; string</td>
      <td>"10997"</td>
      <td>Address of the organisation</td>
    </tr>
    <tr>
      <th align="left">city</th>
      <td>null &#124; string</td>
      <td>"Berlin"</td>
      <td>Address of the organisation</td>
    </tr>
    <tr>
      <th align="left">country</th>
      <td>null &#124; string</td>
      <td>"Deutschland"</td>
      <td>Address of the organisation, translated to the requested language</td>
    </tr>
    <tr>
      <th align="left">name</th>
      <td>string</td>
      <td>"Viva con Agua de Sankt Pauli e.V."</td>
      <td>Name of the organisation</td>
    </tr>
    <tr>
      <th align="left">description</th>
      <td>string</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <th align="left">tax_deductible</th>
      <td>boolean</td>
      <td>true</td>
      <td>True if the organisation is a tax-exempt charity.
If so, Users can request a tax-receipt for donations to that organisation.
[More about this](http://www.betterplace.org/c/hilfe/projekt-steuerlich-absetzbar/).
</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a name="contact-ref" href="#contact">
            ↓contact
          </a>
        </th>
      <td>object</td>
      <td></td>
      <td>The public contact person for this organisation.</td>
    </tr>
    <tr>
      <th align="left">picture</th>
      <td>null &#124; object</td>
      <td></td>
      <td>TODO</td>
    </tr>
  </table>
### <a name="contact" href="#contact-ref">↑Nested Attributes: contact</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">contact.name</th>
      <td>null &#124; string</td>
      <td>"Till B."</td>
      <td>Display name of a betterplace.org user.
Possible formats: "Till B.", "T. Behnke", "Till Behnke".
In the case of donation-opinions the name might also be anonymized
like "Payback User" or empty/null for anonymous donations.
</td>
    </tr>
    <tr>
      <th align="left">contact.picture</th>
      <td>string</td>
      <td>//assets.betterplace.org/…</td>
      <td>User profile picture or a fallback image</td>
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
      <th align="left">self</th>
      <td>Link to this resource itself
(<a href="organisation_details.md">organisation details</a>)
</td>
    </tr>
    <tr>
      <th align="left">platform</th>
      <td>Permalink to betterplace.org</td>
    </tr>
    <tr>
      <th align="left">projects</th>
      <td>Link to the <a href="projects_list.md">project list</a> of this organisation
</td>
    </tr>
    <tr>
      <th align="left">website</th>
      <td>Link to the website of this organisation.</td>
    </tr>
    <tr>
      <th align="left">contact.platform</th>
      <td>The user's profile on betterplace.org.
To view a user profile you have to be logged in.
This array is empty if the user has no useraccount
with betterplace.org but donated via one of our partner.
</td>
    </tr>
    <tr>
      <th align="left">contact.contact_data</th>
      <td>The user's contact data. Please note that you need to be
<a href="../README.md#client-authentication">authenticated as a client</a> with matching
access rights in order to see this information.
</td>
    </tr>
    <tr>
      <th align="left">contact.picture.fill_100x100</th>
      <td>100x100 Pixel</td>
    </tr>
    <tr>
      <th align="left">contact.picture.original</th>
      <td>Maximum sized image. This is the original image with default-cropping or user-cropping applied.</td>
    </tr>
    <tr>
      <th align="left">picture.fill_100x100</th>
      <td>100x100 Pixel</td>
    </tr>
    <tr>
      <th align="left">picture.fill_200x200</th>
      <td>200x200 Pixel</td>
    </tr>
    <tr>
      <th align="left">picture.fill_400x400</th>
      <td>400x400 Pixel</td>
    </tr>
    <tr>
      <th align="left">picture.original</th>
      <td>Maximum sized image. This is the original image with default-cropping or user-cropping applied.</td>
    </tr>
</table>

## Response Example

```json
{
  "total_entries": 9250,
  "offset": 0,
  "total_pages": 4625,
  "current_page": 1,
  "per_page": 2,
  "data": [
    {
      "id": 7816,
      "slug": "---",
      "created_at": "2011-07-05T19:25:52Z",
      "updated_at": "2013-05-17T12:29:15Z",
      "latitude": 50.12379837036133,
      "longitude": 8.68529987335205,
      "street": "Adlerflycht Str. 8",
      "zip": "60138",
      "city": "Frankfurt amain",
      "country": "Germany",
      "name": "Individual and I work in close connetion with WRI",
      "description": "I live in Germany since 2001 as a political refugee from Eritrea. But now I am German citzen.  I studied Law in Eritrea and The Netherlands. I am a candidate for a PHD in Frankfurt Universty.  \r\nI am a member of human right organization in Germany and council member of War Resisters' International since 2010. \r\nI am a co.cordinator of Eritrean Antimilitarist Initiative (EAI) in 2005.",
      "tax_deductible": false,
      "contact": {
        "name": "A. Mehreteab",
        "picture": {
          "links": [
            {
              "rel": "fill_100x100",
              "href": "http://asset1.betterplace.org/assets/default/user_profile_picture/fill_100x100_default.betterplace.jpg"
            },
            {
              "rel": "original",
              "href": "http://asset1.betterplace.org/assets/default/user_profile_picture/fill_100x100_default.betterplace.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.org/en/users/abraham_m"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/en/api_v4/users/190955/contact_data.json"
          }
        ]
      },
      "picture": {
        "links": [
          {
            "rel": "fill_100x100",
            "href": "http://asset1.betterplace.org/assets/default/square_profile_picture/fill_100x100_default.betterplace.jpg"
          },
          {
            "rel": "fill_200x200",
            "href": "http://asset1.betterplace.org/assets/default/square_profile_picture/fill_200x200_default.betterplace.jpg"
          },
          {
            "rel": "fill_400x400",
            "href": "http://asset1.betterplace.org/assets/default/square_profile_picture/fill_400x400_default.betterplace.jpg"
          },
          {
            "rel": "original",
            "href": "http://asset1.betterplace.org/assets/default/square_profile_picture/crop_original_default.betterplace.jpg"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/en/api_v4/organisations/7816.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/en/organisations/---"
        },
        {
          "rel": "projects",
          "href": "https://api.betterplace.org/en/api_v4/organisations/7816/projects.json"
        },
        {
          "rel": "website",
          "href": "http://-----"
        }
      ]
    },
    {
      "id": 10120,
      "slug": "--------------------",
      "created_at": "2012-03-12T11:00:49Z",
      "updated_at": "2013-09-12T20:38:00Z",
      "latitude": -0.28333330154419,
      "longitude": 36.06666564941406,
      "street": "Nakuru,Kenya",
      "zip": null,
      "city": "Nakuru",
      "country": "Kenya",
      "name": "AMAZING GRACE CHILDREN HOME NAKURU,KENYA",
      "description": null,
      "tax_deductible": false,
      "contact": {
        "name": "A. Children Home",
        "picture": {
          "links": [
            {
              "rel": "fill_100x100",
              "href": "http://asset1.betterplace.org/uploads/user/profile_picture/000/249/795/fill_100x100_original_alim3111.jpg"
            },
            {
              "rel": "original",
              "href": "http://asset1.betterplace.org/uploads/user/profile_picture/000/249/795/crop_original_original_alim3111.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.org/en/users/amazing_c"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/en/api_v4/users/249795/contact_data.json"
          }
        ]
      },
      "picture": {
        "links": [
          {
            "rel": "fill_100x100",
            "href": "http://asset1.betterplace.org/uploads/organisation/profile_picture/000/010/120/fill_100x100_profile_thumb_ALIM5576.png"
          },
          {
            "rel": "fill_200x200",
            "href": "http://asset1.betterplace.org/uploads/organisation/profile_picture/000/010/120/fill_200x200_profile_thumb_ALIM5576.png"
          },
          {
            "rel": "fill_400x400",
            "href": "http://asset1.betterplace.org/uploads/organisation/profile_picture/000/010/120/fill_400x400_profile_thumb_ALIM5576.png"
          },
          {
            "rel": "original",
            "href": "http://asset1.betterplace.org/uploads/organisation/profile_picture/000/010/120/crop_original_profile_thumb_ALIM5576.png"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/en/api_v4/organisations/10120.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/en/organisations/--------------------"
        },
        {
          "rel": "projects",
          "href": "https://api.betterplace.org/en/api_v4/organisations/10120/projects.json"
        },
        {
          "rel": "website",
          "href": "http://www.amazinggracechildrenhome.org"
        }
      ]
    }
  ]
}
```

