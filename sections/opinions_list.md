
# Project Opinions List ⇄ [Details](opinion_details.md)

```nginx
GET https://api.betterplace.org/en/api_v4/projects/1114/opinions.json?facets=has_message%3Atrue&order=created_at%3AASC
```

A list of betterplace.org projects opinions (donate money).
Results are contained in a *data* attribute.

*For [betterplace.org clients](../README.md#client-api):*

* _Project-Opinions:_ There is no client-scoped-url.
Please use the api calls that are provided inside the client project _url_ response
to make sure you only request data that is associated with one of your projects.

* _All Opinions:_ Clients can retrieve a list of all opinions of all client-projects:
`/clients/PERMALINK/opinions.json`


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
  <tr>
    <th align="left">order</th>
    <td><code>created_at:ASC</code></td>
    <td>optional</td>
    <td>Order the result by
<code>created_at</code> (default), <code>id</code>, <code>score</code>
Use the optional <code>ASC</code> (default) or <code>DESC</code>.
<a href="../README.md#request-parameter-format">Learn how to format the parameter</a>.
</td>
  </tr>
  <tr>
    <th align="left">facets</th>
    <td><code>has_message:true</code></td>
    <td>optional</td>
    <td>Filter the result set:
<ul>
<li><code>facets=score:positive</code> / <code>negative</code> only positive / negative opinion
<li><code>facets=has_donation:true</code> / <code>false</code> only opinions with / without a donation
<li><code>facets=has_message:true</code> / <code>false</code> only opinions with / without a message
</ul>
It is possible to set multiple facet filters.
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
      <th align="left">donated_amount_in_cents</th>
      <td>number</td>
      <td>5000</td>
      <td>If the opinion was created as part of a donation, this shows the opinions text</td>
    </tr>
    <tr>
      <th align="left">score</th>
      <td>string</td>
      <td>positive</td>
      <td>Opinions can be positive or negative. Negative opinions usually get
a comment as answer very fast but there is no API for opinion-comments yet.
</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a name="author-ref" href="#author">
            ↓author
          </a>
        </th>
      <td>null &#124; object</td>
      <td>TODO</td>
      <td>The author. DonorOpinion may be anonymous,
PlainOpinions and VisitorOpinion require a logged in user.
</td>
    </tr>
    <tr>
      <th align="left">message</th>
      <td>null &#124; string</td>
      <td>"This is a great project. In spring 2007 I travelled around the area together with my children and …"</td>
      <td>An optional message users can provide to tell others
why they like or dislike this project
</td>
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
(<a href="opinion_details.md">opinion details</a>)
</td>
    </tr>
    <tr>
      <th align="left">project</th>
      <td>Link to the project this opinion belongs to
(<a href="project_details.md">project details</a>)
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
      <th align="left">author.picture.original</th>
      <td>Original size as uploaded by the user</td>
    </tr>
</table>

## Response Example

```json
{
  "total_entries": 634,
  "offset": 0,
  "total_pages": 212,
  "current_page": 1,
  "per_page": 3,
  "data": [
    {
      "id": 964,
      "created_at": "2009-03-18T16:34:37Z",
      "donated_amount_in_cents": null,
      "score": "positive",
      "author": {
        "name": "A. Bald",
        "picture": {
          "links": [
            {
              "rel": "original",
              "href": "http://asset1.betterplace.org/assets/default/user_profile_picture/fill_100x100_default.betterplace.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "http://www.betterplace.org/en/users/alexandra_b"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/en/api_v4/users/2763/contact_data.json"
          }
        ]
      },
      "message": "Ich unterstütze Skateistan weil: <br />a) ich die Projektleiter Oliver uns Max kenne und von ihnen überzeugt bin,<br />b) ich durch alles, was ich (auch durch meine Arbeit als Designerin) aus Kabul mitbekommen habe sehr berührt wurde,<br />c) ich persönlich als Designerin für Skateistan involviert bin!",
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/en/api_v4/projects/1114/opinions/964.json"
        },
        {
          "rel": "project",
          "href": "https://api.betterplace.org/en/api_v4/projects/1114.json"
        }
      ]
    },
    {
      "id": 1024,
      "created_at": "2009-03-31T18:21:52Z",
      "donated_amount_in_cents": null,
      "score": "positive",
      "author": {
        "name": "d. habibi",
        "picture": {
          "links": [
            {
              "rel": "original",
              "href": "http://asset1.betterplace.org/uploads/user/profile_picture/000/010/834/original_CIMG4253.JPG"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "http://www.betterplace.org/en/users/omar_a"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/en/api_v4/users/10834/contact_data.json"
          }
        ]
      },
      "message": "ich bin Fürsprecher dieses Projektes, da ich in Kabul geboren bin und meine Kindheit dort verbracht habe, in Deutschland dann als Jugendlicher selbst geskatet habe, jetzt hier studiere und das Thema meiner Diplomarbeit \"Leben in Kabul\" heisst.<br />Ich bin begeistert von dieser Idee \"Skateistan\". Nicht nur wegen der direkten Hilfe vor Ort in Kabul, sondern auch wegen dem großen Presseecho überall in der Welt, wo man sonst nur Nachrichten aus Afghanistan hört, wenn mal wieder ein Attentat verübt wurde, oder nach Bin Laden gesucht wird.",
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/en/api_v4/projects/1114/opinions/1024.json"
        },
        {
          "rel": "project",
          "href": "https://api.betterplace.org/en/api_v4/projects/1114.json"
        }
      ]
    },
    {
      "id": 1323,
      "created_at": "2009-06-14T08:58:06Z",
      "donated_amount_in_cents": null,
      "score": "positive",
      "author": {
        "name": "m. mohsen",
        "picture": {
          "links": [
            {
              "rel": "original",
              "href": "http://asset1.betterplace.org/uploads/user/profile_picture/000/011/827/original_Mirwais_Mohsen_image.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "http://www.betterplace.org/en/users/mirwais_m"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/en/api_v4/users/11827/contact_data.json"
          }
        ]
      },
      "message": "In my point of view, Skateistan is the key to changing the lives of children in Afghanistan. Helping my brothers and sisters  will change  our country because these children are the future of Afghanistan. Providing them with education, health care and teaching them respect for each other and their families will help them be productive and responsible members of our community.  They have learned a lot from skating, and I work for Skateistan in order to make the dreams of these children come true, and break these nationalism ethnic barriers.",
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/en/api_v4/projects/1114/opinions/1323.json"
        },
        {
          "rel": "project",
          "href": "https://api.betterplace.org/en/api_v4/projects/1114.json"
        }
      ]
    }
  ]
}
```

