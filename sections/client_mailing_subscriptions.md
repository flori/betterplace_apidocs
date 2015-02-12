
# Creates/Updates a mailing subscription

```nginx
POST https://api.betterplace.org/de/api_v4/clients/Volksfreund/projects/4425/mailing_subscriptions.json
```

You can create/update mailing subscriptions to projects.

*Only available if authenticated as a client, see [betterplace.org clients](../README.md#client-authentication):*


## URL Parameter

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

## JSON Parameters Example

```json
{
  "email": "peter.paul@betterplace.org",
  "first_name": "Peter",
  "last_name": "Paul",
  "active": true
}
```

## JSON Parameters

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
      <th align="left">email</th>
      <td>string</td>
      <td>peter.paul@betterplace.org</td>
      <td>The first name of the user</td>
    </tr>
    <tr>
      <th align="left">first_name</th>
      <td>string</td>
      <td>Peter</td>
      <td>The first name of the user</td>
    </tr>
    <tr>
      <th align="left">last_name</th>
      <td>string</td>
      <td>Paul</td>
      <td>The last name of the user</td>
    </tr>
    <tr>
      <th align="left">active</th>
      <td>boolean</td>
      <td>true</td>
      <td>State of the subscription: active/inactive</td>
    </tr>
  </table>
</table>

## Response Links

<table>
  <tr>
    <th>Linkname</th>
    <th>Description</th>
  </tr>

  <th colspan="2">No response example defined</th>
</table>

## Response Example

```json
{
  "email": "peter.paul@betterplace.org",
  "first_name": "Peter",
  "last_name": "Paul",
  "active": true,
  "links": [

  ]
}
```
