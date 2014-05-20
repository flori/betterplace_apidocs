
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
  "total_entries": 378747,
  "offset": 0,
  "total_pages": 126249,
  "current_page": 1,
  "per_page": 3,
  "data": [
    {
      "id": 8236,
      "created_at": "2011-10-06T12:06:18Z",
      "donated_amount_in_cents": null,
      "score": "positive",
      "author": {
        "name": "W. Watermann",
        "picture": {
          "links": [
            {
              "rel": "fill_100x100",
              "href": "http://asset1.betterplace.org/assets/default/user_profile_picture/fill_100x100_default.betterplace.jpg"
            },
            {
              "rel": "original",
              "href": "http://asset1.betterplace.org/assets/default/user_profile_picture/fill_100x100_default.betterplace.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.org/en/users/winfried_w3"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/en/api_v4/users/224418/contact_data.json"
          }
        ]
      },
      "message": "Also, ich kann das Projekt von Katrin nur wärmstens empfehlen, es finanziell zu unterstützen. Ich kenne Katrin aus unserer gemeinsamen Zeit bei Unicef in FFM und vertraue Ihr 100 %.<br />Katrin ist SOOOOOWAS von entschlossen zu helfen, und auch ohne das Projekt im Moment im Detail zu kennen: da ist JEDER Euro mit 100 % iger Sicherheit bestens angelegt.<br /><br />Winfried",
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/en/api_v4/projects/7838/opinions/8236.json"
        },
        {
          "rel": "project",
          "href": "https://api.betterplace.org/en/api_v4/projects/7838.json"
        }
      ]
    },
    {
      "id": 8243,
      "created_at": "2011-10-07T09:20:24Z",
      "donated_amount_in_cents": null,
      "score": "positive",
      "author": {
        "name": "M. Kugler",
        "picture": {
          "links": [
            {
              "rel": "fill_100x100",
              "href": "http://asset1.betterplace.org/uploads/user/profile_picture/000/200/066/fill_100x100_original_222752_14564057157_531862157_477022_6957_n.jpg"
            },
            {
              "rel": "original",
              "href": "http://asset1.betterplace.org/uploads/user/profile_picture/000/200/066/crop_original_original_222752_14564057157_531862157_477022_6957_n.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.org/en/users/michael_k72"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/en/api_v4/users/200066/contact_data.json"
          }
        ]
      },
      "message": "Tolle Arbeit, weiter so! LG, Michael K.",
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/en/api_v4/projects/6599/opinions/8243.json"
        },
        {
          "rel": "project",
          "href": "https://api.betterplace.org/en/api_v4/projects/6599.json"
        }
      ]
    },
    {
      "id": 8248,
      "created_at": "2011-10-08T15:13:51Z",
      "donated_amount_in_cents": null,
      "score": "positive",
      "author": {
        "name": "H. Wilde",
        "picture": {
          "links": [
            {
              "rel": "fill_100x100",
              "href": "http://asset1.betterplace.org/uploads/user/profile_picture/000/224/017/fill_100x100_original_Helmuth_Wilde2.jpg"
            },
            {
              "rel": "original",
              "href": "http://asset1.betterplace.org/uploads/user/profile_picture/000/224/017/crop_original_original_Helmuth_Wilde2.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.org/en/users/helmuth_w"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/en/api_v4/users/224017/contact_data.json"
          }
        ]
      },
      "message": "Jahrelang hatte ich ein schlechtes Gewissen, da ich eigentlich nicht wirklich wohltätig war. Es lag aber auch zum großen Teil daran, daß mir die großen Organisationen wie z.B. W....V....., etc wegen der hohen Verwaltungskosten usw. eher suspekt waren. Als ich dann auf Harambee stieß, war ich sofort Feuer und Flamme. Besonders schätze ich den engen Kontakt zu den Patenkindern, aber auch die Transparenz der Aktivitäten. Mittlerweile bin ich ca. 2 Jahre dabei, bereits das 2. mal vor Ort und immer mehr begeistert, was da geleistet wird. Mein Lieblingsauspruch: \"Ich zahle für mein Patenkind € 25,- und in Kilifi kommen € 35,- an!\" Jambo, Jambo",
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/en/api_v4/projects/7806/opinions/8248.json"
        },
        {
          "rel": "project",
          "href": "https://api.betterplace.org/en/api_v4/projects/7806.json"
        }
      ]
    }
  ]
}
```

