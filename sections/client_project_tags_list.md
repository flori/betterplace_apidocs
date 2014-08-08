
# Tags of a project assigned by a client

```nginx
GET https://api.betterplace.org/en/api_v4/clients/Volksfreund/projects/4425/tags.json
```

**For [betterplace.org clients](../README.md#client-api) only:**

This API returns all tags assigned by this client for this project.
Client project tags are a custom client feature and andministered
as a service of [betterplace solutions](http://www.betterplace-solutions.de/#buergerzeitung).

Results are contains in a *data* attribute.


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
    <th align="left">project_id</th>
    <td><code>4425</code></td>
    <td>required</td>
    <td>The name of the client project-tag – a list of tags is provided by
<a href="http://www.betterplace-solutions.de/#buergerzeitung">betterplace solutions</a>.
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
      <th align="left">tag</th>
      <td>string</td>
      <td>"Education"</td>
      <td>The name of the tag, that is unique per client.
</td>
    </tr>
    <tr>
      <th align="left">projects_count</th>
      <td>number</td>
      <td>23</td>
      <td>The number of <a href="projects_list.md">projects</a>
that where tagged with this tag.
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
      <td>Link to the <a href="projects_list.md">project list</a> of all projects that are tagged with this tag for the current client.
</td>
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
    {
      "tag": "Trier",
      "projects_count": 189,
      "links": [
        {
          "rel": "projects",
          "href": "https://api.betterplace.org/en/api_v4/clients/volksfreund/tags/Trier/projects.json"
        }
      ]
    },
    {
      "tag": "KinderJugendliche",
      "projects_count": 191,
      "links": [
        {
          "rel": "projects",
          "href": "https://api.betterplace.org/en/api_v4/clients/volksfreund/tags/KinderJugendliche/projects.json"
        }
      ]
    },
    {
      "tag": "Familien",
      "projects_count": 100,
      "links": [
        {
          "rel": "projects",
          "href": "https://api.betterplace.org/en/api_v4/clients/volksfreund/tags/Familien/projects.json"
        }
      ]
    },
    {
      "tag": "Behinderte",
      "projects_count": 62,
      "links": [
        {
          "rel": "projects",
          "href": "https://api.betterplace.org/en/api_v4/clients/volksfreund/tags/Behinderte/projects.json"
        }
      ]
    },
    {
      "tag": "Prio2",
      "projects_count": 200,
      "links": [
        {
          "rel": "projects",
          "href": "https://api.betterplace.org/en/api_v4/clients/volksfreund/tags/Prio2/projects.json"
        }
      ]
    }
  ]
}
```

