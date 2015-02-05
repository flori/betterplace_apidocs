
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
      <td>1</td>
      <td>An integer number ≥ 1</td>
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
      <td>Street address</td>
    </tr>
    <tr>
      <th align="left">zip</th>
      <td>null &#124; string</td>
      <td>"10997"</td>
      <td>ZIP code</td>
    </tr>
    <tr>
      <th align="left">city</th>
      <td>null &#124; string</td>
      <td>"Berlin"</td>
      <td>Name of the city</td>
    </tr>
    <tr>
      <th align="left">country</th>
      <td>null &#124; string</td>
      <td>"Deutschland"</td>
      <td>Name of the country</td>
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
        <th align="left" style="white-space: nowrap">
          <a name="picture-ref" href="#picture">
            ↓picture
          </a>
        </th>
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
        <th align="left" style="white-space: nowrap">
          <a name="contact.picture-ref" href="#contact.picture">
            ↓contact.picture
          </a>
        </th>
      <td>string</td>
      <td>//assets.betterplace.org/…</td>
      <td>User profile picture or a fallback image</td>
    </tr>
  </table>
### <a name="contact.picture" href="#contact.picture-ref">↑Nested Attributes: contact.picture</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">contact.picture.fallback</th>
      <td>boolean</td>
      <td>true</td>
      <td>Specifies whether a fallback image is given or not</td>
    </tr>
  </table>
### <a name="picture" href="#picture-ref">↑Nested Attributes: picture</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">picture.fallback</th>
      <td>boolean</td>
      <td>true</td>
      <td>Specifies whether a fallback image is given or not</td>
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
  "total_entries": 10758,
  "offset": 0,
  "total_pages": 5379,
  "current_page": 1,
  "per_page": 2,
  "data": [
    {
      "id": 2449,
      "created_at": "2009-11-28T18:12:08+01:00",
      "updated_at": "2013-09-23T20:19:30+02:00",
      "latitude": 51.50659942626953,
      "longitude": 7.45382022857666,
      "street": "Liebigstraße 5",
      "zip": "44139",
      "city": "Dortmund",
      "country": "Germany",
      "slug": "_blank_profile_",
      "name": "Entfernte Organisation",
      "description": "Diese Organisation wurde auf eigenen Wunsch entfernt.",
      "tax_deductible": false,
      "contact": {
        "name": "U. B",
        "picture": {
          "fallback": true,
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/022/259/fill_100x100_original_new-user.gif"
            },
            {
              "rel": "original",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/022/259/crop_original_original_new-user.gif"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.org/en/users/_blank_profile_"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/en/api_v4/users/22259/contact_data.json"
          }
        ]
      },
      "picture": {
        "fallback": true,
        "links": [
          {
            "rel": "fill_100x100",
            "href": "https://asset1.betterplace.org/uploads/organisation/profile_picture/000/002/449/fill_100x100_original_new-organisation.jpg"
          },
          {
            "rel": "fill_200x200",
            "href": "https://asset1.betterplace.org/uploads/organisation/profile_picture/000/002/449/fill_200x200_original_new-organisation.jpg"
          },
          {
            "rel": "fill_400x400",
            "href": "https://asset1.betterplace.org/uploads/organisation/profile_picture/000/002/449/fill_400x400_original_new-organisation.jpg"
          },
          {
            "rel": "original",
            "href": "https://asset1.betterplace.org/uploads/organisation/profile_picture/000/002/449/crop_original_original_new-organisation.jpg"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/en/api_v4/organisations/2449.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/en/organisations/_blank_profile_"
        },
        {
          "rel": "projects",
          "href": "https://api.betterplace.org/en/api_v4/organisations/2449/projects.json"
        },
        {
          "rel": "website",
          "href": ""
        }
      ]
    },
    {
      "id": 457,
      "created_at": "2008-10-06T22:00:18+02:00",
      "updated_at": "2013-12-03T17:48:37+01:00",
      "latitude": -23.60400009155273,
      "longitude": -46.43099975585938,
      "street": "Rua Ribeiro Baião, 111",
      "zip": "CEP: 08381",
      "city": "São Paulo - SP",
      "country": "Brazil",
      "slug": "_cidadessemfome",
      "name": "STÄDTE OHNE HUNGER - CIDADES SEM FOME",
      "description": "CITIES WITHOUT HUNGER - Cidades sem Fome (CsF) is a non-governmental organization (NGO) which has set up sustainable agrarian projects based on organic farming. The aim is to help and teach people to manage their own business and become financially independent. Community Gardens, School Gardens and Agricultural Greenhouses have been developed on unused and neglected public and private areas within social focal points to provide jobs and improve the diets of adults and children. \r\nIn 2009 the Small Family Farms Project, the organizations fourth project, has been set up in Rio Grande do Sul, to train farmers in multiple cropping as an alternative to monoculture and help them starting new businesses in organic farming. \r\nCITIES WITHOUT HUNGER was founded in 2004 in São Paulo by Hans Dieter Temp, who has a degree in Business Administration, and is a Technician for Agriculture and Environmental Policies. In 2013 Hans Dieter Temp was selected and awarded with the title Social Entrepreneur “Changemaker” by Ashoka. \r\nCITIES WITHOUT HUNGER has received numerous national and international awards, such as the FINEP Award 2011 for Technological Innovation, Dubai International Award for Best Practices 2010 (UN-HABITAT), and AEA-Award for Environmental Responsibility in 2009. In 2012 CITIES WITHOUT HUNGER was selected by Caixa Econômica Federal for its commitment to the realization of the UN-Millennium Goals. \r\n",
      "tax_deductible": false,
      "contact": {
        "name": "H. Temp",
        "picture": {
          "fallback": true,
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/004/326/fill_100x100_original_CsF_Team_Hans_Dieter_Temp.jpg"
            },
            {
              "rel": "original",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/004/326/crop_original_original_CsF_Team_Hans_Dieter_Temp.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.org/en/users/hans_t"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/en/api_v4/users/4326/contact_data.json"
          }
        ]
      },
      "picture": {
        "fallback": true,
        "links": [
          {
            "rel": "fill_100x100",
            "href": "https://asset1.betterplace.org/uploads/organisation/profile_picture/000/000/457/fill_100x100_original_Logotipo_-_Cidades_Sem_Fome__1_.jpg"
          },
          {
            "rel": "fill_200x200",
            "href": "https://asset1.betterplace.org/uploads/organisation/profile_picture/000/000/457/fill_200x200_original_Logotipo_-_Cidades_Sem_Fome__1_.jpg"
          },
          {
            "rel": "fill_400x400",
            "href": "https://asset1.betterplace.org/uploads/organisation/profile_picture/000/000/457/fill_400x400_original_Logotipo_-_Cidades_Sem_Fome__1_.jpg"
          },
          {
            "rel": "original",
            "href": "https://asset1.betterplace.org/uploads/organisation/profile_picture/000/000/457/crop_original_original_Logotipo_-_Cidades_Sem_Fome__1_.jpg"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/en/api_v4/organisations/457.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/en/organisations/_cidadessemfome"
        },
        {
          "rel": "projects",
          "href": "https://api.betterplace.org/en/api_v4/organisations/457/projects.json"
        },
        {
          "rel": "website",
          "href": "http://www.cidadessemfome.com.br"
        }
      ]
    }
  ]
}
```

