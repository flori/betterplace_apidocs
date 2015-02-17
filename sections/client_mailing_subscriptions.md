
# Client Mailing Subscriptions

```HTTP
POST https://api.betterplace.org/de/api_v4/clients/Volksfreund/projects/4425/mailing_subscriptions.json
```

You can create/update mailing subscriptions to projects.

**Only available if authenticated as a client.** See [betterplace.org clients](../README.md#client-authentication).

**Response and error codes:**

A successful request will return HTTP status 201 (created).

An error will return HTTP status 422.

**Language:**

The subscription is marked with the language you use in your URL.
Newsletter authors write their content in a specific lang which you can
target with the subscription lang. To target a lang see
[api setting lang](../README.md#addressing-the-locale-of-a-resource).


## URL Parameters

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <th align="left">client_id</th>
    <td><code>Volksfreund</code></td>
    <td>yes</td>
    <td>The betterplace.org-internal client permalink.</td>
  </tr>
  <tr>
    <th align="left">project_id</th>
    <td><code>4425</code></td>
    <td>yes</td>
    <td>Project-id as an integer number ≥ 14.</td>
  </tr>
</table>

## JSON Parameters

JSON parameters have to be provided in the body of the request with the
Content-Type header set to "application/json". The parameters are part of a
flat JSON document without any nesting. Some parameters are required, others
are optional.

### Example

```json
{
  "email": "peter.paul@betterplace.org",
  "first_name": "Peter",
  "last_name": "Paul",
  "active": true
}
```

### Supported Parameters

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Types</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <th align="left">email</th>
    <td><code>peter.paul@betterplace.org</code></td>
    <td>string</td>
    <td>yes</td>
    <td>The email of the user</td>
  </tr>
  <tr>
    <th align="left">first_name</th>
    <td><code>Peter</code></td>
    <td>string</td>
    <td>yes</td>
    <td>The first name of the user</td>
  </tr>
  <tr>
    <th align="left">last_name</th>
    <td><code>Paul</code></td>
    <td>string</td>
    <td>yes</td>
    <td>The last name of the user</td>
  </tr>
  <tr>
    <th align="left">active</th>
    <td><code>true</code></td>
    <td>boolean</td>
    <td>yes</td>
    <td>State of the subscription: active/inactive</td>
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
      <th align="left">status</th>
      <td>string</td>
      <td>accepted</td>
      <td>HTTP status code as a descriptive string (see
http://www.rubydoc.info/github/rack/rack/Rack/Utils), e. g. "accepted"
for code 201.
</td>
    </tr>
    <tr>
      <th align="left">status_code</th>
      <td>number</td>
      <td>201</td>
      <td>HTTP status code as an integer number, e. g. 201.
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
      <th align="left">location</th>
      <td>Location where the created/updated resource can be viewed or more
information about it can be gathered.
</td>
    </tr>
</table>

## Response Example

```json
{
  "status": "created",
  "status_code": 201,
  "links": [

  ]
}
```

