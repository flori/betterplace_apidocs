
# Results List

```nginx
GET http://api.betterplace.dev/en/api_v4/contests/1/results.json
```

Detailed information about each in the challenge participating project.
For further detailed information we provide the api link to the project.


## Input Parameter

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Required/Optional</th>
    <th>Description</th>
  </tr>
  <tr>
    <th align="left">contest_id</th>
    <td><code>1</code></td>
    <td>required</td>
    <td>Contest-id as an integer number ≥ 0.</td>
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
      <th align="left">rank</th>
      <td>number</td>
      <td>TODO</td>
      <td>An integer number ≥ 1</td>
    </tr>
    <tr>
      <th align="left">donation_count</th>
      <td>number</td>
      <td>TODO</td>
      <td>An integer number ≥ 0</td>
    </tr>
    <tr>
      <th align="left">donated_amount_in_cents</th>
      <td>number</td>
      <td>TODO</td>
      <td>An integer number ≥ 0</td>
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
      <th align="left">platform</th>
      <td>A link to the project on betterplace.org</td>
    </tr>
    <tr>
      <th align="left">api</th>
      <td>A link to the project on api.betterplace.org</td>
    </tr>
</table>

## Response Example

```json
{
  "total_entries": null,
  "offset": null,
  "total_pages": null,
  "current_page": null,
  "per_page": null,
  "data": [

  ]
}
```

