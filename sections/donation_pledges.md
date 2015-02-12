
# Client Donation Pledges

```nginx
POST https://api.betterplace.org/de/api_v4/clients/Volksfreund/projects/1114/donation_pledges.json
```

Submit a donation pledge into the system. This will be transformed into
a donation to the receiver. The request has to be a POST request with a
JSON body.

A successful request will return HTTP status 202 (accepted). The
donation is then queued and will be processed by background workers.
Please notice, that this might take up to a few minutes, especially in
high traffic scenarios.

If an error occurs the HTTP return code will be 422 (unprocessable
entity). You can find the documentation on how errors are represented
at [POST error handling](../README.md#error-handling).

*Only available if authenticated as a client, see [betterplace.org clients](../README.md#client-authentication):*


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
    <td><code>1114</code></td>
    <td>yes</td>
    <td>Project-id as an integer number ≥ 14.</td>
  </tr>
</table>

## JSON Parameters

JSON parameters have to be provided in the body of the request. The parameters
are part of a flat JSON document without any nesting. Some parameters are
required, others are optional.

### Example

```json
{
  "first_name": "Max",
  "last_name": "Mustermann",
  "email": "mm@example.com",
  "amount_in_cents": 100,
  "reference": "djksbf23u4sjkdn234p",
  "street": "Rheinstrasse 202",
  "city": "Wiesbaden",
  "zip": "65185",
  "country_code": "DE"
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
    <th align="left">first_name</th>
    <td><code>Max</code></td>
    <td>string</td>
    <td>yes</td>
    <td>First name of the donor.</td>
  </tr>
  <tr>
    <th align="left">last_name</th>
    <td><code>Mustermann</code></td>
    <td>string</td>
    <td>yes</td>
    <td>Last name of the donor.</td>
  </tr>
  <tr>
    <th align="left">email</th>
    <td><code>mm@example.com</code></td>
    <td>string</td>
    <td>yes</td>
    <td>Email address of the donor. Only valid email addresses will be accepted.</td>
  </tr>
  <tr>
    <th align="left">amount_in_cents</th>
    <td><code>100</code></td>
    <td>number</td>
    <td>yes</td>
    <td>The amount of cents that are donated. Must be a positive integer.</td>
  </tr>
  <tr>
    <th align="left">reference</th>
    <td><code>djksbf23u4sjkdn234p</code></td>
    <td>string</td>
    <td>yes</td>
    <td>A unique identifier for this transaction. With this reference one can find the donation and its status later.</td>
  </tr>
  <tr>
    <th align="left">street</th>
    <td><code>Rheinstrasse 202</code></td>
    <td>string</td>
    <td>yes</td>
    <td>The street of the donors address. Used to issue a donation receipt if the donation is tax deductible.</td>
  </tr>
  <tr>
    <th align="left">city</th>
    <td><code>Wiesbaden</code></td>
    <td>string</td>
    <td>yes</td>
    <td>The city of the donors address. Used to issue a donation receipt if the donation is tax deductible.</td>
  </tr>
  <tr>
    <th align="left">zip</th>
    <td><code>65185</code></td>
    <td>string</td>
    <td>yes</td>
    <td>Zip code of the city or region the donor lives at. Used to issue a donation receipt if the donation is tax deductible.</td>
  </tr>
  <tr>
    <th align="left">country_code</th>
    <td><code>DE</code></td>
    <td>string</td>
    <td>yes</td>
    <td>ISO2 code of the country the donor lives in. Used to issue a donation receipt if the donation is tax deductible.</td>
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

