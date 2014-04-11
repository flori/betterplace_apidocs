
# Projects List ⇄ [Details](project_details.md)

```nginx
GET https://api.betterplace.org/en/api_v4/projects.json?facets=completed%3Afalse&nelat=51.123&nelng=12.123&order=rank%3AASC&q=Skateistan&scope=location&swlat=51.001&swlng=12.001
```

A list of betterplace.org projects (donate money).
Results are contained in a *data* attribute.

*For [betterplace.org clients](../README.md#client-api):*
Use this resource like `/clients/PERMALINK/projects.json`


## Input Parameter

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Required/Optional</th>
    <th>Description</th>
  </tr>
  <tr>
    <th align="left">scope</th>
    <td><code>location</code></td>
    <td>optional</td>
    <td>Use the scope to specify how the search-query <code>q</code> should behave:
<ul>
<li>"no scope" (default) performs a full text search
<li><code>human_name</code> searches only on the manager-fullname and carrier-fullname.
    Use this to get all projects by "Unicef" or by "Till Behnke".
<li><code>location</code> does a reverse geocoding lookup
    and shows results based on the lookup-bounding-box.
</ul>
<a href="../README.md#request-parameter-format">Learn how to format the parameter</a>.
</td>
  </tr>
  <tr>
    <th align="left">q</th>
    <td><code>Skateistan</code></td>
    <td>optional</td>
    <td>Search query. The searches behaviour is based on the scope.</td>
  </tr>
  <tr>
    <th align="left">order</th>
    <td><code>rank:ASC</code></td>
    <td>optional</td>
    <td>Order the result by solr-<code>score</code> (only when a query (q) is given),
<code>rank</code>, <code>id</code>, <code>progress_percentage</code>,
<code>tax_deductible</code>, <code>created_at</code>, <code>updated_at</code>,
<code>last_donation_at</code>, <code>completed</code>.
Use the optional <code>ASC</code> (default) or <code>DESC</code>.
<a href="../README.md#request-parameter-format">Learn how to format the parameter</a>.
<br>
The default order is the same as for the
<a href="http//www.betterplace.org/en/projects/list">betterplace.org project list</a>:
<code>completed:asc| score:desc| rank:asc| last_donation_at:desc</code>
</td>
  </tr>
  <tr>
    <th align="left">facets</th>
    <td><code>completed:false</code></td>
    <td>optional</td>
    <td>Filter the result set by <code>tax_deductible</code> or <code>completed</code>. Possible values are
<code>true</code> or <code>false</code>.
It is possible to set multiple facet filters.
<a href="../README.md#request-parameter-format">Learn how to format the parameter</a>.
</td>
  </tr>
  <tr>
    <th align="left">nelat</th>
    <td><code>51.123</code></td>
    <td>optional</td>
    <td>For geographic bound filterning: The northeast corner's latitude.</td>
  </tr>
  <tr>
    <th align="left">nelng</th>
    <td><code>12.123</code></td>
    <td>optional</td>
    <td>For geographic bound filterning: The northeast corner's longitude.</td>
  </tr>
  <tr>
    <th align="left">swlat</th>
    <td><code>51.001</code></td>
    <td>optional</td>
    <td>For geographic bound filterning: The southwest corner's latitude.</td>
  </tr>
  <tr>
    <th align="left">swlng</th>
    <td><code>12.001</code></td>
    <td>optional</td>
    <td>For geographic bound filterning: The southwest corner's longitude.</td>
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
      <td>4</td>
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
      <th align="left">completed_at</th>
      <td>string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone) when the project was completed</td>
    </tr>
    <tr>
      <th align="left">latitude</th>
      <td>number</td>
      <td>52.499007</td>
      <td>Decimal degrees based on user input</td>
    </tr>
    <tr>
      <th align="left">longitude</th>
      <td>number</td>
      <td>13.44947</td>
      <td>Decimal degrees based on user input</td>
    </tr>
    <tr>
      <th align="left">street</th>
      <td>null &#124; string</td>
      <td>"Schlesische Straße 26"</td>
      <td>Where the project takes place</td>
    </tr>
    <tr>
      <th align="left">zip</th>
      <td>null &#124; string</td>
      <td>"10997"</td>
      <td>Where the project takes place</td>
    </tr>
    <tr>
      <th align="left">city</th>
      <td>null &#124; string</td>
      <td>"Berlin"</td>
      <td>Where the project takes place</td>
    </tr>
    <tr>
      <th align="left">country</th>
      <td>null &#124; string</td>
      <td>"Deutschland"</td>
      <td>Where the project takes place, translated to the requested language</td>
    </tr>
    <tr>
      <th align="left">title</th>
      <td>string</td>
      <td></td>
      <td>Max 50 character</td>
    </tr>
    <tr>
      <th align="left">description</th>
      <td>string</td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <th align="left">tax_deductible</th>
      <td>boolean</td>
      <td>true</td>
      <td>True if the project marked as tax deductible.
If so, Users can request a tax-receipt that can be used
with the german tax authorities.
[More about this](http://www.betterplace.org/c/hilfe/projekt-steuerlich-absetzbar/).
</td>
    </tr>
    <tr>
      <th align="left">donations_prohibited</th>
      <td>boolean</td>
      <td>false</td>
      <td>True if the project must not receive donations. This might happen if a tax-receipt
of german tax authorities rans out.
</td>
    </tr>
    <tr>
      <th align="left">open_amount_in_cents</th>
      <td>number</td>
      <td>12382</td>
      <td>How many cents are needed to complete the project</td>
    </tr>
    <tr>
      <th align="left">positive_opinions_count</th>
      <td>number</td>
      <td>13</td>
      <td>Number of positive opinions that are given to a project without a donation.
Those are plain opinions as well as visitor opinions.
</td>
    </tr>
    <tr>
      <th align="left">negative_opinions_count</th>
      <td>number</td>
      <td>0</td>
      <td>Number of *negative* opinions (usually 0) that are given to a project without a donation.
Those are plain opinions as well as visitor opinions.
Critical opinions are part of the betterplace.org
["Web of trust"](http://www.betterplace.org/c/hilfe/woran-erkenne-ich-dass-ein-projekt-vertrauenswurdig-ist/).
</td>
    </tr>
    <tr>
      <th align="left">donor_count</th>
      <td>number</td>
      <td>46</td>
      <td>Number of unique donors, based on the payment-email-address</td>
    </tr>
    <tr>
      <th align="left">progress_percentage</th>
      <td>number</td>
      <td>82</td>
      <td>% financed. Note: We have legacy projects with substantial
donation needs. This percentage includes those needs.
</td>
    </tr>
    <tr>
      <th align="left">incomplete_need_count</th>
      <td>number</td>
      <td>6</td>
      <td>Number of needs that still need donations</td>
    </tr>
    <tr>
      <th align="left">completed_need_count</th>
      <td>number</td>
      <td>12</td>
      <td>Number of completed needs</td>
    </tr>
    <tr>
      <th align="left">blog_post_count</th>
      <td>number</td>
      <td>8</td>
      <td>Number of blogposts (all types)</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a name="contact-ref" href="#contact">
            ↓contact
          </a>
        </th>
      <td>object</td>
      <td>TODO</td>
      <td>The public face of the project / project manager</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a name="carrier-ref" href="#carrier">
            ↓carrier
          </a>
        </th>
      <td>object</td>
      <td>TODO</td>
      <td>An organisation, Users will be added later</td>
    </tr>
    <tr>
      <th align="left">profile_picture</th>
      <td>null &#124; object</td>
      <td></td>
      <td>TODO</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a name="active_matching_fund-ref" href="#active_matching_fund">
            ↓active_matching_fund
          </a>
        </th>
      <td>null &#124; object</td>
      <td>TODO</td>
      <td>TODO</td>
    </tr>
  </table>
### <a name="contact" href="#contact-ref">↑Nested Attributes: contact</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">contact.name</th>
      <td>null &#124; string</td>
      <td>"Till B."</td>
      <td>Display name of a betterplace.org user.
Possible formats: "Till B.", "T. Behnke", "Till Behnke".
In the case of donation-opinions the name might also be anonymized
like "Payback User" or empty/null for anonymous donations.
</td>
    </tr>
    <tr>
      <th align="left">contact.picture</th>
      <td>string</td>
      <td>//assets.betterplace.org/…</td>
      <td>User profile picture or a fallback image</td>
    </tr>
  </table>
### <a name="carrier" href="#carrier-ref">↑Nested Attributes: carrier</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">carrier.name</th>
      <td>string</td>
      <td>"Till B."</td>
      <td>The carrier can be an organisation or user.</td>
    </tr>
    <tr>
      <th align="left">carrier.picture</th>
      <td>string</td>
      <td>//assets.betterplace.org/…</td>
      <td>The organisation logo, user profile picture or a fallback image</td>
    </tr>
  </table>
### <a name="active_matching_fund" href="#active_matching_fund-ref">↑Nested Attributes: active_matching_fund</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">active_matching_fund.id</th>
      <td>string</td>
      <td>53</td>
      <td>An integer number ≥ 1</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.created_at</th>
      <td>string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone)</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.updated_at</th>
      <td>string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone)</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.activated_at</th>
      <td>null &#124; string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone)</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.title</th>
      <td>string</td>
      <td>ACME Matching Everything</td>
      <td>Our matching fund's name</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.description</th>
      <td>string</td>
      <td>It's all about matching donations…</td>
      <td>The description of the matching fund</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.company_name</th>
      <td>string</td>
      <td>ACME</td>
      <td>The company that supports it</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.state</th>
      <td>string</td>
      <td>activated</td>
      <td>Current state of this matching fund: either activated or closed</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.logo_url</th>
      <td>string</td>
      <td>http://example.com/images/logo.png</td>
      <td>The URL of the logo image.</td>
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
      <th align="left">self</th>
      <td>Link to this resource itself
(<a href="project_details.md">project details</a>)
</td>
    </tr>
    <tr>
      <th align="left">platform</th>
      <td>Permalink to betterplace.org</td>
    </tr>
    <tr>
      <th align="left">opinions</th>
      <td>Link to <a href="opinions_list.md">opinion list</a>
</td>
    </tr>
    <tr>
      <th align="left">pictures</th>
      <td>Link to <a href="picture_list.md">project picture list</a>
</td>
    </tr>
    <tr>
      <th align="left">needs</th>
      <td>Link to <a href="needs_list.md">project need list</a>
</td>
    </tr>
    <tr>
      <th align="left">blog_posts</th>
      <td>Link to <a href="blog_posts_list.md">blog post list</a>
</td>
    </tr>
    <tr>
      <th align="left">matching_funds</th>
      <td>Link to <a href="manager_details.md">matching funds list</a>
</td>
    </tr>
    <tr>
      <th align="left">contact.platform</th>
      <td>The user's profile on betterplace.org.
To view a user profile you have to be logged in.
This array is empty if the user has no useraccount
with betterplace.org but donated via one of our partner.
</td>
    </tr>
    <tr>
      <th align="left">contact.contact_data</th>
      <td>The user's contact data. Please note that you need to be
<a href="../README.md#client-authentication">authenticated as a client</a> with matching
access rights in order to see this information.
</td>
    </tr>
    <tr>
      <th align="left">contact.picture.original</th>
      <td>Original size as uploaded by the user</td>
    </tr>
    <tr>
      <th align="left">carrier.self</th>
      <td>Link to this resource itself
(<a href="organisation_details.md">organisation details</a>)
Note: Since the there is no api for users yet, this is only
set for organisations.
</td>
    </tr>
    <tr>
      <th align="left">carrier.picture.original</th>
      <td>Original size as uploaded by the user</td>
    </tr>
    <tr>
      <th align="left">profile_picture.fill_618x322</th>
      <td>618x322 Pixel</td>
    </tr>
    <tr>
      <th align="left">profile_picture.fill_270x141</th>
      <td>270x141 Pixel</td>
    </tr>
    <tr>
      <th align="left">profile_picture.original</th>
      <td>Original size as uploaded by the user</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.self</th>
      <td>Link to this resource itself
(<a href="matching_fund_details.md">matching fund details</a>)
</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.platform</th>
      <td>Permalink to betterplace.org</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.projects</th>
      <td>Link to the list of projects belonging to this matching fund</td>
    </tr>
    <tr>
      <th align="left">active_matching_fund.documentation</th>
      <td>Link to this resource in the documentation
</td>
    </tr>
</table>

## Response Example

```json
{
  "total_entries": 2,
  "offset": 0,
  "total_pages": 1,
  "current_page": 1,
  "per_page": 3,
  "data": [
    {
      "id": 1114,
      "created_at": "2009-03-10T10:12:16Z",
      "updated_at": "2014-03-26T21:30:23Z",
      "completed_at": null,
      "latitude": 34.531617284782,
      "longitude": 69.13581752939456,
      "street": "Taimani, behind Qasemi Winhouse",
      "zip": "",
      "city": "Kabul",
      "country": "Afghanistan",
      "title": "Skateistan Afghanistan",
      "description": "With 68% of Afghanistan’s population under the age of 25, Skateistan strongly believes that youth are the ones most capable of bringing about social change.<br /><br />Skateistan is an Afghan NGO which operates Afghanistan’s (and the world’s) first co-educational skateboarding school. The Skateistan school engages nearly 400 Kabul youth weekly through skateboarding, and provides them with new opportunities in cross-cultural interaction, education, and personal empowerment programs. <br /><br />The students (ages 5-17) come from all of Afghanistan’s diverse ethnic and socioeconomic backgrounds, and include 40% female students, hundreds of streetworking children, and youth with disabilities. They develop skills in skateboarding, leadership, problem-solving, multimedia, and creative arts. The students themselves decide what they want to learn; we connect them with a safe space and opportunities for them to develop the skills that they consider important.<br /><br />For Afghan girls Skateistan's programming is especially important as there are very few recreational opportunities for females. For example, it is not culturally acceptable for girls in Afghanistan to ride bicycles or play sports in public. <br /><br />Skateistan has been active in Kabul since 2007 - with our facility built in 2009 - and in that time we’ve seen that Afghan youth of all ethnicities, genders, and socioeconomic backgrounds love to skateboard. Skateistan brings them together, equipping young men and women to lead their communities toward social change and development.<br /><br />In 2012 Skateistan will be opening its second Afghan facility in Mazar-e-Sharif, Northern Afghanistan. It will have space to teach up to 1000 youth weekly.<br /><br />Our program gives hundreds of oppressed youth a voice. Education and the opportunity for self-expression can break the cycles of poverty, illiteracy and exclusion, with sport paving the way.",
      "tax_deductible": true,
      "donations_prohibited": false,
      "open_amount_in_cents": 169202,
      "positive_opinions_count": 635,
      "negative_opinions_count": 0,
      "donor_count": 515,
      "progress_percentage": 96,
      "incomplete_need_count": 1,
      "completed_need_count": 80,
      "blog_post_count": 82,
      "contact": {
        "name": "E. Kinast",
        "picture": {
          "links": [
            {
              "rel": "original",
              "href": "http://asset1.betterplace.org/uploads/user/profile_picture/000/130/618/original_Picture_023.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "http://www.betterplace.org/en/users/erika_k2"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/en/api_v4/users/130618/contact_data.json"
          }
        ]
      },
      "carrier": {
        "name": "Skateistan",
        "picture": {
          "links": [
            {
              "rel": "original",
              "href": "http://asset1.betterplace.org/uploads/organisation/profile_picture/000/001/054/original_betterplace-logo.png"
            }
          ]
        },
        "links": [
          {
            "rel": "self",
            "href": "https://api.betterplace.org/en/api_v4/organisations/1054.json"
          }
        ]
      },
      "profile_picture": {
        "links": [
          {
            "rel": "fill_618x322",
            "href": "http://asset1.betterplace.org/paperclip/000/289/158/default_girls-merza-sm.jpg"
          },
          {
            "rel": "fill_270x141",
            "href": "http://asset1.betterplace.org/paperclip/000/289/158/profile_girls-merza-sm.jpg"
          },
          {
            "rel": "original",
            "href": "http://asset1.betterplace.org/paperclip/000/289/158/default_girls-merza-sm.jpg"
          }
        ]
      },
      "active_matching_fund": null,
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/en/api_v4/projects/1114.json"
        },
        {
          "rel": "platform",
          "href": "http://www.betterplace.org/en/projects/1114-skateistan-afghanistan"
        },
        {
          "rel": "opinions",
          "href": "https://api.betterplace.org/en/api_v4/projects/1114/opinions.json"
        },
        {
          "rel": "pictures",
          "href": "https://api.betterplace.org/en/api_v4/projects/1114/pictures.json"
        },
        {
          "rel": "needs",
          "href": "https://api.betterplace.org/en/api_v4/projects/1114/needs.json"
        },
        {
          "rel": "blog_posts",
          "href": "https://api.betterplace.org/en/api_v4/projects/1114/blog_posts.json"
        },
        {
          "rel": "matching_funds",
          "href": "https://api.betterplace.org/en/api_v4/matching_funds.json?project_id=1114"
        }
      ]
    },
    {
      "id": 6233,
      "created_at": "2011-02-25T07:48:43Z",
      "updated_at": "2014-03-28T16:00:01Z",
      "completed_at": null,
      "latitude": 11.55883121490479,
      "longitude": 104.9174423217773,
      "street": null,
      "zip": null,
      "city": "Phnom Penh",
      "country": "Cambodia",
      "title": "Skateistan Cambodia",
      "description": "Skateistan Cambodia began operations in March 2011, building the country's first skatepark in Phnom Penh. Since then the NGO has been teaching skateboarding and creative arts classes with marginalized and streetworking Khmer youth six days a week. <br /><br />Skateboarding is a low-barrier, accessible activity that attracts girls and boys of all backgrounds and abilities. The interest from Cambodia's youth has grown so much since March 2011 that Skateistan Cambodia is now building its own facility to accommodate more than the 150 youth we currently work with weekly.<br /><br />By building a safe and covered Skateistan facility in Phnom Pehn, Skateistan will provide year-round opportunities for youth to engage in recreational activities that encourages girls and boys of all backgrounds to build relationships with one another, while increasing their self-confidence and leadership skills. The facility will also have classroom spaces providing creative arts and multimedia activities for the students.<br /><br />Partnering with local, best-practice NGOs in Cambodia, such as Pour un Sourire d'Enfant (PSE), Friends Intl., and Tiny Toones, Skateistan Cambodia also aims to use skateboarding as a tool to create a bridge between at-risk youth and the quality support services already existing in Phnom Penh.<br /><br />Help us grow this grassroots project and create a safe space for all Cambodian youth to be a part of!",
      "tax_deductible": true,
      "donations_prohibited": false,
      "open_amount_in_cents": 24900,
      "positive_opinions_count": 47,
      "negative_opinions_count": 0,
      "donor_count": 43,
      "progress_percentage": 94,
      "incomplete_need_count": 1,
      "completed_need_count": 13,
      "blog_post_count": 31,
      "contact": {
        "name": "A. Buck",
        "picture": {
          "links": [
            {
              "rel": "original",
              "href": "http://asset1.betterplace.org/uploads/user/profile_picture/000/272/452/original_11545_216544438618_2260714_n.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "http://www.betterplace.org/en/users/alixandra_b"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/en/api_v4/users/272452/contact_data.json"
          }
        ]
      },
      "carrier": {
        "name": "Skateistan",
        "picture": {
          "links": [
            {
              "rel": "original",
              "href": "http://asset1.betterplace.org/uploads/organisation/profile_picture/000/001/054/original_betterplace-logo.png"
            }
          ]
        },
        "links": [
          {
            "rel": "self",
            "href": "https://api.betterplace.org/en/api_v4/organisations/1054.json"
          }
        ]
      },
      "profile_picture": {
        "links": [
          {
            "rel": "fill_618x322",
            "href": "http://asset1.betterplace.org/paperclip/000/288/830/default_327569_368768896527128_1081473646_o.jpg"
          },
          {
            "rel": "fill_270x141",
            "href": "http://asset1.betterplace.org/paperclip/000/288/830/profile_327569_368768896527128_1081473646_o.jpg"
          },
          {
            "rel": "original",
            "href": "http://asset1.betterplace.org/paperclip/000/288/830/default_327569_368768896527128_1081473646_o.jpg"
          }
        ]
      },
      "active_matching_fund": null,
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/en/api_v4/projects/6233.json"
        },
        {
          "rel": "platform",
          "href": "http://www.betterplace.org/en/projects/6233-skateistan-cambodia"
        },
        {
          "rel": "opinions",
          "href": "https://api.betterplace.org/en/api_v4/projects/6233/opinions.json"
        },
        {
          "rel": "pictures",
          "href": "https://api.betterplace.org/en/api_v4/projects/6233/pictures.json"
        },
        {
          "rel": "needs",
          "href": "https://api.betterplace.org/en/api_v4/projects/6233/needs.json"
        },
        {
          "rel": "blog_posts",
          "href": "https://api.betterplace.org/en/api_v4/projects/6233/blog_posts.json"
        },
        {
          "rel": "matching_funds",
          "href": "https://api.betterplace.org/en/api_v4/matching_funds.json?project_id=6233"
        }
      ]
    }
  ]
}
```

