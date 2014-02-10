
# User Contact Data Details

```nginx
GET https://api.betterplace.org/en/api_v4/users/250285/contact_data.json
```

Name and email for the given user.

*Only available if authenticated as a client, see [betterplace.org clients](../README.md#client-authentication):*


## Input Parameter

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Required/Optional</th>
    <th>Description</th>
  </tr>
  <tr>
    <th align="left">user_id</th>
    <td><code>250285</code></td>
    <td>required</td>
    <td>User-id as an integer number.</td>
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
      <th align="left">email</th>
      <td>string</td>
      <td>peter.paul@betterplace.org</td>
      <td>The email address of the user</td>
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
  "first_name": "Markus",
  "last_name": "Jo",
  "email": "mjo@betterplace.org"
}
```

