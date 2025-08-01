
# Opinions List

```Cirru
GET https://api.betterplace.org/de/api_v4/projects/1/opinions.json?facets=has_message%3Atrue&order=confirmed_at%3ADESC
```

A list of betterplace.org projects or fundraising event opinions (donate money).
There is no details view for opinions.

* Example for project opinions `…/api_v4/projects/1114/opinions.json`
* Example for fundraising event opinions `…/api_v4/fundraising_events/19267/opinions.json`

Results are contained in a *data* attribute.


## URL Parameters

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <th align="left">project_id</th>
    <td><code>1</code></td>
    <td>no</td>
<td>

Project id as an integer number.
This parameter is required in case you want to show project opinions.
Also check the URL example in the introduction.


</td>
  </tr>
  <tr>
    <th align="left">fundraising_event_id</th>
    <td><code>1</code></td>
    <td>no</td>
<td>

Fundraising Event id as an integer number.
This parameter is required in case you want to show fundraising event opinions.
Also check the URL example in the introduction.


</td>
  </tr>
  <tr>
    <th align="left">order</th>
    <td><code>confirmed_at:DESC</code></td>
    <td>no</td>
<td>

Order the result set.
<br>
It is strongly recommended to <strong>specify an order</strong> with each request.
The default order might change at any time without notice.
A recommended order is <code>confirmed_at:DESC</code>, which sorts the
project opinions by the confirmation time in descending order.
This is also the order of the opinions
list on the betterplae project details page</a>.<br>
<em>Other supported orders are:</em>
<ul>
<li><code>created_at:ASC/DESC</code>
<li><code>updated_at:ASC/DESC</code>
<li><code>confirmed_at:ASC/DESC</code>
<li><code>id:ASC/DESC</code>
<li><code>amount_in_cents:ASC/DESC</code>
</ul>
It is possible to set multiple order parameters.
<a href="../README.md#request-parameter-format">Learn how to format the parameter</a>.


</td>
  </tr>
  <tr>
    <th align="left">facets</th>
    <td><code>has_message:true</code></td>
    <td>no</td>
<td>

Filter the result set.
Documented and supported filters are:
<ul>
  <li><code>has_message:true/false</code> – did the donor add a message to her donation
  <li><code>company_donation:true/false</code> – is the donor a company
  <li><code>has_author_or_amount:true/false</code> – exclude anonymous donations with no amount shown
  <li><code>since:datetime</code> – filter for donations that are newer than a certain datetime
</ul>
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
      <td><code>number</code></td>
      <td><code>1</code></td>
<td>

An integer number ≥ 1

</td>
    </tr>
    <tr>
      <th align="left">created_at</th>
      <td><code>string</code></td>
      <td><code>"1994-11-05T13:15:30Z"</code></td>
<td>

DateTime (ISO8601 with Timezone)

</td>
    </tr>
    <tr>
      <th align="left">updated_at</th>
      <td><code>string</code></td>
      <td><code>"1994-11-05T13:15:30Z"</code></td>
<td>

DateTime (ISO8601 with Timezone)

</td>
    </tr>
    <tr>
      <th align="left">donated_amount_in_cents</th>
      <td><code>number</code></td>
      <td><code>5000</code></td>
<td>

The amount donated, but only if the user allowed the amount to be
visible. Most donation forms allow the donor to specify if they
want their amount to be visible. As a default, the donated amount
is visible.

Known issue: For forwarding donations (money that is forwarded from a fundraising event to a project)
this field is always empty, which is wrong.


</td>
    </tr>
    <tr>
      <th align="left">client_name</th>
      <td><code>string</code></td>
      <td><code>PAYBACK Spendenwelt</code></td>
<td>

Name of the related client, if available.


</td>
    </tr>
    <tr>
      <th align="left">score</th>
      <td><code>string</code></td>
      <td><code>positive</code></td>
<td>

DEPRECATED 2017-06-16 - Always returns "positive"


</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="author-ref" href="#author">
            ↓author
          </a>
        </th>
      <td><code>null &#124; object</code></td>
      <td><code>TODO</code></td>
<td>

Donor information, if available.


</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="backed_by_fundraising_event-ref" href="#backed_by_fundraising_event">
            ↓backed_by_fundraising_event
          </a>
        </th>
      <td><code>object</code></td>
      <td><code>TODO</code></td>
<td>

Information about the fundraising event through which the donation came in, if available.


</td>
    </tr>
    <tr>
      <th align="left">message</th>
      <td><code>null &#124; string</code></td>
      <td><code>"This is a great project. In spring 2007 I travelled around the area together with my children and …"</code></td>
<td>

An optional message by users.

The body is plain text potentially containing line-breaks.


</td>
    </tr>
    <tr>
      <th align="left">confirmed_at</th>
      <td><code>string</code></td>
      <td><code>"1994-11-05T13:15:30Z"</code></td>
<td>

DateTime (ISO8601 with Timezone)

</td>
    </tr>
  </table>

### <a id="author" href="#author-ref">↑Nested Attributes: author</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">author.id</th>
      <td><code>number</code></td>
      <td><code>1</code></td>
<td>

An integer number ≥ 1

</td>
    </tr>
    <tr>
      <th align="left">author.name</th>
      <td><code>null &#124; string</code></td>
      <td><code>"Till B."</code></td>
<td>

Display name of a betterplace.org user.
Possible formats: "Till B.", "T. Behnke", "Till Behnke".

In the case of donation-opinions the name might also be
empty/null for anonymous donations for anonymous donations.


</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="author.picture-ref" href="#author.picture">
            ↓author.picture
          </a>
        </th>
      <td><code>object</code></td>
      <td><code>//betterplace-assets.betterplace.org ↪/uploads/user/profile_picture ↪/000/000/001 ↪/fill_100x100_original_tb.jpg</code></td>
<td>

User profile picture or a fallback image

</td>
    </tr>
  </table>

### <a id="author.picture" href="#author.picture-ref">↑Nested Attributes: author.picture</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">author.picture.fallback</th>
      <td><code>boolean</code></td>
      <td><code>true</code></td>
<td>

Specifies whether a fallback image is given or not

</td>
    </tr>
  </table>

### <a id="backed_by_fundraising_event" href="#backed_by_fundraising_event-ref">↑Nested Attributes: backed_by_fundraising_event</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">backed_by_fundraising_event.id</th>
      <td><code>number</code></td>
      <td><code>1</code></td>
<td>

An integer number ≥ 1

</td>
    </tr>
    <tr>
      <th align="left">backed_by_fundraising_event.url</th>
      <td><code>string</code></td>
      <td><code>Lorem ipsum</code></td>
<td>

URL of the fundraising event


</td>
    </tr>
    <tr>
      <th align="left">backed_by_fundraising_event.title</th>
      <td><code>string</code></td>
      <td><code>Lorem ipsum</code></td>
<td>

Title of the fundraising event


</td>
    </tr>
    <tr>
      <th align="left">backed_by_fundraising_event.donor_count</th>
      <td><code>number</code></td>
      <td><code>100</code></td>
<td>

Number of donors who donated to the fundraising event


</td>
    </tr>
    <tr>
      <th align="left">backed_by_fundraising_event.sponsoring_name</th>
      <td><code>string</code></td>
      <td><code>Company XY</code></td>
<td>

Company name if it is a sponsored fundraising event


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
<th align="left">

project

</th>
<td>

Link to the project this opinion belongs to
(<a href="project_details.md">project details</a>)


</td>
    </tr>
    <tr>
<th align="left">

fundraising_event

</th>
<td>

Link to the fundraising event this opinion belongs to
(<a href="fundraising_event_details.md">fundraising event details</a>)


</td>
    </tr>
    <tr>
<th align="left">

author.platform

</th>
<td>

The user's profile on betterplace.org.
To view a user profile you have to be logged in.
This array is empty if the user has no useraccount
with betterplace.org but donated via one of our partner.


</td>
    </tr>
    <tr>
<th align="left">

author.contact_data

</th>
<td>

The user's contact data. Please note that you need to be
<a href="../README.md#client-api">authenticated as a client</a> with matching
access rights in order to see this information.


</td>
    </tr>
    <tr>
<th align="left">

author.picture.fill_100x100

</th>
<td>

100×100 Pixel

</td>
    </tr>
    <tr>
<th align="left">

author.picture.original

</th>
<td>

Maximum sized image. This is the original image with default-cropping or user-cropping applied.

</td>
    </tr>
    <tr>
<th align="left">

backed_by_fundraising_event.sponsoring_logo

</th>
<td>

Sponsoring Logo

</td>
    </tr>
</table>

## Response Example

```json
{
  "current_page": 1,
  "offset": 0,
  "per_page": 3,
  "total_entries": 1,
  "total_pages": 1,
  "data": [
    {
      "id": 1,
      "created_at": "2025-06-26T13:12:26+02:00",
      "updated_at": "2025-06-26T13:12:26+02:00",
      "donated_amount_in_cents": 50000,
      "score": "positive",
      "author": {
        "name": "Anonym",
        "picture": {
          "fallback": true,
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://betterplace-assets.betterplace.org/assets/default/donation_profile_picture/fill_100x100_default.png"
            },
            {
              "rel": "original",
              "href": "https://betterplace-assets.betterplace.org/assets/default/donation_profile_picture/fill_100x100_default.png"
            }
          ]
        },
        "links": []
      },
      "message": "with &lt;3",
      "confirmed_at": "2025-06-26T13:12:26+02:00",
      "links": [
        {
          "rel": "project",
          "href": "https://api.betterplace.dev/de/api_v4/projects/1.json"
        }
      ]
    }
  ]
}
```

