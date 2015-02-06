
# Client Details

## Request

```nginx
GET https://api.betterplace.org/en/api_v4/clients/Volksfreund.json
```

## Command

```bash
curl "https://api.betterplace.org/en/api_v4/clients/Volksfreund.json"
```

**For [betterplace.org clients](../README.md#client-api) only:**

Some client-statistics for a betterplace.org client. All results are cached for 15 minutes.


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
    <td><code>Volksfreund</code></td>
    <td>required</td>
    <td>The betterplace.org-internal client permalink</td>
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
      <th align="left">donated_amount_in_cents</th>
      <td>number</td>
      <td>10100</td>
      <td>How many cents are donated already to all client projects. 
Calculation based on open_amount_in_cents and requested_amount_in_cents.

Therefore it includes the money of the client-pool-fundraising-event
that still has to be forwarded to one of the client-projects-needs.
It also includes external donations that project manager can add to projects.

Remember: This includes all donations to projects of this client even those
that are donated via betterplace.org or other channels.
</td>
    </tr>
    <tr>
      <th align="left">pool_balance_in_cents</th>
      <td>number</td>
      <td>100</td>
      <td>Clients may have a client-pool-fundraising-event that receives money
from offline-donations that could not be associated with a project or
similar use cases.

The balance repesents the donated amount in cents on the pool
that has not yet been forwarded to one of the client-project-needs.

This is the number that is include in open_amount_in_cents and donated_amount_in_cents.
</td>
    </tr>
    <tr>
      <th align="left">open_amount_in_cents</th>
      <td>number</td>
      <td>9900</td>
      <td>How many cents are still needed to complete all client projects.
This calculation is based on the sum of all
<a href="need_details.md">needs (open_amount_in_cents)</a>.
We also substract the money of the client-pool-fundraising-event
that still has to be forwarded to one of the client-projects-needs.
</td>
    </tr>
    <tr>
      <th align="left">requested_amount_in_cents</th>
      <td>number</td>
      <td>11000</td>
      <td>How many cents are still needed to complete all client projects.
This calculation is based on the sum of all
<a href="need_details.md">needs (requested_amount_in_cents)</a>.
</td>
    </tr>
    <tr>
      <th align="left">projects_count</th>
      <td>number</td>
      <td>100</td>
      <td>The number of <a href="projects_list.md">projects</a> of this client
</td>
    </tr>
    <tr>
      <th align="left">client_donated_amount_in_cents</th>
      <td>number</td>
      <td>8100</td>
      <td>How many cents are donated through the clients donation page.
</td>
    </tr>
    <tr>
      <th align="left">client_matched_amount_in_cents</th>
      <td>number</td>
      <td>2500</td>
      <td>How many cents are donated by matching donations by all matching funds of the client
</td>
    </tr>
    <tr>
      <th align="left">client_donations_count</th>
      <td>number</td>
      <td>200</td>
      <td>The number of <a href="client_donations_list.md">client donations</a> for this client
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
      <th align="left">projects</th>
      <td>Link to the <a href="projects_list.md">project list</a> of this client
</td>
    </tr>
    <tr>
      <th align="left">client_donations</th>
      <td>Link to the <a href="client_donations_list.md">client donations list</a> of this client
</td>
    </tr>
    <tr>
      <th align="left">client_project_tags</th>
      <td>Link to the <a href="client_tags_list.md">tags list</a> of this client
</td>
    </tr>
    <tr>
      <th align="left">opinions</th>
      <td>Link to the <a href="opinions_list.md">opinions list</a> of this client
</td>
    </tr>
</table>

## Response Example

```json
{
  "donated_amount_in_cents": 141634359,
  "pool_balance_in_cents": 8054639,
  "open_amount_in_cents": 22065686,
  "requested_amount_in_cents": 163700045,
  "projects_count": 322,
  "client_donated_amount_in_cents": 105663187,
  "client_matched_amount_in_cents": 0,
  "client_donations_count": 11299,
  "links": [
    {
      "rel": "projects",
      "href": "https://api.betterplace.org/en/api_v4/clients/volksfreund/projects.json"
    },
    {
      "rel": "client_donations",
      "href": "https://api.betterplace.org/en/api_v4/clients/volksfreund/client_donations.json"
    },
    {
      "rel": "client_project_tags",
      "href": "https://api.betterplace.org/en/api_v4/clients/volksfreund/tags.json"
    },
    {
      "rel": "opinions",
      "href": "https://api.betterplace.org/en/api_v4/clients/volksfreund/opinions.json"
    }
  ]
}
```

