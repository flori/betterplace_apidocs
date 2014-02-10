
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
      <td>string</td>
      <td>53</td>
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
      <th align="left">payout</th>
      <td>null &#124; undefined</td>
      <td>TODO</td>
      <td></td>
    </tr>
    <tr>
      <th align="left">author</th>
      <td>string</td>
      <td>"Till B."</td>
      <td>Display name of a betterplace.org user.
Possible formats: "Till B.", "T. Behnke", "Till Behnke"
</td>
    </tr>
    <tr>
      <th colspan="4">Links</th>
    </tr>
    <tr>
      <th>Linkname</th>
      <th>Description</th>
    </tr>
    <tr>
      <th align="left">self</th>
      <td colspan="3">Link to this resource itself
(<a href="blog_post_details.md">blog post details</a>)
</td>
    </tr>
    <tr>
      <th align="left">platform</th>
      <td colspan="3">Permalink to betterplace.org</td>
    </tr>
    <tr>
      <th align="left">documentation</th>
      <td colspan="3">Link to this resource in the documentation
</td>
    </tr>
  </table>
</table>

## Response Example

```json
{
  "total_entries": 0,
  "offset": 0,
  "total_pages": 0,
  "current_page": 1,
  "per_page": 2,
  "data": [

  ]
}
```

