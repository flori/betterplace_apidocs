
# Client Donations List ⇄ [Details](client_donation_details.md)

```nginx
GET https://api.betterplace.org/en/api_v4/clients/Volksfreund/client_donations.json?facets=client_reference%3A1234
```

**For [betterplace.org clients](../README.md#client-api) only:**

This API returns all donations to all client projects that where made using
the client donation form (but none of the other donation-sources).

Results are contained in a *data* attribute.


## Input Parameter

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Required/Optional</th>
    <th>Description</th>
  </tr>
  <tr>
    <th align="left">client_id</th>
    <td><code>Volksfreund</code></td>
    <td>required</td>
    <td>The betterplace.org-internal client permalink.</td>
  </tr>
  <tr>
    <th align="left">facets</th>
    <td><code>client_reference:1234</code></td>
    <td>optional</td>
    <td>You can search for a specific client_reference: <code>?facets=client_reference:54</code>

Example:
<a href="https://api.betterplace.org/en/api_v4/clients/karmic_minion/client_donations?facets=client_reference:54">
  <code>https://api.betterplace.org/en/api_v4/clients/karmic_minion/client_donations?facets=client_reference:54
</a>

This feature is only used in some cases that relate to the
<a href="../donation_form/third_party_app_donation_form.md">ThirdPartyApp custom donation form for organisations</a>
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
      <th align="left">amount_in_cents</th>
      <td>number</td>
      <td>10100</td>
      <td>Donated amount in cents</td>
    </tr>
    <tr>
      <th align="left">state</th>
      <td>string</td>
      <td>"confirmed"</td>
      <td>Donations can be created, confirmed, revoked or invalid. These mean:
<ul>
  <li><b>created</b> - The donation has been started, but the payment has not been processed yet</li>
  <li><b>confirmed</b> - The donation has been made and the payment has been processed successfully</li>
  <li><b>invalid</b> - There was some problem with this donation and the payment process never completed</li>
  <li><b>revoked</b> - The donation was cancelled because the payment has been revoked</li>
</ul>
</td>
    </tr>
    <tr>
      <th align="left">client_reference</th>
      <td>string</td>
      <td>922ec9531b-etc</td>
      <td>Client Donations can be identified via a custom client reference token. This reference should be url safe, e.g.
only consist of alphanumeric symbols like a SHA-1 Hash.
</td>
    </tr>
    <tr>
      <th align="left">created_at</th>
      <td>string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone)</td>
    </tr>
    <tr>
      <th align="left">receiver_type</th>
      <td>string</td>
      <td>"Project"</td>
      <td>Client donations may go to <code>Project</code>,
Project <code>Element</code>, <code>FundraisingEvent</code>.
</td>
    </tr>
    <tr>
      <th align="left">receiver_id</th>
      <td>number</td>
      <td>1114</td>
      <td>The id of the project, project element or fundraising event.</td>
    </tr>
    <tr>
      <th align="left">receiver_title</th>
      <td>string</td>
      <td>"Skateistan Afghanistan"</td>
      <td>The title of the project, project element or fundraising event.</td>
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
      <th align="left">receiver</th>
      <td>Link to the <a href="project_details.md">project details</a>
or <a href="need_details.md">project need details</a>
that is associated with this donation.
</td>
    </tr>
    <tr>
      <th align="left">self</th>
      <td>Link to this resource itself
(<a href="client_donation_details.md">client donation details</a>)
</td>
    </tr>
</table>

## Response Example

```json
{
  "total_entries": 9267,
  "offset": 0,
  "total_pages": 3089,
  "current_page": 1,
  "per_page": 3,
  "data": [
    {
      "amount_in_cents": 1000,
      "state": "confirmed",
      "client_reference": null,
      "created_at": "2010-10-28T12:44:49Z",
      "receiver_type": "Project",
      "receiver_id": 4807,
      "receiver_title": "Kleinbus für den Palais e.V. Trier",
      "links": [
        {
          "rel": "receiver",
          "href": "https://api.betterplace.org/en/api_v4/projects/4807.json"
        },
        {
          "rel": "self",
          "href": "https://api.betterplace.org/en/api_v4/clients/volksfreund/client_donations/328db52eb745be52f3b5aaf0.json"
        }
      ]
    },
    {
      "amount_in_cents": 100,
      "state": "confirmed",
      "client_reference": null,
      "created_at": "2010-10-28T15:48:16Z",
      "receiver_type": "Project",
      "receiver_id": 4798,
      "receiver_title": "Hilfe für Jugendliche mit krebskranken Eltern",
      "links": [
        {
          "rel": "receiver",
          "href": "https://api.betterplace.org/en/api_v4/projects/4798.json"
        },
        {
          "rel": "self",
          "href": "https://api.betterplace.org/en/api_v4/clients/volksfreund/client_donations/7d775febc93584375ab07136.json"
        }
      ]
    },
    {
      "amount_in_cents": 400,
      "state": "confirmed",
      "client_reference": null,
      "created_at": "2010-10-29T07:46:25Z",
      "receiver_type": "Project",
      "receiver_id": 4798,
      "receiver_title": "Hilfe für Jugendliche mit krebskranken Eltern",
      "links": [
        {
          "rel": "receiver",
          "href": "https://api.betterplace.org/en/api_v4/projects/4798.json"
        },
        {
          "rel": "self",
          "href": "https://api.betterplace.org/en/api_v4/clients/volksfreund/client_donations/86be4452d4afb0f2d56f0add.json"
        }
      ]
    }
  ]
}
```

