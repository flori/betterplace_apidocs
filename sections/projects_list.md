
# Projects List ⇄ [Details](project_details.md)

```Cirru
GET https://api.betterplace.org/de/api_v4/projects.json?around=10997+Berlin%2C+Germany&around_distance=25km&facets=completed%3Afalse&nelat=51.123&nelng=12.123&order=rank%3ADESC&q=Skateistan&scope=location&swlat=51.001&swlng=12.001
```

A list of betterplace.org projects (donate money).
Results are contained in a *data* attribute.

**For [betterplace.org clients](../README.md#client-api):**
Use this resource as follows: `/clients/PERMALINK/projects.json`.

To guarantee stable search results,
all clients are required to specify at least one facet and order with each request as explained
below.


## URL Parameters

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Required</th>
    <th>Description</th>
  </tr>
  <tr>
    <th align="left">scope</th>
    <td><code>location</code></td>
    <td>no</td>
<td>

Use the scope to specify how the search query <code>q</code> should behave:
<ul>
<li>"no scope" (default) performs a full text search
<li><code>human_name</code> searches only on the manager-fullname and carrier-fullname.
  Use this to get all entities by "Unicef" or by "Till Behnke".
<li><code>location</code> does a reverse geocoding lookup.
  This lookup returns a bounding box. We transform this bounding box to a
  rectangle that is large enough to encapsulate the whole bounding box.
  We then return all entities that are within this rectangle.
</ul>
<a href="../README.md#request-parameter-format">Learn how to format the parameter</a>.


</td>
  </tr>
  <tr>
    <th align="left">around</th>
    <td><code>10997 Berlin, Germany</code></td>
    <td>no</td>
<td>

Order the results by the distance to the given location from near to far.
<br>
Location can be provided as …
<br>
<em>… Lat/Lng:</em> <code>52.50,13.45</code>
<br>
<em>… ZIP:</em> <code>10997 Berlin, Germany</code>.
We use the centre of the ZIP code area as center for the search.
Please add enough context information (like the Country name)
so google knows what place you are looking for.
<br>
<em>… any location search:</em> All queries other than a float tuple
are sent to the google location service. For the provided response we
take a fitting lat/lng value as center of the search. So in theory,
you can use any search that works for google maps.
<br>
Check the <code>around_location</code> to see what latitude/longitude
values have been used for the query.


</td>
  </tr>
  <tr>
    <th align="left">around_distance</th>
    <td><code>25km</code></td>
    <td>no</td>
<td>

In combination with the <code>around</code> parameter the search will be
limited to results whose location is closer than the given value to the
location provided through the <code>around</code> parameter. Possible
values are all integer values followed by <code>m</code> for meters or
<code>km</code> for kilometers, e.g. <code>1000m</code>, <code>1km</code>.
<br>
When <code>around_distance</code> is given without <code>around</code> it
will be ignored.


</td>
  </tr>
  <tr>
    <th align="left">nelat</th>
    <td><code>51.123</code></td>
    <td>no</td>
<td>

For geographic bound filterning: The northeast corner's latitude.

</td>
  </tr>
  <tr>
    <th align="left">nelng</th>
    <td><code>12.123</code></td>
    <td>no</td>
<td>

For geographic bound filterning: The northeast corner's longitude.

</td>
  </tr>
  <tr>
    <th align="left">swlat</th>
    <td><code>51.001</code></td>
    <td>no</td>
<td>

For geographic bound filterning: The southwest corner's latitude.

</td>
  </tr>
  <tr>
    <th align="left">swlng</th>
    <td><code>12.001</code></td>
    <td>no</td>
<td>

For geographic bound filterning: The southwest corner's longitude.

</td>
  </tr>
  <tr>
    <th align="left">q</th>
    <td><code>Skateistan</code></td>
    <td>no</td>
<td>

Search query. The searches behaviour is based on the scope.

</td>
  </tr>
  <tr>
    <th align="left">facets</th>
    <td><code>completed:false</code></td>
    <td>no</td>
<td>

Filter the result set.
<br>
It is strongly recommended to <strong>specify facets</strong> with each request.
A recommended set of facets is <code>tax_deductible:true| completed:false|
closed:false| prohibit_donations:false</code> (without the spaces) which
only shows active projects that can receive donations.
<br>
<em>Supported filters are:</em>
<ul>
<li><code>tax_deductible:true/false</code>
<li><code>completed:true/false</code> –
is this project fully financed (100 %)? See <code>completed_at</code>
<li><code>closed:true/false</code> –
has this project been closed by the project manager? See <code>closed_at</code>
<li><code>prohibit_donations:true/false</code> –
are donations to this project forbidden at the moment? Closed and blocked projects
will always return true, for example.
</ul>
It is possible to set multiple facet filters.
<a href="../README.md#request-parameter-format">Learn how to format the parameter</a>.


</td>
  </tr>
  <tr>
    <th align="left">order</th>
    <td><code>rank:DESC</code></td>
    <td>no</td>
<td>

Order the result set.
<br>
It is strongly recommended to <strong>specify an order</strong> with each request.
The default order might change at any time without notice.
A recommended order is <code>score:desc | completed:asc | rank:desc|
last_donation_at:desc</code> (without the spaces). This is the order betterplace.org uses
<a href="http://www.betterplace.org/en/projects/list">for the project list</a>.
<br>
<em>Supported orders are:</em>
<ul>
<li><code>score:ASC/DESC</code> – as provided by the search engine whenever a search term
is given.
<li><code>rank:ASC/DESC</code> – a betterplace.org-specific, platform-wide activity indicator
<li><code>progress_percentage:ASC/DESC</code> – financing goal fulfillment given as 0 to 100
<li><code>tax_deductible:ASC/DESC</code> – true (1) or false (0)
<li><code>completed:ASC/DESC</code> – true (1) or false (0)
<li><code>created_at:ASC/DESC</code> and <code>updated_at:ASC/DESC</code>
<li><code>last_donation_at:ASC/DESC</code>
<li><code>id:ASC/DESC</code>
</ul>
It is possible to set multiple order parameters.
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

DateTime (ISO8601 with Timezone) when the project was created by the
project manager.


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
      <th align="left">latitude</th>
      <td><code>number</code></td>
      <td><code>52.499007</code></td>
<td>

Decimal degrees based on user input

</td>
    </tr>
    <tr>
      <th align="left">longitude</th>
      <td><code>number</code></td>
      <td><code>13.44947</code></td>
<td>

Decimal degrees based on user input

</td>
    </tr>
    <tr>
      <th align="left">street</th>
      <td><code>null &#124; string</code></td>
      <td><code>"Schlesische Straße 26"</code></td>
<td>

Street address

</td>
    </tr>
    <tr>
      <th align="left">zip</th>
      <td><code>null &#124; string</code></td>
      <td><code>"10997"</code></td>
<td>

ZIP code

</td>
    </tr>
    <tr>
      <th align="left">city</th>
      <td><code>null &#124; string</code></td>
      <td><code>"Berlin"</code></td>
<td>

Name of the city

</td>
    </tr>
    <tr>
      <th align="left">country</th>
      <td><code>null &#124; string</code></td>
      <td><code>"Deutschland"</code></td>
<td>

Name of the country

</td>
    </tr>
    <tr>
      <th align="left">content_updated_at</th>
      <td><code>string</code></td>
      <td><code>"1994-11-05T13:15:30Z"</code></td>
<td>

DateTime (ISO8601 with Timezone)

</td>
    </tr>
    <tr>
      <th align="left">activated_at</th>
      <td><code>null &#124; string</code></td>
      <td><code>"1994-11-05T13:15:30Z"</code></td>
<td>

DateTime (ISO8601 with Timezone) when the project was activated
by us, otherwise it is null.


</td>
    </tr>
    <tr>
      <th align="left">title</th>
      <td><code>string</code></td>
      <td><code></code></td>
<td>

Max 50 character

</td>
    </tr>
    <tr>
      <th align="left">description</th>
      <td><code>string</code></td>
      <td><code></code></td>
<td>

A description of the project. This may contain any of the following
HTML tags: ```a, b, br, div, em, i, iframe, img, li, ol, p, strong, ul```.


</td>
    </tr>
    <tr>
      <th align="left">summary</th>
      <td><code>string</code></td>
      <td><code></code></td>
<td>

A short summary of the project..


</td>
    </tr>
    <tr>
      <th align="left">tax_deductible</th>
      <td><code>boolean</code></td>
      <td><code>true</code></td>
<td>

True if the project marked as tax deductible.
If so, Users can request a tax receipt that can be used
with the German tax authorities.
[More about this](http://www.betterplace.org/c/hilfe/projekt-steuerlich-absetzbar/).


</td>
    </tr>
    <tr>
      <th align="left">donations_prohibited</th>
      <td><code>boolean</code></td>
      <td><code>false</code></td>
<td>

True if the project must not receive donations. This might happen, for example,
if a tax receipt of German tax authorities ran out.

Please check this flag whenever you display a donation button.
Should you show a button for a project that cannot receive donations
the user will open the donation form and see an error message on
betterplace.org instead!


</td>
    </tr>
    <tr>
      <th align="left">completed_at</th>
      <td><code>string</code></td>
      <td><code>"1994-11-05T13:15:30Z"</code></td>
<td>

DateTime (ISO8601 with Timezone) of the moment the project was fully
funded (100% `progress_percentage`).

A completed project may still be active (as in not closed).
See `closed_at for details.


</td>
    </tr>
    <tr>
      <th align="left">closed_at</th>
      <td><code>string</code></td>
      <td><code>"1994-11-05T13:15:30Z"</code></td>
<td>

DateTime (ISO8601 with Timezone) when the project was closed by the
project manager.

A closed project does not have to be fully funded.
See `completed_at` for details.


</td>
    </tr>
    <tr>
      <th align="left">open_amount_in_cents</th>
      <td><code>number</code></td>
      <td><code>12382</code></td>
<td>

How many cents are needed to complete the project

</td>
    </tr>
    <tr>
      <th align="left">donated_amount_in_cents</th>
      <td><code>number</code></td>
      <td><code>12382</code></td>
<td>

How many cents are donated already.
This includes:
- sum of all donations
- sum of all forwardings to the project
- external donations

Subtracting:
- backwardings from the project


</td>
    </tr>
    <tr>
      <th align="left">positive_opinions_count</th>
      <td><code>number</code></td>
      <td><code>13</code></td>
<td>

Number of positive opinions that are given to a project without a donation.
Those are plain opinions as well as visitor opinions.

DEPRECATED 2017-06-23

Use `donations_count` and `comments_count` instead. There is no distinction
between positive and negative comments any more, all opinions were converted
into comments.


</td>
    </tr>
    <tr>
      <th align="left">negative_opinions_count</th>
      <td><code>number</code></td>
      <td><code>0</code></td>
<td>

Number of *negative* opinions (usually 0) that are given to a project without a donation.
Those are plain opinions as well as visitor opinions.
Critical opinions are part of the betterplace.org
["Web of trust"](http://www.betterplace.org/c/hilfe/woran-erkenne-ich-dass-ein-projekt-vertrauenswurdig-ist/).

DEPRECATED 2017-06-23

Always returns 0. Don't use this field any more.


</td>
    </tr>
    <tr>
      <th align="left">donations_count</th>
      <td><code>number</code></td>
      <td><code>42</code></td>
<td>

Count of confirmed donations for this project

</td>
    </tr>
    <tr>
      <th align="left">newsletter_subscriptions_count</th>
      <td><code>number</code></td>
      <td><code>42</code></td>
<td>

Count of active newsletter subscriptions for this project.

EXPERIMENTAL 2019-02-21

Can be removed at any time. Use with caution


</td>
    </tr>
    <tr>
      <th align="left">comments_count</th>
      <td><code>number</code></td>
      <td><code>24</code></td>
<td>

Count of all comments for this project. This contains positive and negative
reviews of the project, questions and answers by the project manager, as
well as comments from users.


</td>
    </tr>
    <tr>
      <th align="left">donor_count</th>
      <td><code>number</code></td>
      <td><code>46</code></td>
<td>

⚠️ DEPRECATED!
This value is deprecated and will be removed after 2021-01-01.
Please update your code to use the `donations_count`.

Number of unique donors, based on the payment-email-address


</td>
    </tr>
    <tr>
      <th align="left">progress_percentage</th>
      <td><code>number</code></td>
      <td><code>82</code></td>
<td>

% financed. Note: We have legacy projects with substantial
donation needs (pre ~2014). This percentage includes those needs.


</td>
    </tr>
    <tr>
      <th align="left">incomplete_need_count</th>
      <td><code>number</code></td>
      <td><code>6</code></td>
<td>

Number of needs that still need donations

</td>
    </tr>
    <tr>
      <th align="left">completed_need_count</th>
      <td><code>number</code></td>
      <td><code>12</code></td>
<td>

Number of completed needs

</td>
    </tr>
    <tr>
      <th align="left">blog_post_count</th>
      <td><code>number</code></td>
      <td><code>8</code></td>
<td>

Number of blogposts (all types)

</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="contact-ref" href="#contact">
            ↓contact
          </a>
        </th>
      <td><code>object</code></td>
      <td><code>TODO</code></td>
<td>

The public face of the project / project manager

</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="carrier-ref" href="#carrier">
            ↓carrier
          </a>
        </th>
      <td><code>null &#124; object</code></td>
      <td><code>TODO</code></td>
<td>

The organisation that carries this project

</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="profile_picture-ref" href="#profile_picture">
            ↓profile_picture
          </a>
        </th>
      <td><code>null &#124; object</code></td>
      <td><code></code></td>
<td>

TODO

</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="active_matching_fund-ref" href="#active_matching_fund">
            ↓active_matching_fund
          </a>
        </th>
      <td><code>null &#124; object</code></td>
      <td><code>TODO</code></td>
<td>

**DEPRECATED** Do not use this data. We will remove the nested
matching fund data in the future.

To get this data follow the active_matching_fund link and retrieve
the data from the appropriate endpoint.


</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="closed_notice-ref" href="#closed_notice">
            ↓closed_notice
          </a>
        </th>
      <td><code>null &#124; object</code></td>
      <td><code>TODO</code></td>
<td>

**This is an experimental feature and is still under heavy development. Please use it with caution.**


</td>
    </tr>
  </table>

### <a id="contact" href="#contact-ref">↑Nested Attributes: contact</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">contact.id</th>
      <td><code>number</code></td>
      <td><code>1</code></td>
<td>

An integer number ≥ 1

</td>
    </tr>
    <tr>
      <th align="left">contact.name</th>
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
          <a id="contact.picture-ref" href="#contact.picture">
            ↓contact.picture
          </a>
        </th>
      <td><code>object</code></td>
      <td><code>//betterplace-assets.betterplace.org ↪/uploads/user/profile_picture ↪/000/000/001 ↪/fill_100x100_original_tb.jpg</code></td>
<td>

User profile picture or a fallback image

</td>
    </tr>
  </table>

### <a id="contact.picture" href="#contact.picture-ref">↑Nested Attributes: contact.picture</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">contact.picture.fallback</th>
      <td><code>boolean</code></td>
      <td><code>true</code></td>
<td>

Specifies whether a fallback image is given or not

</td>
    </tr>
  </table>

### <a id="carrier" href="#carrier-ref">↑Nested Attributes: carrier</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">carrier.id</th>
      <td><code>number</code></td>
      <td><code>1</code></td>
<td>

An integer number ≥ 1

</td>
    </tr>
    <tr>
      <th align="left">carrier.name</th>
      <td><code>string</code></td>
      <td><code>"Till B."</code></td>
<td>

The carrier can be an organisation or user.

</td>
    </tr>
    <tr>
      <th align="left">carrier.city</th>
      <td><code>string</code></td>
      <td><code>"Berlin"</code></td>
<td>

The city in which the carrier resides

</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="carrier.picture-ref" href="#carrier.picture">
            ↓carrier.picture
          </a>
        </th>
      <td><code>object</code></td>
      <td><code>https://betterplace-assets.betterplace.org/…</code></td>
<td>

The organisation logo, user profile picture or a fallback image

</td>
    </tr>
  </table>

### <a id="carrier.picture" href="#carrier.picture-ref">↑Nested Attributes: carrier.picture</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">carrier.picture.fallback</th>
      <td><code>boolean</code></td>
      <td><code>true</code></td>
<td>

Specifies whether a fallback image is given or not

</td>
    </tr>
  </table>

### <a id="profile_picture" href="#profile_picture-ref">↑Nested Attributes: profile_picture</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">profile_picture.fallback</th>
      <td><code>boolean</code></td>
      <td><code>true</code></td>
<td>

Specifies whether a fallback image is given or not

</td>
    </tr>
  </table>

### <a id="active_matching_fund" href="#active_matching_fund-ref">↑Nested Attributes: active_matching_fund</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">active_matching_fund.id</th>
      <td><code>number</code></td>
      <td><code>1</code></td>
<td>

An integer number ≥ 1

</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.created_at</th>
      <td><code>string</code></td>
      <td><code>"1994-11-05T13:15:30Z"</code></td>
<td>

DateTime (ISO8601 with Timezone)

</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.updated_at</th>
      <td><code>string</code></td>
      <td><code>"1994-11-05T13:15:30Z"</code></td>
<td>

DateTime (ISO8601 with Timezone)

</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.activated_at</th>
      <td><code>null &#124; string</code></td>
      <td><code>"1994-11-05T13:15:30Z"</code></td>
<td>

DateTime (ISO8601 with Timezone)

</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.title</th>
      <td><code>string</code></td>
      <td><code>ACME Matching Everything</code></td>
<td>

Our matching fund's name

</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.description</th>
      <td><code>string</code></td>
      <td><code>It's all about matching donations…</code></td>
<td>

The description of the matching fund

</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.company_name</th>
      <td><code>string</code></td>
      <td><code>ACME</code></td>
<td>

The company that supports it

</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.client_id</th>
      <td><code>string</code></td>
      <td><code>clientname</code></td>
<td>

The client to which the matching fund belongs

</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.provided_amount_in_cents</th>
      <td><code>number</code></td>
      <td><code>12300</code></td>
<td>

The amount in cents the company provided to be matched

</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.donated_amount_in_cents</th>
      <td><code>number</code></td>
      <td><code>12300</code></td>
<td>

The amount in cents the company already donated

</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.state</th>
      <td><code>string</code></td>
      <td><code>activated</code></td>
<td>

Current state of this matching fund: either activated or closed

</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.logo_url</th>
      <td><code>string</code></td>
      <td><code>http://example.com/images/logo.png</code></td>
<td>

The URL of the logo image.

</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.maximum_matching_amount_in_cents</th>
      <td><code>number</code></td>
      <td><code>10000</code></td>
<td>

Up to this amount donations get matched by the matching fund

</td>
    </tr>
  </table>

### <a id="closed_notice" href="#closed_notice-ref">↑Nested Attributes: closed_notice</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">closed_notice.text</th>
      <td><code>null &#124; string</code></td>
      <td><code>Thank you for the successful funding.</code></td>
<td>

A close notice from the project manager

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

self

</th>
<td>

Link to this resource itself
(<a href="project_details.md">project details</a>)


</td>
    </tr>
    <tr>
<th align="left">

platform

</th>
<td>

Permalink to betterplace.org

</td>
    </tr>
    <tr>
<th align="left">

opinions

</th>
<td>

Link to <a href="opinions_list.md">donations/opinions list</a>


</td>
    </tr>
    <tr>
<th align="left">

pictures

</th>
<td>

Link to <a href="project_pictures_list.md">project pictures list</a>


</td>
    </tr>
    <tr>
<th align="left">

needs

</th>
<td>

Link to <a href="needs_list.md">project needs list</a>


</td>
    </tr>
    <tr>
<th align="left">

blog_posts

</th>
<td>

Link to <a href="blog_posts_list.md">blog posts list</a>


</td>
    </tr>
    <tr>
<th align="left">

active_matching_fund

</th>
<td>

Link to <a href="matching_fund_details.md">matching fund</a>


</td>
    </tr>
    <tr>
<th align="left">

video

</th>
<td>

Link to a youtube video of this project


</td>
    </tr>
    <tr>
<th align="left">

matching_funds

</th>
<td>

Link to <a href="matching_funds_list.md">matching funds list</a>


</td>
    </tr>
    <tr>
<th align="left">

categories

</th>
<td>

Link to <a href="categories_list.md">categories list</a>


</td>
    </tr>
    <tr>
<th align="left">

new_client_donation

</th>
<td>

Link to the donation form. Templated, needs insertion of the client_id.


</td>
    </tr>
    <tr>
<th align="left">

new_donation

</th>
<td>

Link to the regular donation form.


</td>
    </tr>
    <tr>
<th align="left">

contact.platform

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

contact.contact_data

</th>
<td>

The user's contact data. Please note that you need to be
<a href="../README.md#client-api">authenticated as a client</a> with matching
access rights in order to see this information.


</td>
    </tr>
    <tr>
<th align="left">

contact.picture.fill_100x100

</th>
<td>

100×100 Pixel

</td>
    </tr>
    <tr>
<th align="left">

contact.picture.original

</th>
<td>

Maximum sized image. This is the original image with default-cropping or user-cropping applied.

</td>
    </tr>
    <tr>
<th align="left">

carrier.self

</th>
<td>

Link to this resource itself
(<a href="organisation_details.md">organisation details</a>)
Note: Since the there is no api for users yet, this is only
set for organisations.


</td>
    </tr>
    <tr>
<th align="left">

carrier.picture.fill_100x100

</th>
<td>

100×100 Pixel

</td>
    </tr>
    <tr>
<th align="left">

carrier.picture.original

</th>
<td>

Maximum sized image. This is the original image with default-cropping or user-cropping applied.

</td>
    </tr>
    <tr>
<th align="left">

profile_picture.fill_960x500

</th>
<td>

950×500 Pixel

</td>
    </tr>
    <tr>
<th align="left">

profile_picture.fill_730x380

</th>
<td>

730×380 Pixel

</td>
    </tr>
    <tr>
<th align="left">

profile_picture.fill_618x322

</th>
<td>

618×322 Pixel / DEPRECATED, will be removed after 5/2015

</td>
    </tr>
    <tr>
<th align="left">

profile_picture.fill_410x214

</th>
<td>

410×214 Pixel

</td>
    </tr>
    <tr>
<th align="left">

profile_picture.fill_270x141

</th>
<td>

270×141 Pixel / DEPRECATED, will be removed after 5/2015

</td>
    </tr>
    <tr>
<th align="left">

profile_picture.original

</th>
<td>

Maximum sized image. This is the original image with default-cropping or user-cropping applied.

</td>
    </tr>
    <tr>
<th align="left">

active_matching_fund.self

</th>
<td>

Link to this resource itself
(<a href="matching_fund_details.md">matching fund details</a>)


</td>
    </tr>
    <tr>
<th align="left">

active_matching_fund.platform

</th>
<td>

Permalink to betterplace.org

</td>
    </tr>
    <tr>
<th align="left">

active_matching_fund.projects

</th>
<td>

Link to the <a href="projects_list.md">list of projects</a>
belonging to this matching fund


</td>
    </tr>
    <tr>
<th align="left">

active_matching_fund.documentation

</th>
<td>

Link to this resource in the documentation


</td>
    </tr>
    <tr>
<th align="left">

closed_notice.call_to_action

</th>
<td>

A link to a final blog post, the next project url or any other followup
information for the donors.


</td>
    </tr>
</table>

## Response Example

```json
{
  "total_entries": 3,
  "offset": 0,
  "total_pages": 1,
  "current_page": 1,
  "per_page": 3,
  "data": [
    {
      "id": 6233,
      "created_at": "2011-02-25T08:48:43+01:00",
      "updated_at": "2021-05-17T20:10:05+02:00",
      "latitude": 11.55883121490479,
      "longitude": 104.9174423217773,
      "street": null,
      "zip": null,
      "city": "Phnom Penh",
      "country": "Kambodscha",
      "content_updated_at": "2021-03-15T11:04:58+01:00",
      "activated_at": "2011-02-25T09:03:15+01:00",
      "title": "Skateistan Kambodscha",
      "description": "<div>Im März 2011 wurde durch Skateistan Kambodscha der erste Skatepark des Landes in Phnom Penh eröffnet. Seit dem können benachteiligte Kinder und Jugendliche an sechs Tagen der Woche an Skateboardstunden und kreativen Bildungsmaßnahmen teilnehmen. <br><br>Skateistan Kambodscha benutzt Skateboarden als ein Instrument zur Starkmachung in Phnom Penh. Diese non-profit Organisation beschäftigt sich jede Woch mit rund 300 Jugendlichenen Kambodschanern zwischen fünf und 18 Jahren. Die Hälfte der Schüler sind weiblich und kommen aus armen Verhältnissen. </div><div><br></div><div>Skateboarding ist eine niedrigschwellige Aktivität, an der Mädchen und Jungen mit unterschiedlichen Hintergründen und Fähigkeiten teilnehmen können.  Hier können die Kinder das ganze Jahr über skateboarden, an verschiedenen Sport- und Bildungsangeboten teilnehmen und die Bücherei nutzen. Durch die bei Skateistan angebotenen Möglichkeiten zur Freizeitgestaltung können die  Kinder und Jugendlichen neue Freundschaften schließen, mehr Selbstvertrauen gewinnen und spielerisch neue Fähigkeiten erlernen. </div><div><br></div><div>Skateboarden ist eine inklusive Sportart - wir arbeiten mit verschiedenen Partnerorganisationen zusammen um Kindern und Jugendlichen den Zugang zum skateboarden zu ermöglichen. Durch die Partnerschaft mit Pour un Sourire d'Enfant (PSE), Friends Intl. und Tiny Toones können wir gefährdete Kinder und Jugendliche auch mit schon vorhandenen Hilfsangeboten in Verbindung bringen.<br> </div><div> Anfang 2019 wurde unsere neue Bibliothek vervollständigt und den Schülern vorgestellt. Über 100 Bücher und vier Computer wurden in dem neuen Lernbereich zur Verfügung gestellt. <br><br>\n</div><div>Unterstützen Sie Skateistan Kambodscha und helfen Sie uns dabei, Kindern und Jugendlichen in Kambodscha einen sicheren Ort für ihre persönliche Entwicklung zu geben. </div><div><br></div>",
      "summary": "Bei Skateistan Kambodscha haben 300 Kinder und Jugendliche wöchentlich die Möglichkeit, zu skateboarden und an Bildungsmaßnahmen teilzunehmen.",
      "tax_deductible": true,
      "donations_prohibited": true,
      "completed_at": null,
      "closed_at": "2021-03-15T11:04:58+01:00",
      "open_amount_in_cents": 112296,
      "donated_amount_in_cents": 861004,
      "positive_opinions_count": 64,
      "negative_opinions_count": 0,
      "donations_count": 64,
      "newsletter_subscriptions_count": 29,
      "comments_count": 0,
      "donor_count": 61,
      "progress_percentage": 88,
      "incomplete_need_count": 4,
      "completed_need_count": 19,
      "blog_post_count": 39,
      "contact": {
        "id": 287126,
        "name": "Louie Groß (display)",
        "picture": {
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://betterplace-assets.betterplace.org/uploads/user/profile_picture/000/287/126/fill_100x100_bp1584575045_Skateistan_facebook-02.png"
            },
            {
              "rel": "original",
              "href": "https://betterplace-assets.betterplace.org/uploads/user/profile_picture/000/287/126/crop_original_bp1584575045_Skateistan_facebook-02.png"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.org/de/users/287126"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/de/api_v4/users/287126/contact_data.json"
          }
        ]
      },
      "carrier": {
        "id": 1054,
        "name": "Skateistan",
        "city": "Berlin",
        "picture": {
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://betterplace-assets.betterplace.org/uploads/organisation/profile_picture/000/001/054/fill_100x100_bp1523439289_Skateistan_facebook-01.png"
            },
            {
              "rel": "original",
              "href": "https://betterplace-assets.betterplace.org/uploads/organisation/profile_picture/000/001/054/crop_original_bp1523439289_Skateistan_facebook-01.png"
            }
          ]
        },
        "links": [
          {
            "rel": "self",
            "href": "https://api.betterplace.org/de/api_v4/organisations/1054.json"
          }
        ]
      },
      "profile_picture": {
        "links": [
          {
            "rel": "fill_960x500",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/006/233/fill_960x500_bp1584531889_original_327569_368768896527128_1081473646_o.jpg"
          },
          {
            "rel": "fill_730x380",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/006/233/fill_730x380_bp1584531889_original_327569_368768896527128_1081473646_o.jpg"
          },
          {
            "rel": "fill_618x322",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/006/233/fill_618x322_bp1584531889_original_327569_368768896527128_1081473646_o.jpg"
          },
          {
            "rel": "fill_410x214",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/006/233/fill_410x214_bp1584531889_original_327569_368768896527128_1081473646_o.jpg"
          },
          {
            "rel": "fill_270x141",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/006/233/fill_270x141_bp1584531889_original_327569_368768896527128_1081473646_o.jpg"
          },
          {
            "rel": "original",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/006/233/crop_original_bp1584531889_original_327569_368768896527128_1081473646_o.jpg"
          }
        ]
      },
      "active_matching_fund": null,
      "closed_notice": null,
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/projects/6233.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/projects/6233-skateistan-kambodscha"
        },
        {
          "rel": "opinions",
          "href": "https://api.betterplace.org/de/api_v4/projects/6233/opinions.json"
        },
        {
          "rel": "pictures",
          "href": "https://api.betterplace.org/de/api_v4/projects/6233/pictures.json"
        },
        {
          "rel": "needs",
          "href": "https://api.betterplace.org/de/api_v4/projects/6233/needs.json"
        },
        {
          "rel": "blog_posts",
          "href": "https://api.betterplace.org/de/api_v4/projects/6233/blog_posts.json"
        },
        {
          "rel": "matching_funds",
          "href": "https://api.betterplace.org/de/api_v4/matching_funds.json?project_id=6233"
        },
        {
          "rel": "categories",
          "href": "https://api.betterplace.org/de/api_v4/projects/6233/categories.json"
        },
        {
          "rel": "new_client_donation",
          "href": "https://www.betterplace.org/de/donate/%7Bclient_id%7D/projects/6233",
          "templated": true
        },
        {
          "rel": "new_donation",
          "href": "https://www.betterplace.org/de/donate/platform/projects/6233"
        }
      ]
    },
    {
      "id": 60749,
      "created_at": "2018-02-22T20:01:23+01:00",
      "updated_at": "2021-05-17T20:21:38+02:00",
      "latitude": 34.5553494,
      "longitude": 69.207486,
      "street": "Weststraße 193",
      "zip": "",
      "city": "Kabul",
      "country": "Afghanistan",
      "content_updated_at": "2021-03-15T11:04:05+01:00",
      "activated_at": "2018-02-23T09:52:39+01:00",
      "title": "Unterstütze Sport &amp; Bildung für Kinder und Jugendliche mit Skateboarding",
      "description": "<div>▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾▾<br><strong>Wir brauchen eure Unterstützung für alle Kinder und Jugendlichen, denen wir das Skaten ermöglichen möchten. Mach mit SKATE &amp; EDUCATE. <br><br>&gt;&gt;&gt; Spende 5€ um einen Unterrichtstag zu unterstützen &lt;&lt;&lt;</strong><br><br>Wir wollen, dass Skateistan noch mehr Kindern und Jugendlichen die Möglichkeit geben kann, skaten zu lernen. Skateistan glaubt daran, dass alle Kinder und Jugendlichen die gleichen Rechte haben, sicher zu sein, Sport zu treiben, zur Schule zu gehen, selbstsicher zu sein und eine Führungskraft zu werden.</div>",
      "summary": "Wir brauchen eure Unterstützung für alle Kinder und Jugendlichen, denen wir das Skaten ermöglichen möchten. Mach mit SKATE &amp; EDUCATE. \r\n\r\n&gt; Spende 5€ um einen Unterrichtstag zu unterstützen ",
      "tax_deductible": true,
      "donations_prohibited": true,
      "completed_at": null,
      "closed_at": "2021-03-15T11:04:05+01:00",
      "open_amount_in_cents": 966000,
      "donated_amount_in_cents": 34000,
      "positive_opinions_count": 5,
      "negative_opinions_count": 0,
      "donations_count": 5,
      "newsletter_subscriptions_count": 4,
      "comments_count": 0,
      "donor_count": 5,
      "progress_percentage": 3,
      "incomplete_need_count": 9,
      "completed_need_count": 1,
      "blog_post_count": 1,
      "contact": {
        "id": 506119,
        "name": "Simon ?‍?‍?Familie Emoji (display)",
        "picture": {
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://betterplace-assets.betterplace.org/uploads/user/profile_picture/000/506/119/fill_100x100_bp1584585415_Profilbild_Skateistan.png"
            },
            {
              "rel": "original",
              "href": "https://betterplace-assets.betterplace.org/uploads/user/profile_picture/000/506/119/crop_original_bp1584585415_Profilbild_Skateistan.png"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.org/de/users/506119"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/de/api_v4/users/506119/contact_data.json"
          }
        ]
      },
      "carrier": {
        "id": 1054,
        "name": "Skateistan",
        "city": "Berlin",
        "picture": {
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://betterplace-assets.betterplace.org/uploads/organisation/profile_picture/000/001/054/fill_100x100_bp1523439289_Skateistan_facebook-01.png"
            },
            {
              "rel": "original",
              "href": "https://betterplace-assets.betterplace.org/uploads/organisation/profile_picture/000/001/054/crop_original_bp1523439289_Skateistan_facebook-01.png"
            }
          ]
        },
        "links": [
          {
            "rel": "self",
            "href": "https://api.betterplace.org/de/api_v4/organisations/1054.json"
          }
        ]
      },
      "profile_picture": {
        "links": [
          {
            "rel": "fill_960x500",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/060/749/fill_960x500_bp1584558480_Skateistan_Girl_Power.jpg"
          },
          {
            "rel": "fill_730x380",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/060/749/fill_730x380_bp1584558480_Skateistan_Girl_Power.jpg"
          },
          {
            "rel": "fill_618x322",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/060/749/fill_618x322_bp1584558480_Skateistan_Girl_Power.jpg"
          },
          {
            "rel": "fill_410x214",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/060/749/fill_410x214_bp1584558480_Skateistan_Girl_Power.jpg"
          },
          {
            "rel": "fill_270x141",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/060/749/fill_270x141_bp1584558480_Skateistan_Girl_Power.jpg"
          },
          {
            "rel": "original",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/060/749/crop_original_bp1584558480_Skateistan_Girl_Power.jpg"
          }
        ]
      },
      "active_matching_fund": null,
      "closed_notice": null,
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/projects/60749.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/projects/60749-unterstuetze-sport-bildung-fuer-kinder-und-jugendliche-mit-skateboarding"
        },
        {
          "rel": "opinions",
          "href": "https://api.betterplace.org/de/api_v4/projects/60749/opinions.json"
        },
        {
          "rel": "pictures",
          "href": "https://api.betterplace.org/de/api_v4/projects/60749/pictures.json"
        },
        {
          "rel": "needs",
          "href": "https://api.betterplace.org/de/api_v4/projects/60749/needs.json"
        },
        {
          "rel": "blog_posts",
          "href": "https://api.betterplace.org/de/api_v4/projects/60749/blog_posts.json"
        },
        {
          "rel": "matching_funds",
          "href": "https://api.betterplace.org/de/api_v4/matching_funds.json?project_id=60749"
        },
        {
          "rel": "categories",
          "href": "https://api.betterplace.org/de/api_v4/projects/60749/categories.json"
        },
        {
          "rel": "new_client_donation",
          "href": "https://www.betterplace.org/de/donate/%7Bclient_id%7D/projects/60749",
          "templated": true
        },
        {
          "rel": "new_donation",
          "href": "https://www.betterplace.org/de/donate/platform/projects/60749"
        }
      ]
    },
    {
      "id": 1114,
      "created_at": "2009-03-10T11:12:16+01:00",
      "updated_at": "2021-05-17T20:09:03+02:00",
      "latitude": -8.783195,
      "longitude": 34.508523,
      "street": "Berliner Straße 73",
      "zip": "",
      "city": "South Africa, Cambodia",
      "country": "Afghanistan",
      "content_updated_at": "2021-01-06T11:28:11+01:00",
      "activated_at": "2009-03-10T00:00:00+01:00",
      "title": "Unterstütze Skateistan - Sport &amp; Bildung für Kinder",
      "description": "<div>Skateistan ist eine mehrfach ausgezeichnete, internationale non-profit Organisation, welche Kinder in Afghanistan, Kambodscha und Südafrika durch Skateboarden und Bildung stark macht. Mit unseren innovativen Programmen möchten wir jungen Menschen die Möglichkeit bieten Vorbilder für eine bessere Welt zu werden. Viele unserer Schüler haben nur wenige Möglichkeiten an Sport- und Bildungsangeboten teilzunehmen. Das betrifft insbesondere Mädchen, gehandicapte Kinder und andere Minderheiten. Armut, Konflikte und Gefahren sind die Realitäten für die Menschen in den Gebieten, wo wir aktiv sind. In solchen Umständen ist es schwer für die Kinder gehört zu werden und genauso mühsam ihr physisches und mentales Wohl sicherzustellen.<br><br>Wir von Skateistan glauben, dass jedes Kind einen Zugang zu Bildung und Freizeitgestaltung braucht, bei dem sie Selbstvertrauen aufbauen können, Freunde kennen lernen und neue Fähigkeiten erlernen, die eine positive Vorbildfunktion mit sich bringen. Skateistan erreicht mit ihren Skateschulen derzeit mehr als 2.600 Schüler weltweit. Über die Hälfte der Skateistan Schüler sind weiblich und Skateboarden ist seither der größte Sport für Mädchen in Afghanistan.<br><br>In 2018 haben wir unseren zehnten Geburtstag gefeiert. Von einigen wenigen Mädchen auf Skateboards in Kabul ist Skateistan zu einer internationalen Nichtregierungsorganisation mit über 2000 aktiven Schülern in drei Ländern gewachsen. <strong>Doch das ist für uns erst der Anfang. Wir wollen noch mehr erreichen, so dass noch mehr Kinder durch Bildung und Skateboarding gestärkt werden.<br></strong><br>\n</div><div>Indem wir Programme für Kinder aus sämtlichen Gesellschaftsschichten zur Verfügung stellen, helfen wir, soziale Grenzen abzubauen. Wir zeigen Kindern, dass Vielfalt etwas ist, was es zu feiern gilt. <strong>Über 50% unserer Schüler sind Mädchen und 78% unserer Schüler kommen aus Familien, die über keine finanziellen Mittel zur Selbsthilfe verfügen</strong>. 160 unserer Kinder leben mit Behinderungen und über 70 Kinder sind im eigenen Land vertrieben.<br><br>\n</div><div>Deswegen betreibt Skateistan Skate-Schulen in Afghanistan, Kambodscha und Südafrika, die den Spaß und den Freigeist von Skateboarding verbindet mit der Chance für die Kinder, ihre kreativen Talente und Interessen auszuprobieren. <strong>Wir glauben, dass Bildung der beste Weg ist, um Kinder zu stärken</strong>, sodass sie den Wandel in ihrem eigenen Umfeld, in ihren Familien, ihren Nachbarschaften einleiten und Gelerntes dort weitergeben. Indem sie über Spiel und Spaß lernen, stellen wir eine positive Verbindung zu Bildung her. Skateboarding lehrt sie außerdem Lektionen, die sie für ihr ganzes Leben behalten. <strong>Skateboarding lehrt sie, kreativ zu werden, hinzufallen und wieder aufzustehen und auf ein Ziel hinzuarbeiten.</strong>\n</div><div><br></div>",
      "summary": "Skateistan will Kindern in Afghanistan, Kambodsha und Sudafrika neue Perspektiven eröffnen, Vorurteile abbauen, Gleichberechtigung fördern und Freude bringen.",
      "tax_deductible": true,
      "donations_prohibited": false,
      "completed_at": null,
      "closed_at": null,
      "open_amount_in_cents": 467800,
      "donated_amount_in_cents": 8507052,
      "positive_opinions_count": 1119,
      "negative_opinions_count": 0,
      "donations_count": 1119,
      "newsletter_subscriptions_count": 451,
      "comments_count": 0,
      "donor_count": 789,
      "progress_percentage": 94,
      "incomplete_need_count": 1,
      "completed_need_count": 106,
      "blog_post_count": 101,
      "contact": {
        "id": 287126,
        "name": "Louie Groß (display)",
        "picture": {
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://betterplace-assets.betterplace.org/uploads/user/profile_picture/000/287/126/fill_100x100_bp1584575045_Skateistan_facebook-02.png"
            },
            {
              "rel": "original",
              "href": "https://betterplace-assets.betterplace.org/uploads/user/profile_picture/000/287/126/crop_original_bp1584575045_Skateistan_facebook-02.png"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.org/de/users/287126"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/de/api_v4/users/287126/contact_data.json"
          }
        ]
      },
      "carrier": {
        "id": 1054,
        "name": "Skateistan",
        "city": "Berlin",
        "picture": {
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://betterplace-assets.betterplace.org/uploads/organisation/profile_picture/000/001/054/fill_100x100_bp1523439289_Skateistan_facebook-01.png"
            },
            {
              "rel": "original",
              "href": "https://betterplace-assets.betterplace.org/uploads/organisation/profile_picture/000/001/054/crop_original_bp1523439289_Skateistan_facebook-01.png"
            }
          ]
        },
        "links": [
          {
            "rel": "self",
            "href": "https://api.betterplace.org/de/api_v4/organisations/1054.json"
          }
        ]
      },
      "profile_picture": {
        "links": [
          {
            "rel": "fill_960x500",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/001/114/fill_960x500_bp1605784738_Bamyan_selects_July2019_Outreach_Mubaraka__2_.jpeg"
          },
          {
            "rel": "fill_730x380",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/001/114/fill_730x380_bp1605784738_Bamyan_selects_July2019_Outreach_Mubaraka__2_.jpeg"
          },
          {
            "rel": "fill_618x322",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/001/114/fill_618x322_bp1605784738_Bamyan_selects_July2019_Outreach_Mubaraka__2_.jpeg"
          },
          {
            "rel": "fill_410x214",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/001/114/fill_410x214_bp1605784738_Bamyan_selects_July2019_Outreach_Mubaraka__2_.jpeg"
          },
          {
            "rel": "fill_270x141",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/001/114/fill_270x141_bp1605784738_Bamyan_selects_July2019_Outreach_Mubaraka__2_.jpeg"
          },
          {
            "rel": "original",
            "href": "https://betterplace-assets.betterplace.org/uploads/project/profile_picture/000/001/114/crop_original_bp1605784738_Bamyan_selects_July2019_Outreach_Mubaraka__2_.jpeg"
          }
        ]
      },
      "active_matching_fund": null,
      "closed_notice": null,
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/projects/1114-unterstuetze-skateistan-sport-bildung-fuer-kinder"
        },
        {
          "rel": "opinions",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114/opinions.json"
        },
        {
          "rel": "pictures",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114/pictures.json"
        },
        {
          "rel": "needs",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114/needs.json"
        },
        {
          "rel": "blog_posts",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114/blog_posts.json"
        },
        {
          "rel": "video",
          "href": "https://www.youtube.com/watch?v=KgcS_b_UeYo&feature=emb_logo"
        },
        {
          "rel": "matching_funds",
          "href": "https://api.betterplace.org/de/api_v4/matching_funds.json?project_id=1114"
        },
        {
          "rel": "categories",
          "href": "https://api.betterplace.org/de/api_v4/projects/1114/categories.json"
        },
        {
          "rel": "new_client_donation",
          "href": "https://www.betterplace.org/de/donate/%7Bclient_id%7D/projects/1114",
          "templated": true
        },
        {
          "rel": "new_donation",
          "href": "https://www.betterplace.org/de/donate/platform/projects/1114"
        }
      ]
    }
  ]
}
```

