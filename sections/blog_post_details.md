
# Project Blog Post Details ⇄ [List](blog_posts_list.md)

```nginx
GET https://api.betterplace.org/en/api_v4/projects/1114/blog_posts/88972.json
```

The details of a betterplace.org project blog post.
The details and list view show the same data.

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
    <td><code>1114</code></td>
    <td>required</td>
    <td>Project-id as an integer number ≥ 14.</td>
  </tr>
  <tr>
    <th align="left">id</th>
    <td><code>88972</code></td>
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
  <table>
    <tr>
      <th colspan="4">Links</th>
    </tr>
    <tr>
      <th>Linkname</th>
      <th colspan="3">Description</th>
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
  "id": 88972,
  "created_at": "2013-10-30T11:39:27Z",
  "updated_at": "2013-10-30T11:39:27Z",
  "lang": "en",
  "type": "BlogPost",
  "title": "First Climbing Contest Held in Afghanistan",
  "body": "<p><img src=\"http://skateistan.org/sites/default/files/users/duncan.buck/1381505_10201192263663306_1801301726_n.jpeg\"><br></p>\n<p>On\r\n Saturday 28th September, Skateistan Kabul's volunteers and staff took \r\npart in the inaugural indoor climbing competition held at the facility, \r\nwith both girls and boys competing (ages 11-22). This was the 1st \r\nclimbing competition that has taken place at Skateistan and the 1st \r\nknown climbing contest held in Afghanistan!<br><br>The climbing \r\ncompetition had both female and male categories with contests that \r\nincluded speed climbing and fastest rope coil. The competition was \r\njudged by our amazing volunteer climbing teachers, including the \r\ncompetition organiser Gio Trambaiolo who has been instrumental in \r\nteaching climbing to the Skateistan volunteers. Gio has volunteered as a\r\n climbing teacher nearly each week for well over a year. Skateistan is \r\nextremely lucky to have such a wonderful team of dedicated volunteers, \r\nwho include around a dozen foreigners with certified climbing \r\nbackgrounds.</p>\n<p>\" Everyone did very well, it's amazing to\r\n see how the instructors and volunteers have progressed over the past \r\nfew months. \" - Gio, volunteer climbing teacher</p>\n<p>Each \r\nweek since June 2012, climbing lessons have been provided \r\nto Skateistan's Youth Leaders, who are Afghan staff and volunteers with \r\nthe project. They have learned climbing techniques, as well as built \r\nup trust and respect for each other through the sport. It is been \r\ninspiring to watch the volunteers develop as climbers and to see the \r\nhigh skill level our Youth Leaders have developed since the program took\r\n shape last year. Through the program, 14 young Afghans (50% girls) have\r\n received certificates to be Beginner Climbing Instructors, and they now\r\n facilitate climbing classes with more than 400 students who attend \r\nSkateistan.</p>\n<p>A brief prize ceremony was held the following week to \r\ngive the final results of the competition, as well as some prizes which \r\nwere given to everyone who participated.</p>We\r\n want to thank all the climbing volunteers who have created a hugely \r\nsuccesful sports program for our staff and students. We wish to thank \r\nGiovanni Trambaiolo, Sheilagh Henry, Kate Hughes, Mindy Visser, Colin R,\r\n Erin Blankenship, Jeffery Dow, Kelsey Noonan, Sarah-Jean \r\nCunningham, and Stephanie Faser. Your constant creativity and innovative\r\n training have made climbing one of the leading activities for the Youth\r\n Leaders at Skateistan. The development of students who attend your \r\nclasses has been a great pleasure to watch, and will benefit hundreds of\r\n children who will continue to be taught by their Afghan peers.<p><br><img src=\"http://skateistan.org/sites/default/files/users/duncan.buck/2013-09-24-peace-day-eventimg_1269.jpg\"></p>\n<p><br></p>\n<br>",
  "author": {
    "name": "E. Kinast",
    "picture": {
      "links": [
        {
          "rel": "original",
          "href": "/paperclip/000/330/773/original_Picture_023.jpg"
        },
        {
          "rel": "large_attention_deprecated",
          "href": "/paperclip/000/330/773/default_Picture_023.jpg"
        },
        {
          "rel": "profile_attention_deprecated",
          "href": "/paperclip/000/330/773/profile_Picture_023.jpg"
        },
        {
          "rel": "thumb_attention_deprecated",
          "href": "/paperclip/000/330/773/thumb_Picture_023.png"
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
  "links": [
    {
      "rel": "self",
      "href": "https://api.betterplace.org/en/api_v4/blog_posts/88972.json"
    },
    {
      "rel": "platform",
      "href": "http://www.betterplace.org/en/projects/1114-skateistan-afghanistan/news/88972"
    },
    {
      "rel": "documentation",
      "href": "https://github.com/betterplace/betterplace_apidocs/blob/master/sections/blog_post_details.md"
    }
  ]
}
```

