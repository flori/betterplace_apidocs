
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
#### Links
  <table>
    <tr>
      <th>Linkname</th>
      <th colspan="3">Description</th>
    </tr>
    <tr>
      <th align="left">original</th>
      <td colspan="3">Original size as uploaded by the user</td>
    </tr>
    <tr>
      <th align="left">large_attention_deprecated</th>
      <td colspan="3">Large size – ATTENTION, this feature is DEPRECATED and will be removed at the end of may 2013. Please use the orginal format. Read the project pictures-documentation at "custom image sizes" for other solutions"</td>
    </tr>
    <tr>
      <th align="left">profile_attention_deprecated</th>
      <td colspan="3">Medium size – ATTENTION, this feature is DEPRECATED. See above.</td>
    </tr>
    <tr>
      <th align="left">thumb_attention_deprecated</th>
      <td colspan="3">Thumbnail size – ATTENTION, this feature is DEPRECATED. See above.</td>
    </tr>
  </table>
</table>

## Response Example

```json
{
  "total_entries": 8648,
  "offset": 0,
  "total_pages": 4324,
  "current_page": 1,
  "per_page": 2,
  "data": [
    {
      "id": 14,
      "slug": "mellemfolkeligtsamvirke",
      "created_at": "2007-07-03T11:54:42Z",
      "updated_at": "2013-09-23T17:09:15Z",
      "latitude": 55.68310165405273,
      "longitude": 12.5846996307373,
      "street": "Borgergade 14",
      "zip": "1300",
      "city": "Copenhagen",
      "country": "Denmark",
      "name": "Mellemfolkeligt Samvirke",
      "description": "Danish humanitarian organization promoting global democracy and fair trade since 1944.",
      "tax_deductible": false,
      "contact": {
        "name": "Jeppe Bo P.",
        "picture": {
          "links": [
            {
              "rel": "original",
              "href": "/paperclip/000/001/032/original_tegning-2.jpg"
            },
            {
              "rel": "large_attention_deprecated",
              "href": "/paperclip/000/001/032/default_tegning-2.jpg"
            },
            {
              "rel": "profile_attention_deprecated",
              "href": "/paperclip/000/001/032/profile_tegning-2.jpg"
            },
            {
              "rel": "thumb_attention_deprecated",
              "href": "/paperclip/000/001/032/thumb_tegning-2.png"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "http://www.betterplace.org/en/users/jeppe_p"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/en/api_v4/users/17/contact_data.json"
          }
        ]
      },
      "picture": {
        "links": [
          {
            "rel": "original",
            "href": "/uploads/organisation/profile_picture/14/original_original_logo_black.gif"
          },
          {
            "rel": "large_attention_deprecated",
            "href": "/uploads/organisation/profile_picture/14/default_original_logo_black.gif"
          },
          {
            "rel": "profile_attention_deprecated",
            "href": "/uploads/organisation/profile_picture/14/profile_original_logo_black.gif"
          },
          {
            "rel": "thumb_attention_deprecated",
            "href": "/uploads/organisation/profile_picture/14/thumb_original_logo_black.gif"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/en/api_v4/organisations/14.json"
        },
        {
          "rel": "platform",
          "href": "http://www.betterplace.org/en/organisations/mellemfolkeligtsamvirke"
        },
        {
          "rel": "projects",
          "href": "https://api.betterplace.org/en/api_v4/organisations/14/projects.json"
        }
      ]
    },
    {
      "id": 15,
      "slug": "gexsi",
      "created_at": "2007-07-03T15:06:31Z",
      "updated_at": "2013-09-23T17:09:17Z",
      "latitude": 51.53049850463867,
      "longitude": -0.12232699990273,
      "street": "1A Birkenhead ",
      "zip": "WC1H 8BA",
      "city": "London",
      "country": "UK",
      "name": "The Global Exchange for Social Investment - GEXSI",
      "description": "GEXSI is a charitable organisation registered in the UK, with offices in London and Berlin. From Philanthropic Support to Commercial Investment Social entrepreneurs who want to become self-sustaining, GEXSI can assist in finding start-up assistance from donors or investors. GEXSI mobilises a blend of philanthropic funds and commercial financing, tailored to the specific needs of social enterprises.\r\n\r\nGEXSI links charitable donors, social entrepreneurs, and social investors in funding exceptional economic, ecological, and social projects for sustainable development in low-income regions around the world. In order to unleash Entrepreneurship in Low-income Countries, GEXSI mobilises the capital and expertise needed by social entrepreneurs to move from 'aid to market'. \r\n\r\nInitially, social enterprises often depend on grants. To move towards self-reliance, many need start-up support – access to expertise, markets and finance. Many evolving social enterprises experience a financing gap: their financial needs exceed microcredit capacities, but do not reach the levels of commercial financing. The Global Exchange for Social Investment (GEXSI) assists in closing this gap. For Social Entrepreneurs, GEXSI provides expertise and financing tailored to the needs of each social entrepreneur. The Global Exchange for Social Investment (GEXSI) focuses on businesses that have social, environmental and economic impact, and clear potential for scaling up or replication.\r\n\r\nGEXSI collaborates with enterprises requiring initial financial support in their business development. Enterprises assisted by GEXSI typically look for investments ranging from EUR 10,000 to EUR 500,000.\r\n\r\nFor social entrepreneurs, GEXSI: Provides technical expertise in business planning and investment structuring; Locates financing, and; Facilitates networking, mentorship and exchanges of information and expertise.\r\n\r\n",
      "tax_deductible": false,
      "contact": {
        "name": "A. Renner",
        "picture": {
          "links": [
            {
              "rel": "original",
              "href": "/paperclip/000/000/392/original_Andreas_Renner_GEXSI.jpg"
            },
            {
              "rel": "large_attention_deprecated",
              "href": "/paperclip/000/000/392/default_Andreas_Renner_GEXSI.jpg"
            },
            {
              "rel": "profile_attention_deprecated",
              "href": "/paperclip/000/000/392/profile_Andreas_Renner_GEXSI.jpg"
            },
            {
              "rel": "thumb_attention_deprecated",
              "href": "/paperclip/000/000/392/thumb_Andreas_Renner_GEXSI.png"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "http://www.betterplace.org/en/users/andreas_r"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/en/api_v4/users/33/contact_data.json"
          }
        ]
      },
      "picture": {
        "links": [
          {
            "rel": "original",
            "href": "/uploads/organisation/profile_picture/15/original_original_GEXSI.gif"
          },
          {
            "rel": "large_attention_deprecated",
            "href": "/uploads/organisation/profile_picture/15/default_original_GEXSI.gif"
          },
          {
            "rel": "profile_attention_deprecated",
            "href": "/uploads/organisation/profile_picture/15/profile_original_GEXSI.gif"
          },
          {
            "rel": "thumb_attention_deprecated",
            "href": "/uploads/organisation/profile_picture/15/thumb_original_GEXSI.gif"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/en/api_v4/organisations/15.json"
        },
        {
          "rel": "platform",
          "href": "http://www.betterplace.org/en/organisations/gexsi"
        },
        {
          "rel": "projects",
          "href": "https://api.betterplace.org/en/api_v4/organisations/15/projects.json"
        }
      ]
    }
  ]
}
```

