
# Matching Funds List ⇄ [Details](matching_fund_details.md)

```nginx
GET https://api.betterplace.org/en/api_v4/matching_funds.json?facets=state%3Aactivated&project_id=1114
```

A list of betterplace.org matching funds.


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
    <th align="left">facets</th>
    <td><code>state:activated</code></td>
    <td>optional</td>
    <td>Filter the result set by <code>state</code> (activated|closed)
<a href="../README.md#request-parameter-format">Learn how to format the parameter</a>.
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
      <td>string</td>
      <td>53</td>
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
      <th align="left">activated_at</th>
      <td>null &#124; string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone)</td>
    </tr>
    <tr>
      <th align="left">title</th>
      <td>string</td>
      <td>ACME Matching Everything</td>
      <td>Our matching fund's name</td>
    </tr>
    <tr>
      <th align="left">description</th>
      <td>string</td>
      <td>It's all about matching donations…</td>
      <td>The description of the matching fund</td>
    </tr>
    <tr>
      <th align="left">company_name</th>
      <td>string</td>
      <td>ACME</td>
      <td>The company that supports it</td>
    </tr>
    <tr>
      <th align="left">state</th>
      <td>string</td>
      <td>activated</td>
      <td>Current state of this matching fund: either activated or closed</td>
    </tr>
    <tr>
      <th align="left">logo_url</th>
      <td>string</td>
      <td>http://example.com/images/logo.png</td>
      <td>The URL of the logo image.</td>
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
(<a href="matching_fund_details.md">matching fund details</a>)
</td>
    </tr>
    <tr>
      <th align="left">platform</th>
      <td colspan="3">Permalink to betterplace.org</td>
    </tr>
    <tr>
      <th align="left">projects</th>
      <td colspan="3">Link to the list of projects belonging to this matching fund</td>
    </tr>
    <tr>
      <th align="left">documentation</th>
      <td colspan="3">Link to this resource in the documentation
</td>
    </tr>
  </table>
</table>

## Response Example

```json
{
  "total_entries": 0,
  "offset": 0,
  "total_pages": 1,
  "current_page": 1,
  "per_page": 2,
  "data": [

  ]
}
```
