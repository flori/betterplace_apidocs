
# Volunteering Details ⇄ [List](volunteering_list.md)

```nginx
GET https://api.betterplace.org/en/api_v4/volunteering/23.json
```

The details of a betterplace.org volunteering offer (donate time).

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
  <tr>
    <th align="left">id</th>
    <td><code>23</code></td>
    <td>required</td>
    <td>Volunteering-id as an integer number ≥ 1.</td>
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
      <td>Where the volunteering takes place</td>
    </tr>
    <tr>
      <th align="left">zip</th>
      <td>null &#124; string</td>
      <td>"10997"</td>
      <td>Where the volunteering takes place</td>
    </tr>
    <tr>
      <th align="left">city</th>
      <td>null &#124; string</td>
      <td>"Berlin"</td>
      <td>Where the volunteering takes place</td>
    </tr>
    <tr>
      <th align="left">country</th>
      <td>null &#124; string</td>
      <td>"Deutschland"</td>
      <td>Where the volunteering takes place, translated to the requested language</td>
    </tr>
    <tr>
      <th align="left">title</th>
      <td>string</td>
      <td>TODO</td>
      <td>Max 100 character unless the volunteering is imported</td>
    </tr>
    <tr>
      <th align="left">description</th>
      <td>string</td>
      <td>TODO</td>
      <td>TODO</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a name="carrier-ref" href="#carrier">
            ↓carrier
          </a>
        </th>
      <td>object</td>
      <td>TODO</td>
      <td>An organisation, Users will be added later</td>
    </tr>
    <tr>
      <th align="left">vacancies</th>
      <td>number</td>
      <td>1</td>
      <td>The number of volunteers that are needed, provided by the manager</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a name="image-ref" href="#image">
            ↓image
          </a>
        </th>
      <td>null &#124; object</td>
      <td>TODO</td>
      <td>Each volunteering has one optional image</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a name="contact-ref" href="#contact">
            ↓contact
          </a>
        </th>
      <td>object</td>
      <td>TODO</td>
      <td>Contact person, contact data and contact address</td>
    </tr>
    <tr>
      <th align="left">topics</th>
      <td>array</td>
      <td>["Development cooperation", "Children & youth"]</td>
      <td>Up to 4 categories that describe, what for which causes you need volunteers.
Results are translated to the requested language.
Possible results: "Animal & environment protection", "Culture & sports",
"Children & youth", "Development cooperation ", "DisabledEducation", "Elderly people",
"Human rights", "Immigrants", "Invalid", "Local help", "Socially deprived"
</td>
    </tr>
    <tr>
      <th align="left">activities</th>
      <td>array &#124; null</td>
      <td>["consulting/coaching", "office work"]</td>
      <td>Up to 4 categories that describe, what for which causes you need volunteers.
Results are translated to the requested language.
Possible results: "consulting/coaching", "crafting/gardening", "doing sports",
"doing the chores", "group care", "nursing/parenting", "office work",
"organising/managing", "painting/designing", "tutoring/reading",
"visiting/accompanying", "writing/translating"
</td>
    </tr>
    <tr>
      <th align="left">imported_from</th>
      <td>null &#124; string</td>
      <td>aktion_mensch</td>
      <td>Betterplace imports volunteering offers from Aktions Mensch.</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a name="import_information-ref" href="#import_information">
            ↓import_information
          </a>
        </th>
      <td>null &#124; object</td>
      <td>TODO</td>
      <td>Meta data concerning the import of this volunteering offer, if it
was indeed imported.
</td>
    </tr>
  </table>
#### Links
  <table>
    <tr>
      <th>Linkname</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">self</th>
      <td>Link to this resource itself
(<a href="volunteering_details.md">volunteering details</a>)
</td>
    </tr>
    <tr>
      <th align="left">platform</th>
      <td>Permalink to betterplace.org</td>
    </tr>
    <tr>
      <th align="left">carrier.logo</th>
      <td>Thumbnail size</td>
    </tr>
    <tr>
      <th align="left">image.fill_618x322</th>
      <td>618x322 Pixel</td>
    </tr>
    <tr>
      <th align="left">image.fill_270x141</th>
      <td>270x141 Pixel</td>
    </tr>
    <tr>
      <th align="left">image.original</th>
      <td>Original size</td>
    </tr>
    <tr>
      <th align="left">image.thumb</th>
      <td>Thumbnail size</td>
    </tr>
    <tr>
      <th align="left">image.medium</th>
      <td>Medium size</td>
    </tr>
    <tr>
      <th align="left">image.regular</th>
      <td>Regular size</td>
    </tr>
    <tr>
      <th align="left">contact.picture.original</th>
      <td>Original size as uploaded by the user</td>
    </tr>
  </table>
### <a name="carrier" href="#carrier-ref">↑Nested Attributes: carrier</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">carrier.name</th>
      <td>string</td>
      <td>"Viva con Agua de Sankt Pauli e.V."</td>
      <td>An organisation name, Users will be added later</td>
    </tr>
    <tr>
      <th align="left">carrier.street</th>
      <td>string</td>
      <td>"Rosenstr. 3"</td>
      <td>Contact data for the organisation</td>
    </tr>
    <tr>
      <th align="left">carrier.city</th>
      <td>string</td>
      <td>"Berlin"</td>
      <td>Contact data for the organisation</td>
    </tr>
    <tr>
      <th align="left">carrier.zip</th>
      <td>string</td>
      <td>"10123"</td>
      <td>Contact data for the organisation</td>
    </tr>
    <tr>
      <th align="left">carrier.country</th>
      <td>string</td>
      <td>"Germany"</td>
      <td>Contact data for the organisation</td>
    </tr>
    <tr>
      <th align="left">carrier.latitude</th>
      <td>number</td>
      <td>13.1234</td>
      <td>Contact data for the organisation</td>
    </tr>
    <tr>
      <th align="left">carrier.longitude</th>
      <td>number</td>
      <td>54.123</td>
      <td>Contact data for the organisation</td>
    </tr>
  </table>
#### Links
  No links defined for **carrier**.
### <a name="image" href="#image-ref">↑Nested Attributes: image</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">image.description</th>
      <td>string</td>
      <td></td>
      <td>Image description</td>
    </tr>
  </table>
#### Links
  No links defined for **image**.
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
      <td>string</td>
      <td>Till Behnke</td>
      <td>Fullname of the contact person.
For imported volunteering offers, this is the
contact-name that is provided on import.
</td>
    </tr>
    <tr>
      <th align="left">contact.phone</th>
      <td>string</td>
      <td>030 - 7676 4488 44</td>
      <td>Phone number for direct contact.
No validations on input apply.
</td>
    </tr>
    <tr>
      <th align="left">contact.email</th>
      <td>string</td>
      <td>change@betterplace.org</td>
      <td>Plain text email-address for direct contact
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
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">contact.original</th>
      <td>Original size as uploaded by the user</td>
    </tr>
  </table>
### <a name="import_information" href="#import_information-ref">↑Nested Attributes: import_information</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">import_information.created_at</th>
      <td>null &#124; string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone) when the imported record was actually created.
</td>
    </tr>
    <tr>
      <th align="left">import_information.updated_at</th>
      <td>null &#124; string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone) when the imported record was
actually updated last.
</td>
    </tr>
    <tr>
      <th align="left">import_information.import_type</th>
      <td>string</td>
      <td>"Import::ImportFormat"</td>
      <td>Type of import this record originated from.</td>
    </tr>
    <tr>
      <th align="left">import_information.import_id</th>
      <td>string</td>
      <td>"foo:23"</td>
      <td>Unique identifier for this imported record.
</td>
    </tr>
    <tr>
      <th align="left">import_information.imported_at</th>
      <td>string</td>
      <td>"1994-11-15T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone) when the record was imported at
betterplace.
</td>
    </tr>
  </table>
#### Links
  No links defined for **import_information**.

## Response Example

```json
{
  "id": 23,
  "created_at": "2013-01-28T09:23:17Z",
  "updated_at": "2013-05-16T15:21:06Z",
  "latitude": null,
  "longitude": null,
  "street": null,
  "zip": null,
  "city": null,
  "country": null,
  "title": "Essensausgabe/Fahrdienst",
  "description": "<p>Die Kasseler Tafel e.V. sammelt qualitativ einwandfreie Lebensmittel, die kurz vor dem Mindesthaltbarkeitsdatum stehen, bei Firmen in der Region ein und verteilt diese gegen einen symbolischen Betrag an bedürftige Mitbürgerinnen und Mitbürger.</p>\n<p>Freiwillige können sich in folgenden Bereichen bei der Kasseler Tafel betätigen:</p>\n<p>1. Lebensmittel sortieren und ausgeben</p>\n<p>2. als Fahrer: Abholung der Lebensmittel bei den Supermärkten</p>\n\n<p>Mehr Informationen finden Sie unter: http://kasseler-tafel.de/</p>\n<p>Wir freuen uns über Ihr Interesse! </p><ul><li>Unfallversicherung</li><li>Haftpflichtversicherung</li><li>Anleitung durch Fachkräfte</li><li>Tätigkeitsnachweise</li><li>Ausstattung mit Medien / Arbeitsmaterialien</li></ul>",
  "carrier": {
    "name": "FreiwilligenZentrum Kassel",
    "street": "Spohrstraße 5",
    "city": "Kassel",
    "zip": "34117",
    "country": "Germany",
    "latitude": 51.3171,
    "longitude": 9.49561,
    "links": [
      {
        "rel": "logo",
        "href": ""
      }
    ]
  },
  "vacancies": 1,
  "image": {
    "description": null,
    "links": [
      {
        "rel": "fill_618x322",
        "href": "http://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_618x322_default.betterplace.png"
      },
      {
        "rel": "fill_270x141",
        "href": "http://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_270x141_default.betterplace.png"
      },
      {
        "rel": "original",
        "href": "http://asset1.betterplace.org/assets/default/job_description_profile_picture/fill_618x322_default.betterplace.png"
      },
      {
        "rel": "thumb",
        "href": "http://asset1.betterplace.org/assets/default/job_description_profile_picture/thumb_default.betterplace.png"
      },
      {
        "rel": "medium",
        "href": "http://asset1.betterplace.org/assets/default/job_description_profile_picture/medium_default.betterplace.png"
      },
      {
        "rel": "regular",
        "href": "http://asset1.betterplace.org/assets/default/job_description_profile_picture/regular_default.betterplace.png"
      }
    ]
  },
  "contact": {
    "name": "Frank Gerhold",
    "phone": "0561 - 10 24 25",
    "email": "info@freiwilligenzentrumkassel.de",
    "picture": null,
    "links": [

    ]
  },
  "topics": [

  ],
  "activities": [

  ],
  "imported_from": "aktion_mensch",
  "import_information": {
    "created_at": "2013-03-15T00:00:00Z",
    "updated_at": "2013-03-15T00:00:00Z",
    "import_type": "Bettertime::AktionMensch::Import",
    "import_id": "fn-471",
    "imported_at": "2013-05-16T15:21:06Z",
    "links": [

    ]
  },
  "links": [
    {
      "rel": "self",
      "href": "https://api.betterplace.org/en/api_v4/volunteering/23.json"
    },
    {
      "rel": "platform",
      "href": "http://www.betterplace.org/en/volunteering/23-essensausgabe-fahrdienst"
    }
  ]
}
```

