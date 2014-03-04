
# Client donation details

```nginx
GET https://api.betterplace.org/en/api_v4/clients/Volksfreund/client_donations/5733f8cf3feaaf711172fbfd.json
```

**For [betterplace.org clients](../README.md#client-api) only:**
The details of a donation.


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
    <td>The betterplace.org-internal client permalink</td>
  </tr>
  <tr>
    <th align="left">id</th>
    <td><code>5733f8cf3feaaf711172fbfd</code></td>
    <td>required</td>
    <td>The donation token that the client donation form passed to the callback url</td>
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
</table>

## Response Example

```json
{
  "total_entries": 0,
  "offset": 0,
  "total_pages": 1,
  "current_page": 1,
  "per_page": 3,
  "data": [

  ]
}
```

