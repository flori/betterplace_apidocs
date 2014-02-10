
# Project Needs List ⇄ [Details](need_details.md)

```nginx
GET https://api.betterplace.org/en/api_v4/projects/1114/needs.json
```

A list of betterplace.org projects needs (donate money).
Results are contained in a *data* attribute.
The details and list view show the same data per project need.

*For [betterplace.org clients](../README.md#client-api):*
There is no client-scoped-url.
Please use the api calls that are provided inside the client project _url_ response
to make sure you only request data that is associated with one of your projects.


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
      <th align="left">id</th>
      <td>number</td>
      <td>29</td>
      <td>A integer number ≥ 1</td>
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
      <th align="left">title</th>
      <td>string</td>
      <td></td>
      <td>Max 50 character</td>
    </tr>
    <tr>
      <th align="left">description</th>
      <td>string</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <th align="left">completed</th>
      <td>boolean</td>
      <td>false</td>
      <td>True if the need is 100 % financed</td>
    </tr>
    <tr>
      <th align="left">progress_percentage</th>
      <td>number</td>
      <td>82</td>
      <td>% financed</td>
    </tr>
    <tr>
      <th align="left">donated_amount_in_cents</th>
      <td>number</td>
      <td>12382</td>
      <td>How many cents are donated already.
This includes all donations that can be given to a need
(direct donation, forwarding of project donation,
forwarding of organisation donation,
forwarding of fundraising event donations,
offline donations and also(!) external donations)
</td>
    </tr>
    <tr>
      <th align="left">open_amount_in_cents</th>
      <td>number</td>
      <td>12382</td>
      <td>How many cents are still needed to complete the need</td>
    </tr>
    <tr>
      <th align="left">requested_amount_in_cents</th>
      <td>number</td>
      <td>12382</td>
      <td>How much money is needed in total</td>
    </tr>
    <tr>
      <th colspan="4">Links</th>
    </tr>
    <tr>
      <th>Linkname</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">self</th>
      <td colspan="3">Link to this resource itself
(<a href="need_details.md">need details</a>)
</td>
    </tr>
    <tr>
      <th align="left">project</th>
      <td colspan="3">Link to the related <a href="project_details.md">project's details</a>
</td>
    </tr>
  </table>
</table>

## Response Example

```json
{
  "total_entries": 80,
  "offset": 0,
  "total_pages": 27,
  "current_page": 1,
  "per_page": 3,
  "data": [
    {
      "id": 76625,
      "created_at": "2014-01-03T10:41:44Z",
      "updated_at": "2014-02-04T20:17:46Z",
      "title": "Kabul Skatepark Food",
      "description": "Equivalent to providing food for the Kabul skatepark for 1 month including the Back-To-School program which runs 5 days/week. The Back-To-School program aims to give children the support they need to return to public school in Afghanistan.",
      "completed": false,
      "progress_percentage": 90.46,
      "donated_amount_in_cents": 66944,
      "open_amount_in_cents": 7056,
      "requested_amount_in_cents": 74000,
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/en/api_v4/projects/1114/needs/76625.json"
        },
        {
          "rel": "project",
          "href": "https://api.betterplace.org/en/api_v4/projects/1114.json"
        }
      ]
    },
    {
      "id": 5228,
      "created_at": "2009-03-10T10:38:39Z",
      "updated_at": "2013-10-29T00:16:31Z",
      "title": "Warme Mahlzeiten",
      "description": "Wer sich viel bewegt, der muss auch richtig essen: Mit nur 50 Euro im Monat lassen sich 8-10 warme Mahlzeiten für rund 30 Waisenkinder bereitstellen, die zweimal in der Woche von dem Skateistan-Team besucht werden und lernen Skateboard zu fahren.",
      "completed": true,
      "progress_percentage": 100.0,
      "donated_amount_in_cents": 5000,
      "open_amount_in_cents": 0,
      "requested_amount_in_cents": 5000,
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/en/api_v4/projects/1114/needs/5228.json"
        },
        {
          "rel": "project",
          "href": "https://api.betterplace.org/en/api_v4/projects/1114.json"
        }
      ]
    },
    {
      "id": 5229,
      "created_at": "2009-03-10T10:54:30Z",
      "updated_at": "2013-10-29T00:16:31Z",
      "title": "Skateboardlehrer",
      "description": "Mirwais, 13, ist Afghanistans erster talentierter Skateboardlehrer. Früher wusch er für 2 Dollar am Tag Autos auf der Straße. Heute ist er Skateistans Angestellter und kann mit seinem Gehalt (167 Euro/Monat) seine Familie ernähren.",
      "completed": true,
      "progress_percentage": 100.0,
      "donated_amount_in_cents": 16700,
      "open_amount_in_cents": 0,
      "requested_amount_in_cents": 16700,
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/en/api_v4/projects/1114/needs/5229.json"
        },
        {
          "rel": "project",
          "href": "https://api.betterplace.org/en/api_v4/projects/1114.json"
        }
      ]
    }
  ]
}
```
