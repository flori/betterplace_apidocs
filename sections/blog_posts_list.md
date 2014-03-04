
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
</table>

## Response Example

```json
{
  "total_entries": 82,
  "offset": 0,
  "total_pages": 41,
  "current_page": 1,
  "per_page": 2,
  "data": [
    {
      "id": 3900,
      "created_at": "2009-03-10T12:21:31Z",
      "updated_at": "2009-03-10T12:21:31Z",
      "lang": "de",
      "type": "BlogPost",
      "title": "Skateistan in N24",
      "body": "Kommenden Freitag (13.03.), 12:30 Uhr, gibt es eine halbe Stunde Skateistan auf dem Nachrichtensender N24. Reinschauen lohnt sich!",
      "author": {
        "name": "M. Henninger",
        "picture": {
          "links": [
            {
              "rel": "original",
              "href": "/paperclip/000/041/702/original_maxn_skate.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "http://www.betterplace.org/en/users/max_h2"
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
          "href": "https://api.betterplace.org/en/api_v4/blog_posts/3900.json"
        },
        {
          "rel": "platform",
          "href": "http://www.betterplace.org/en/projects/1114-skateistan-afghanistan/news/3900"
        },
        {
          "rel": "documentation",
          "href": "https://github.com/betterplace/betterplace_apidocs/blob/master/sections/blog_post_details.md"
        }
      ]
    },
    {
      "id": 3917,
      "created_at": "2009-03-11T19:46:27Z",
      "updated_at": "2009-03-11T20:05:14Z",
      "lang": "de",
      "type": "BlogPost",
      "title": "Mirwais",
      "body": "<p>Wir haben unsere erste Unterst&uuml;tzung erfahren - vielen Dank daf&uuml;r auch im Namen von Mirwais, der dadurch seine Arbeit f&uuml;r Skateistan fortsetzen kann. An dieser Stelle m&ouml;chte ich Mirwais etwas n&auml;her vorstellen:&nbsp;</p>\r\n<p>INTERVIEW WITH Mirwais Ghulam Mohammad</p>\r\n<p>HOW DID YOU FIND OUT ABOUT SKATEBOARDING?\r\nI was washing cars in Macrorayan when I first saw Oliver, Sharna, Shams, Mirwais and Moneer skating. I left the car I was washing and went to join the other children playing on the skateboards. I really liked it the first time. From then on, every time I saw Oliver and the others riding their motorcycles piled high with skateboards I would leave the cars and go to them to practice skating. After some months, Oliver asked me to join the Skateistan team.</p>\r\n<p>WHAT WERE YOU DOING BEFORE JOINING THE SKATEISTAN TEAM? \r\nBefore joining Skateistan, I was washing cars for 7 years. I had a number of special customers who would look for me, four foreigners and eighteen Afghans. For a four-wheel drive, I would make 80 Afghanis (around 1 Euro) for one hours work. I wash between 3 and 4 cars on a good day but I have to pay 20% of my wages to the guards who work nearby so they could buy tobacco. They are much bigger than me! In winter it was an especially difficult job to clean the cars as it is often below freezing and it is hard to scrape the ice from under the cars.</p>\r\n<p>WHAT IS YOUR ROLE IN SKATEISTAN? \r\nI have been working for Skateistan for one and a half months. I am very happy in my job, I take care of the Skateistan office and guesthouse and make sure all the equipment is clean and oiled, ready for skating. When we teach the children, it is my job to help them as much as possible and make sure everyone is sharing the boards. I teach the boys new tricks and collect all the boards at the end of each session.</p>\r\n<p>WHAT DO YOU LIKE BEST ABOUT SKATEBOARDING?\r\nI like learning how to ollie, drop off ledges and skate fast around the transition of the fountain that we skate. My favourite trick is to ollie and I practice this as much as I can in my spare time. I can now ollie almost 20 cm off the ground.</p>\r\n<p>DO ANY OF YOUR SIBLINGS SKATE? \r\nTwo of my younger brothers are skating. They wanted to learn after watching me skate. Now I teach them how to drop into the fountain, how to ollie and how to skate fast around the transition of the fountain.</p>\r\n<p>WHAT DO YOU THINK OF SEEING FEMALE SKATEBOARDERS IN KABUL? \r\nI think it is good that there are girls skating. When I first saw the girls skating, it inspired me to try harder so I could be as good as them. Some of the girls skate better than the boys!</p>\r\n<p>WHAT WOULD YOU LIKE TO DO IN THE FUTURE? \r\nI would like to keep skateboarding and eventually become the champion skater of Afghanistan!</p>\r\n<p>Mirwais Ghulam Mohammad is 16 years old and has four brothers and three sisters.</p>",
      "author": {
        "name": "M. Henninger",
        "picture": {
          "links": [
            {
              "rel": "original",
              "href": "/paperclip/000/041/702/original_maxn_skate.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "http://www.betterplace.org/en/users/max_h2"
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
          "href": "https://api.betterplace.org/en/api_v4/blog_posts/3917.json"
        },
        {
          "rel": "platform",
          "href": "http://www.betterplace.org/en/projects/1114-skateistan-afghanistan/news/3917"
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

