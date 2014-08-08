
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
      <th align="left">updated_at</th>
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
  "total_entries": 651,
  "offset": 0,
  "total_pages": 217,
  "current_page": 1,
  "per_page": 3,
  "data": [
    {
      "id": 1572,
      "created_at": "2009-07-22T20:23:26Z",
      "updated_at": "2009-07-22T20:23:26Z",
      "donated_amount_in_cents": null,
      "score": "positive",
      "author": {
        "name": "U. Köhler",
        "picture": {
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/015/597/fill_100x100_original_Ute_SchloGraFe.sw1.jpg"
            },
            {
              "rel": "original",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/015/597/crop_original_original_Ute_SchloGraFe.sw1.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.org/en/users/ute_k2"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/en/api_v4/users/15597/contact_data.json"
          }
        ]
      },
      "message": "Ich bin Fürsprecherin des Projekts Skateistan, weil ich den Projektverantwortlichen Max Henninger letztes Jahr im Zuge meines Studiums kennengelernt habe und er uns über seine Arbeit in Afghanistan berichtet hat. <br />Ich bin begeistert von seiner Überzeugung, seiner Tatkraft und seinem Mut, Kindern in einem vom Krieg erschütterten Land ein bisschen Lebensfreude zu geben!",
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/en/api_v4/projects/1114/opinions/1572.json"
        },
        {
          "rel": "project",
          "href": "https://api.betterplace.org/en/api_v4/projects/1114.json"
        }
      ]
    },
    {
      "id": 1584,
      "created_at": "2009-07-24T13:52:27Z",
      "updated_at": "2009-07-24T13:52:27Z",
      "donated_amount_in_cents": null,
      "score": "positive",
      "author": {
        "name": "D. Habenicht",
        "picture": {
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/015/688/fill_100x100_original_Daniel1.jpg"
            },
            {
              "rel": "original",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/015/688/crop_original_original_Daniel1.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.org/en/users/daniel_h14"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/en/api_v4/users/15688/contact_data.json"
          }
        ]
      },
      "message": "Ich verlege seit 2007 das Buch von Boris Barschow: \"Kabul, ich komme wieder\". Mittlerweile ist er zum dritten mal in Afghanistan. Da ich durch ihn ein wenig mit der Problematik des Landes vertraut wurde, habe ich auch ein Auge für andere schöne Aktionen für Frieden und Völkerverständigung. Skateistan ist eine unglaubliche Brücke zum Menschen. Die Skate-Community hat die Kraft diese Brücke zu stärken und das ich möchte tatkräftig unterstützen.<br /><br />bless<br />Daniel",
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/en/api_v4/projects/1114/opinions/1584.json"
        },
        {
          "rel": "project",
          "href": "https://api.betterplace.org/en/api_v4/projects/1114.json"
        }
      ]
    },
    {
      "id": 5442,
      "created_at": "2010-11-14T08:43:17Z",
      "updated_at": "2010-11-14T08:43:17Z",
      "donated_amount_in_cents": null,
      "score": "positive",
      "author": {
        "name": "J. S.",
        "picture": {
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/018/797/fill_100x100_original_profil.jpg"
            },
            {
              "rel": "original",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/018/797/crop_original_original_profil.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.org/en/users/joel_s"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/en/api_v4/users/18797/contact_data.json"
          }
        ]
      },
      "message": "Wenig kann viel bewirken. Gerade Skateistan vermag mit einem sehr kleinen Budget - für Afghanistan  klein - wirklich ne Menge zu bewegen, und so das Leben von ner Menge Kids nachhaltig verändern.<br />Vor Ort durfte ich erfahren, wie effizient und hart die Jungs und Mädels von Skateistan in diesem schwierigen Umfeld arbeiten und wie mit den ihnen zur Verfügung stehenden Mitteln sorgsam gewirtschaftet wird.<br />Keep goin !!!",
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/en/api_v4/projects/1114/opinions/5442.json"
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

