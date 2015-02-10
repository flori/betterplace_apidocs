
# Client Donation Pledges

```nginx
POST https://api.betterplace.org/de/api_v4/clients/Volksfreund/projects/1114/donation_pledges.json
```

Submit a donation pledge into the system. This will be transformed into a donation to the receiver.

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
    <th align="left">client_id</th>
    <td><code>Volksfreund</code></td>
    <td>required</td>
    <td>The betterplace.org-internal client permalink.</td>
  </tr>
  <tr>
    <th align="left">project_id</th>
    <td><code>1114</code></td>
    <td>required</td>
    <td>Project-id as an integer number ≥ 14.</td>
  </tr>
</table>

## Response Attributes

  <th colspan="4">No response example defined</th>
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
null
```

