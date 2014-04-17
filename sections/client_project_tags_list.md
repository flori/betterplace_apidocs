
# Client project-tags list

```nginx
GET https://api.betterplace.org/en/api_v4/clients/Volksfreund/project_tags.json
```

**For [betterplace.org clients](../README.md#client-api) only:**

This API returns all project-tags defined for a client.

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
      <td>Link to the <a href="projects_list.md">project list</a> of all tagged projects for the current client.
</td>
    </tr>
</table>

## Response Example

```json
{
  "total_entries": 21,
  "offset": 0,
  "total_pages": 11,
  "current_page": 1,
  "per_page": 2,
  "data": [
    {
      "tag": "Gesundheit",
      "projects_count": 12,
      "links": [
        {
          "rel": "projects",
          "href": "https://api.betterplace.org/en/api_v4/clients/volksfreund/project_tags/Gesundheit/projects.json"
        }
      ]
    },
    {
      "tag": "Bildung",
      "projects_count": 17,
      "links": [
        {
          "rel": "projects",
          "href": "https://api.betterplace.org/en/api_v4/clients/volksfreund/project_tags/Bildung/projects.json"
        }
      ]
    }
  ]
}
```


# Tags of a project assigned by a client

```nginx
GET https://api.betterplace.org/en/api_v4/clients/Volksfreund/projects/11614/tags.json
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
    <th align="left">id</th>
    <td><code>11614</code></td>
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
      <td>Link to the <a href="projects_list.md">project list</a> of all tagged projects for the current client.
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
  "per_page": 2,
  "data": [

  ]
}
```

