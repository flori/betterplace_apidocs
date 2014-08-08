
# Project Blog Posts List ⇄ [Details](blog_post_details.md)

```nginx
GET https://api.betterplace.org/en/api_v4/projects/1114/blog_posts.json
```

A list of betterplace.org projects blog posts.
Results are contained in a *data* attribute.

*For [betterplace.org clients](../README.md#client-api):*

* _Project-Blogposts:_ There is no client-scoped-url.
Please use the api calls that are provided inside the client project _url_ response
to make sure you only request data that is associated with one of your projects.

* _All Blogposts:_ Clients can retrieve a list of all blogpost of all client-projects:
`/clients/PERMALINK/blog_posts.json`


## Input Parameter

<table>
  <tr>
    <th>Parameter</th>
    <th>Example</th>
    <th>Required/Optional</th>
    <th>Description</th>
  </tr>
  <tr>
    <th align="left">project_id</th>
    <td><code>1114</code></td>
    <td>required</td>
    <td>Project-id as an integer number ≥ 14.</td>
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
      <td>1</td>
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
      <th align="left">lang</th>
      <td>string</td>
      <td>en</td>
      <td>Blog posts have only one language at the moments</td>
    </tr>
    <tr>
      <th align="left">type</th>
      <td>string</td>
      <td>PayoutBlogPost</td>
      <td>Blogposts can be created by a user <code>BlogPost</code>
to update your donors about new developments
or as part of the payout process <code>PayoutBlogPost</code>
where you tell what needs you payed our and
what you plan to do with the money.
</td>
    </tr>
    <tr>
      <th align="left">title</th>
      <td>string</td>
      <td>Thank you from Beijing</td>
      <td></td>
    </tr>
    <tr>
      <th align="left">body</th>
      <td>string</td>
      <td>I am so happy to hear about the first donation for the Good Gifted Garden. If I told Chun …</td>
      <td>The body has html like links, embeded videos, pictures.</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a name="payout-ref" href="#payout">
            ↓payout
          </a>
        </th>
      <td>null &#124; object</td>
      <td>TODO</td>
      <td></td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a name="author-ref" href="#author">
            ↓author
          </a>
        </th>
      <td>string</td>
      <td>"Till B."</td>
      <td>Display name of a betterplace.org user.
Possible formats: "Till B.", "T. Behnke", "Till Behnke"
</td>
    </tr>
  </table>
### <a name="payout" href="#payout-ref">↑Nested Attributes: payout</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a name="payout.needs-ref" href="#payout.needs">
            ↓payout.needs
          </a>
        </th>
      <td>array</td>
      <td>TODO</td>
      <td>TODO</td>
    </tr>
  </table>
### <a name="payout.needs" href="#payout.needs-ref">↑Nested Attributes: payout.needs</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">payout.needs.need_title</th>
      <td>string</td>
      <td>Schoolbooks</td>
      <td>Title of the need</td>
    </tr>
    <tr>
      <th align="left">payout.needs.payout_amount_in_cents</th>
      <td>string</td>
      <td>2300</td>
      <td>Amount paid out to that need</td>
    </tr>
  </table>
### <a name="author" href="#author-ref">↑Nested Attributes: author</a>

  <table>
    <tr>
      <th>Attribute</th>
      <th>Types</th>
      <th>Example</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">author.name</th>
      <td>null &#124; string</td>
      <td>"Till B."</td>
      <td>Display name of a betterplace.org user.
Possible formats: "Till B.", "T. Behnke", "Till Behnke".
In the case of donation-opinions the name might also be anonymized
like "Payback User" or empty/null for anonymous donations.
</td>
    </tr>
    <tr>
      <th align="left">author.picture</th>
      <td>string</td>
      <td>//assets.betterplace.org/…</td>
      <td>User profile picture or a fallback image</td>
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
(<a href="blog_post_details.md">blog post details</a>)
</td>
    </tr>
    <tr>
      <th align="left">platform</th>
      <td>Permalink to betterplace.org</td>
    </tr>
    <tr>
      <th align="left">documentation</th>
      <td>Link to this resource in the documentation
</td>
    </tr>
    <tr>
      <th align="left">author.platform</th>
      <td>The user's profile on betterplace.org.
To view a user profile you have to be logged in.
This array is empty if the user has no useraccount
with betterplace.org but donated via one of our partner.
</td>
    </tr>
    <tr>
      <th align="left">author.contact_data</th>
      <td>The user's contact data. Please note that you need to be
<a href="../README.md#client-authentication">authenticated as a client</a> with matching
access rights in order to see this information.
</td>
    </tr>
    <tr>
      <th align="left">author.picture.fill_100x100</th>
      <td>100x100 Pixel</td>
    </tr>
    <tr>
      <th align="left">author.picture.original</th>
      <td>Maximum sized image. This is the original image with default-cropping or user-cropping applied.</td>
    </tr>
</table>

## Response Example

```json
{
  "total_entries": 84,
  "offset": 0,
  "total_pages": 42,
  "current_page": 1,
  "per_page": 2,
  "data": [
    {
      "id": 5703,
      "created_at": "2009-06-15T06:21:20Z",
      "updated_at": "2009-06-15T06:21:20Z",
      "lang": "en",
      "type": "BlogPost",
      "title": "Go Skateboarding Day Kabul",
      "body": "<p>Skateistan's first GSD in Kabul on June 21st: Skate-a-thon and competition in honor of Go Skateboarding Day, a holiday on which we recognize the value of skateboarding to youth in societies across the world. Join the Skateistan students as they skateboard from Bibi Mahru to Macroryan. There will be a celebratory skateboarding competition upon arrival at the empty fountain in Macroryan.</p>",
      "payout": null,
      "author": {
        "name": "M. Henninger",
        "picture": {
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/009/238/fill_100x100_original_maxn_skate.jpg"
            },
            {
              "rel": "original",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/009/238/crop_original_original_maxn_skate.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.org/en/users/max_h2"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/en/api_v4/users/9238/contact_data.json"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/en/api_v4/blog_posts/5703.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/en/projects/1114-skateistan-afghanistan/news/5703"
        },
        {
          "rel": "documentation",
          "href": "https://github.com/betterplace/betterplace_apidocs/blob/master/sections/blog_post_details.md"
        }
      ]
    },
    {
      "id": 6910,
      "created_at": "2009-07-12T10:25:13Z",
      "updated_at": "2009-07-12T10:27:16Z",
      "lang": "en",
      "type": "BlogPost",
      "title": "We Skated! Kabul",
      "body": "<p>&nbsp;</p>\r\n<p>Several news outlets have featured stories about our celebration of international Go Skateboarding Day on Monday June 21, and the laying of the cornerstone at our new skatepark next to Ghazi Stadium on Tuesday June 22. Read all about it:</p>\r\n<p><a href=\"http://www.worldchanging.com/archives/009959.html\">WorldChanging</a></p>\r\n<p><a href=\"http://axisoflogic.com/artman/publish/Article_55984.shtml\">Axis of Logic</a></p>\r\n<p><a href=\"http://jezebel.com/5299583/sk8r-gurls\">Jezebel</a></p>\r\n<p><a href=\"http://skateboarding.transworld.net/2009/06/23/go-skateboarding-day-in-kabul/\">Transworld Skateboarding</a></p>\r\n<p><a href=\"http://www.pajhwok.com/photoserv.asp\">Pajhwok Afghan News</a></p>\r\n<p><a href=\"http://www.ksdk.com/news/national/story.aspx?storyid=178412&amp;amp;amp;catid=28\">KSDK 5</a></p>\r\n<p><a href=\"http://www.nationalpost.com/news/story.html?id=1718795\">National Post</a></p>\r\n<p>&nbsp;</p>",
      "payout": null,
      "author": {
        "name": "M. Henninger",
        "picture": {
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/009/238/fill_100x100_original_maxn_skate.jpg"
            },
            {
              "rel": "original",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/009/238/crop_original_original_maxn_skate.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.org/en/users/max_h2"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/en/api_v4/users/9238/contact_data.json"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/en/api_v4/blog_posts/6910.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/en/projects/1114-skateistan-afghanistan/news/6910"
        },
        {
          "rel": "documentation",
          "href": "https://github.com/betterplace/betterplace_apidocs/blob/master/sections/blog_post_details.md"
        }
      ]
    }
  ]
}
```

