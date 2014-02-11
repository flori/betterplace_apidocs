
# Project Opinion Details ⇄ [List](opinions_list.md)

```nginx
GET https://api.betterplace.org/en/api_v4/projects/38/opinions/22.json
```

The details of a betterplace.org project opinion (donate money).
The details and list view show the same data.

This will always show the data if a valid opinion id is given, even if that opinion
does not belong to the project in the URL.

*For [betterplace.org clients](../README.md#client-api):*
There is no client-scoped-url.
Please use the api calls that are provided inside the client project _url_ response
to make sure you only request data that is associated with one of your projects.


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
    <td><code>38</code></td>
    <td>required</td>
    <td>Project-id as an integer number ≥ 14.</td>
  </tr>
  <tr>
    <th align="left">id</th>
    <td><code>22</code></td>
    <td>required</td>
    <td>Blog-post-id as an integer number ≥ 9.</td>
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
#### Links
  <table>
    <tr>
      <th>Linkname</th>
      <th colspan="3">Description</th>
    </tr>
    <tr>
      <th align="left">self</th>
      <td colspan="3">Link to this resource itself
(<a href="opinion_details.md">opinion details</a>)
</td>
    </tr>
    <tr>
      <th align="left">project</th>
      <td colspan="3">Link to the project this opinion belongs to
(<a href="project_details.md">project details</a>)
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
#### Links
  <table>
    <tr>
      <th>Linkname</th>
      <th colspan="3">Description</th>
    </tr>
    <tr>
      <th align="left">author.original</th>
      <td colspan="3">Original size as uploaded by the user</td>
    </tr>
    <tr>
      <th align="left">author.large_attention_deprecated</th>
      <td colspan="3">Large size – ATTENTION, this feature is DEPRECATED and will be removed at the end of may 2013. Please use the orginal format. Read the project pictures-documentation at "custom image sizes" for other solutions"</td>
    </tr>
    <tr>
      <th align="left">author.profile_attention_deprecated</th>
      <td colspan="3">Medium size – ATTENTION, this feature is DEPRECATED. See above.</td>
    </tr>
    <tr>
      <th align="left">author.thumb_attention_deprecated</th>
      <td colspan="3">Thumbnail size – ATTENTION, this feature is DEPRECATED. See above.</td>
    </tr>
  </table>
</table>

## Response Example

```json
{
  "id": 22,
  "created_at": "2007-11-24T13:14:02Z",
  "score": "positive",
  "author": {
    "name": "G. Krabbe",
    "picture": {
      "links": [
        {
          "rel": "original",
          "href": "/paperclip/000/004/520/original_Schule_Leutersdorf_2.JPG"
        },
        {
          "rel": "large_attention_deprecated",
          "href": "/paperclip/000/004/520/default_Schule_Leutersdorf_2.jpg"
        },
        {
          "rel": "profile_attention_deprecated",
          "href": "/paperclip/000/004/520/profile_Schule_Leutersdorf_2.jpg"
        },
        {
          "rel": "thumb_attention_deprecated",
          "href": "/paperclip/000/004/520/thumb_Schule_Leutersdorf_2.png"
        }
      ]
    },
    "links": [
      {
        "rel": "platform",
        "href": "http://www.betterplace.org/en/users/giesela_k"
      },
      {
        "rel": "contact_data",
        "href": "https://api.betterplace.org/en/api_v4/users/759/contact_data.json"
      }
    ]
  },
  "message": "Ich bin zweimal in Bolivien gewesen, auch in El Alto und im COMPA, und ich habe gesehen, wie schwer das (Über-)leben für viele Leute ist. Wie wichtig Bildung ist, sollte ich als ehemalige Lehrerin ja wissen.... Das hier vorgestellte Projekt erinnert mich an die Fahrbibliotheken in der ehemaligen DDR; und wenn hier benachteiligten Kindern und Jugendlichen in Gegenden ohne kulturelle Infrastruktur eine adäquate Form von Bildung ermöglicht werden soll, ist das nur zu unterstützen. Nach meinen Möglichkeiten werde ich das Projekt unterstützen.",
  "links": [
    {
      "rel": "self",
      "href": "https://api.betterplace.org/en/api_v4/projects/35/opinions/22.json"
    },
    {
      "rel": "project",
      "href": "https://api.betterplace.org/en/api_v4/projects/35.json"
    }
  ]
}
```

