
# Project Need Details ⇄ [List](needs_list.md)

```nginx
GET https://api.betterplace.org/en/api_v4/projects/1114/needs/59220.json
```

The details of a betterplace.org project need (donate money).
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
  <tr>
    <th align="left">id</th>
    <td><code>59220</code></td>
    <td>required</td>
    <td>Need-id as an integer number ≥ 29.</td>
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
(<a href="need_details.md">need details</a>)
</td>
    </tr>
    <tr>
      <th align="left">project</th>
      <td>Link to the related <a href="project_details.md">project's details</a>
</td>
    </tr>
  </table>

## Response Example

```json
{
  "id": 79124,
  "created_at": "2014-02-17T16:01:17Z",
  "updated_at": "2014-03-21T13:35:08Z",
  "title": "Clean Water for the Skateparks in Kabul and MeS",
  "description": "The equivalent of supplying clean drinking water for all of our staff and students in both the Kabul and Mazar-e-Sharif Skateparks. ",
  "completed": false,
  "progress_percentage": 5.74,
  "donated_amount_in_cents": 10298,
  "open_amount_in_cents": 169202,
  "requested_amount_in_cents": 179500,
  "links": [
    {
      "rel": "self",
      "href": "https://api.betterplace.org/en/api_v4/projects/1114/needs/79124.json"
    },
    {
      "rel": "project",
      "href": "https://api.betterplace.org/en/api_v4/projects/1114.json"
    }
  ]
}
```

