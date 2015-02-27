
# Fundraising Event List ⇄ [Details](fundraising_event_details.md)

```Rebol
GET https://api.betterplace.org/de/api_v4/fundraising-events.json?around=10997+Berlin%2C+Germany&facets=completed%3Afalse&order=rank%3ADESC&q=Skateistan&scope=location
```

A list of betterplace.org fundraising events (donate money).
Results are contained in a *data* attribute.

*For [betterplace.org clients](../README.md#client-api):*
Use this resource like `/clients/PERMALINK/fundraising-events.json`


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
    <td>Use the scope to specify how the search-query <code>q</code> should behave:
<ul>
<li>"no scope" (default) performs a full text search
<li><code>human_name</code> searches only on the manager-fullname and carrier-fullname.
  Use this to get all entities by "Unicef" or by "Till Behnke".
<li><code>location</code> does a reverse geocoding lookup.
  This lookup returns a bounding-box. We transform this bounding-box in a
  rectangle that is large enough to encapsulate the whole bounding-box.
  We then return all entities that belong to this rectangle.
</ul>
<a href="../README.md#request-parameter-format">Learn how to format the parameter</a>.
</td>
  </tr>
  <tr>
    <th align="left">q</th>
    <td><code>Skateistan</code></td>
    <td>no</td>
    <td>Search query. The searches behaviour is based on the scope.</td>
  </tr>
  <tr>
    <th align="left">around</th>
    <td><code>10997 Berlin, Germany</code></td>
    <td>no</td>
    <td>Order the results by the distance to the given location from near to far.
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
are send to the google location service. For the provided response we
take a fitting lat/lng value as center of the search. So in theory,
you can use any search that works for google maps.
<br>
Check the <code>around_location</code> to see what latitude/longitude
values have been used for the query.
</td>
  </tr>
  <tr>
    <th align="left">facets</th>
    <td><code>completed:false</code></td>
    <td>no</td>
    <td>Filter the result set.
Documented and supported filters are:
<ul>
<li><code>tax_deductible:true/false</code>
<li><code>completed:true/false</code>
<li><code>prohibit_donations:true/false</code>
</ul>
It is possible to set multiple facet filters.
<a href="../README.md#request-parameter-format">Learn how to format the parameter</a>.
</td>
  </tr>
  <tr>
    <th align="left">order</th>
    <td><code>rank:DESC</code></td>
    <td>no</td>
    <td>Order the results by <code>score</code> (only when a query (q) is given),
<code>rank</code>, <code>id</code>, <code>progress_percentage</code>,
<code>tax_deductible</code>, <code>created_at</code>, <code>updated_at</code>,
<code>last_donation_at</code>, <code>completed</code>.
Use the optional <code>ASC</code> (default) or <code>DESC</code>.
<a href="../README.md#request-parameter-format">Learn how to format the parameter</a>.
<br>
The default order is the same as for the
<a href="https://www.betterplace.org/en/projects/list?search_form%5Bfilters%5D%5Btype%5D=Group">betterplace.org fundraising events list</a>:
<code>completed:asc| score:desc | rank:desc| last_donation_at:desc</code>
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
      <td>True if the fundraising event is marked as tax deductible.
If so, Users can request a tax-receipt that can be used
with the german tax authorities.
[More about this](http://www.betterplace.org/c/hilfe/projekt-steuerlich-absetzbar/).
</td>
    </tr>
    <tr>
      <th align="left">donations_prohibited</th>
      <td>boolean</td>
      <td>false</td>
      <td>True if the fundraising event must not receive donations. This might
happen if a tax-receipt of german tax authorities rans out.
</td>
    </tr>
    <tr>
      <th align="left">closed_at</th>
      <td>string</td>
      <td>"1994-11-05T13:15:30Z"</td>
      <td>DateTime (ISO8601 with Timezone) when the fundraising event was closed</td>
    </tr>
    <tr>
      <th align="left">donor_count</th>
      <td>number</td>
      <td>46</td>
      <td>Number of unique donors, based on the payment-email-address</td>
    </tr>
    <tr>
      <th align="left">donated_amount_in_cents</th>
      <td>number</td>
      <td>232323</td>
      <td>How many cents were already raised with the fundraising event</td>
    </tr>
    <tr>
      <th align="left">requested_amount_in_cents</th>
      <td>number</td>
      <td>12382</td>
      <td>How many cents were requested to be raised with the fundraising event</td>
    </tr>
    <tr>
      <th align="left">progress_percentage</th>
      <td>number</td>
      <td>5</td>
      <td>% financed.
</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="contact-ref" href="#contact">
            ↓contact
          </a>
        </th>
      <td>object</td>
      <td>TODO</td>
      <td>The public face of the fundraising event / fundraising event manager</td>
    </tr>
    <tr>
        <th align="left" style="white-space: nowrap">
          <a id="profile_picture-ref" href="#profile_picture">
            ↓profile_picture
          </a>
        </th>
      <td>null &#124; object</td>
      <td></td>
      <td>TODO</td>
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
      <th align="left">contact.name</th>
      <td>null &#124; string</td>
      <td>"Till B."</td>
      <td>Display name of a betterplace.org user.
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
      <td>string</td>
      <td>//asset1.betterplace.org/uploads/user/profile_picture/000/000/001/fill_100x100_original_tb.jpg</td>
      <td>User profile picture or a fallback image</td>
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
      <td>boolean</td>
      <td>true</td>
      <td>Specifies whether a fallback image is given or not</td>
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
      <td>boolean</td>
      <td>true</td>
      <td>Specifies whether a fallback image is given or not</td>
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
(<a href="fundraising_event_details.md">fundraising event details</a>)
</td>
    </tr>
    <tr>
      <th align="left">platform</th>
      <td>Permalink to betterplace.org</td>
    </tr>
    <tr>
      <th align="left">new_client_donation</th>
      <td>Link to the donation form. Templated, needs insertion of the client_id.
</td>
    </tr>
    <tr>
      <th align="left">new_donation</th>
      <td>Link to the regular donation form.
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
<a href="../README.md#client-api">authenticated as a client</a> with matching
access rights in order to see this information.
</td>
    </tr>
    <tr>
      <th align="left">contact.picture.fill_100x100</th>
      <td>100x100 Pixel</td>
    </tr>
    <tr>
      <th align="left">contact.picture.original</th>
      <td>Maximum sized image. This is the original image with default-cropping or user-cropping applied.</td>
    </tr>
    <tr>
      <th align="left">profile_picture.fill_960x500</th>
      <td>950x500 Pixel</td>
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
      <td>Maximum sized image. This is the original image with default-cropping or user-cropping applied.</td>
    </tr>
</table>

## Response Example

```json
{
  "total_entries": 11,
  "offset": 0,
  "total_pages": 4,
  "current_page": 1,
  "per_page": 3,
  "data": [
    {
      "id": 20476,
      "created_at": "2014-12-22T23:18:27+01:00",
      "updated_at": "2015-02-20T17:26:29+01:00",
      "title": "LET'S SHAPE SKATEISTAN AFGHANISTAN",
      "description": ">> Once you have donated, feel free to send an email with your full name to win@kaywaz.com To get one of the 50 pieces limited new album of KAYWAZ (www.KAYWAZ.com) for free. First come, first serve. They will be send to you by february! &lt;&lt; <br /><br />--<br /><br />Who is rasing money for who? We as the World Economic Forum Global Shapers Hub Frankfurt (www.globalshapersfrankfurt.de) & KAYWAZ.com are raising money for the Nonprofit organisation Skateistan (www.skateistan.org) in Afghanistan to give girls & boys access to creative education in a safe environment. <br /><br />Skateistan has developed an innovative, youth-led programming that builds confidence, trust and social capital among children. It uses “the hook” of skateboarding to connect kids with education. Skateistan provides opportunities for education, leadership, and creative thinking that help break the cycles of poverty and exclusion. | Check out some videos about Skateistan here: www.vimeo.com/skateistan<br /><br />--<br /><br />About: Karim alias KAYWAZ is the incoming curator of the Global Shapers Hub Frankfurt and an entrepreneur & investor but also a passionate artist & musician. You can also meet KAYWAZ & SKATEISTAN on January 7, 2015 in Berlin for an exlusive concert & interview: www.facebook.com/events/1396192070671743",
      "tax_deductible": true,
      "donations_prohibited": false,
      "closed_at": null,
      "donor_count": 14,
      "donated_amount_in_cents": 50000,
      "requested_amount_in_cents": 50000,
      "progress_percentage": 100,
      "contact": {
        "name": "Karim M.",
        "picture": {
          "fallback": true,
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/419/722/fill_100x100_kaywaz_klein.jpg"
            },
            {
              "rel": "original",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/419/722/crop_original_kaywaz_klein.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.org/de/users/karim_m2"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/de/api_v4/users/419722/contact_data.json"
          }
        ]
      },
      "profile_picture": {
        "fallback": true,
        "links": [
          {
            "rel": "fill_960x500",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/020/476/fill_960x500_kaywaz_fundraising_2.jpg"
          },
          {
            "rel": "fill_618x322",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/020/476/fill_618x322_kaywaz_fundraising_2.jpg"
          },
          {
            "rel": "fill_270x141",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/020/476/fill_270x141_kaywaz_fundraising_2.jpg"
          },
          {
            "rel": "original",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/020/476/crop_original_kaywaz_fundraising_2.jpg"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/fundraising-events/20476.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/fundraising-events/globalshapersfrankfurt"
        },
        {
          "rel": "new_client_donation",
          "href": "https://www.betterplace.org/de/fundraising-events/20476/client_donations/new?client_id=%7Bclient_id%7D",
          "templated": true
        },
        {
          "rel": "new_donation",
          "href": "https://www.betterplace.org/de/fundraising-events/20476/donations/new"
        }
      ]
    },
    {
      "id": 18750,
      "created_at": "2014-08-15T12:34:14+02:00",
      "updated_at": "2015-02-22T17:20:21+01:00",
      "title": "Skateistan Fundraiser @ IC",
      "description": "We have kicked off our first Skateistan Fundraiser at Inhouse Consulting! <br /><br />What is Skateistan? <br /># A non-profit organization using skateboarding as a tool to create new opportunities for children and potential for change in Afghanistan & Cambodia<br /># Using skateboarding to build trust, to support kids’ education and to strengthen their community sense &  leadership skills <br /># Or simply … a really cool organization creating change for the better in a very tough part of this world (https://www.skateistan.org/content/our-story)<br /><br />How will the fundraiser work? <br />Our final target is to raise € 1,500 by the end of the year. To achieve the target we’re relying on your donations and we will organize a few events to share Skateistan’s work.<br />\t<br />So what happens when we hit the target? <br />We will skate from Bonn to Cologne in the speed of yellow (+ drinks for all donors at the other end)<br /><br />Cool! How can I support the cause?  <br />1. Donate via this fundraising site<br />2. Join the team & help us with new ideas (or your arms & legs)<br />3. Share the word with other colleagues & friends<br /><br />…and stay tuned for more activities planned in Q4. Let’s keep Skateistan rolling!<br />Thank you very much & best regards, <br /><br />Andreas, Anja & the PGFF/Tech",
      "tax_deductible": true,
      "donations_prohibited": false,
      "closed_at": null,
      "donor_count": 16,
      "donated_amount_in_cents": 128900,
      "requested_amount_in_cents": 150000,
      "progress_percentage": 85,
      "contact": {
        "name": "A. Bicking",
        "picture": {
          "fallback": true,
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://asset1.betterplace.org/assets/default/user_profile_picture/fill_100x100_default.betterplace.jpg"
            },
            {
              "rel": "original",
              "href": "https://asset1.betterplace.org/assets/default/user_profile_picture/fill_100x100_default.betterplace.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.org/de/users/andreas_b86"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/de/api_v4/users/394488/contact_data.json"
          }
        ]
      },
      "profile_picture": {
        "fallback": true,
        "links": [
          {
            "rel": "fill_960x500",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/018/750/fill_960x500_aboutus_top_fazila.png"
          },
          {
            "rel": "fill_618x322",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/018/750/fill_618x322_aboutus_top_fazila.png"
          },
          {
            "rel": "fill_270x141",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/018/750/fill_270x141_aboutus_top_fazila.png"
          },
          {
            "rel": "original",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/018/750/crop_original_aboutus_top_fazila.png"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/fundraising-events/18750.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/fundraising-events/skateistan_fundraiser"
        },
        {
          "rel": "new_client_donation",
          "href": "https://www.betterplace.org/de/fundraising-events/18750/client_donations/new?client_id=%7Bclient_id%7D",
          "templated": true
        },
        {
          "rel": "new_donation",
          "href": "https://www.betterplace.org/de/fundraising-events/18750/donations/new"
        }
      ]
    },
    {
      "id": 13904,
      "created_at": "2013-04-14T11:50:33+02:00",
      "updated_at": "2014-01-08T17:40:20+01:00",
      "title": "Bertram's Münster Marathon 2013 für Skateistan",
      "description": "Die Idee zu dem Spendenaufruf kam mir, nachdem ich bei Facebook den Spendenaufruf von zwei in Amerika lebenden Afghaninnen gelesen hatte, die ihren Spendenaufruf mit ihrer Teilnahme am LA Marathon verbunden hatten und dabei über 5.000 Dollar zusammenbekommen hatten.<br />Nach Kontakt mit Oliver und Erika von Skateistan habe ich mich dann entschlossen, meine Teilnahme am Münster Marathon 2013 für diesen Spendenaufruf zu nutzen.<br />Im Ergebnis soll die Spende dem Kabul Back-to-School Programm von Skateistan zu Gute kommen. Das Programm verhilft Kindern in Kabul zum Einstieg in die Schule und schließlich zum Besuch einer öffentlichen Schule. Diese Kinder konnten bisher nicht zu einer öffentlichen Schule gehen, weil sie entweder betteln oder Straßenjobs wahrnehmen mussten, um sich und/oder ihrer Familie das Überleben zu sichern,  Die Lehrkraft, die dieses Programm in Kabul umsetzt, indem sie etwa 40 Jungen und Mädchen an 5 Tagen in der Woche unterrichtet, bekommt dafür ein Jahresgehalt von 5.363 Euro. In diesem Betrag ist auch der sichere Transport in Kabul mit den Skateistan Fahrzeugen inbegriffen. Sollten wir es also schaffen, die 5.363 Euro zusammen zu bekommen, haben wir das Programm für ein Jahr gesichert. <br />Gerade in Afghanistan ist Bildung von besonderer Bedeutung, um nachhaltig und langfristig den Aufbau und die Weiterentwicklung voran zu treiben, wobei die Gleichbehandlung von Jungen und Mädchen, die gemeinsamen Aktivitäten unterschiedlicher Bevölkerungsgruppen und Ethnien in einem Projekt ein wesentlicher weiterer Baustein in der Philosophie von Skateistan sind.<br /><br />Ich möchte es hier bei diesem Informationsstand belassen, aber ich werde euch immer über Postings, email etc über den Spendenstand, und meine Vorbereitungen für den Münster Marathon 2013 auf dem Laufenden halten. Das Training werde ich weiter intensivieren müssen, denn ich möchte den Münster Marathon in mindestens 3:30 Std. laufen. Für die Teilnahme spende ich zunächst 50 Euro, sollte ich ihn in 3:30 Std. schaffen wieder 50 Euro und für jede weitere Minute, die ich unter 3:30 reinkomme gibt es nochmals 10 Euro. Im letzten Jahr bin ich bei knapp 30 Grad immerhin schon auf 3:38 gekommen und bin, gerade vor dem Hintergrund meiner diesjährigen bereits laufenden Vorbereitungen ganz zuversichtlich, dass es mit 3:30 klappen dürfte.<br />Es wäre einfach fantastisch, wenn ihr analog zu meiner Staffelung von euch mögliche Beträge spendet. Bei allein 170 facebook Freunden, zig weiteren mail-Kontakten, Linkedin Kontakten etc. müsste es eigentlich möglich sein, die 5.363 Euro zu erreichen. Also macht doch bitte alle im Rahmen eurer Möglichkeiten mit, jeder Euro zählt und jeder Euro spornt mich an, noch mehr zu trainieren und die 3:30 möglichst weit zu unterschreiten. <br />Es ist einfach ein so wunderbares Projekt, zumal wenn man einmal die Straßenkinder selbst tagsüber bei Skateistan und dann abends wieder auf der Straße im Verkehrschaos von Kabul hat betteln sehen, dann frage ich mich, warum ich nicht schon eher auf die Idee gekommen bin, etwas dafür zu tun.<br /><br />WAS IST SKATEISTAN?<br />Die erste Skateboardschule Afghanistans!<br />In Afghanistan machen schulpflichtige Kinder einen größeren Anteil an <br />der Bevölkerung aus als in jedem anderen Land der Welt. 68 Prozent <br />der Afghanen sind 25 Jahre alt oder jünger, fünfzig Prozent sind jünger <br />als 17 Jahre. Viele dieser 15 Millionen afghanischen Kinder und Ju-<br />gendlichen haben keinen Zugang zu Freizeitsportanlagen, viele Schulen <br />verfügen nicht einmal über Spielplätze. Mädchen war es bis vor weni-<br />gen Jahren sogar verboten, in der Öffentlichkeit Sport zu treiben.<br />Skateistan, eine Non-Profit-Organisation in Kabul, will diese Jugendli-<br />chen durch Skateboarding zusammenbringen und ihnen neue Mög-<br />lichkeiten eröffnen. Nur wenige Menschen in Afghanistan hatten zuvor <br />überhaupt jemals ein Skateboard zu Gesicht bekommen; heute hilft <br />Skateboarding dabei, Gemeinschaften aufzubauen, die auf gegensei-<br />tigem Respekt und Verständnis beruhen.<br />Denn beim Skateboarding kommt es auf die eigene Leistung der Ju-<br />gendlichen an; die Sportart passt deshalb gut zu traditionellen afgha-<br />nischen Werten. Skateboarding vermittelt den Jugendlichen was es <br />bedeuten kann, sich selbst immer wieder zu verbessern. Das hilft den <br />Jugendlichen, sich und ihre Gemeinschaften voran zu bringen.<br />Skateistan ist mehr als Skateboarding. Die Organisation spricht nicht <br />nur die besonders benachteiligten Jugendlichen Kabuls an, sondern <br />Jungen und Mädchen aller ethnischen und sozio-kulturellen Hinter-<br />gründe. Durch das gemeinsame Skateboarding lernen sie Respekt <br />über Klassen- und Geschlechtergrenzen hinweg. Zusätzliche Lehr-<br />programme helfen den jungen Männern und Frauen, sich neben dem <br />Skateboard-Unterricht weiter zu bilden.<br /><br />DER SKATEISTAN e.V. IN DEUTSCHLAND<br />Skateistan hilft Kindern und Jugendlichen in Afghanistan, indem es <br />ihnen einen Sport gibt und damit eine Perspektive für die Zukunft. <br />Der Verein Skateistan e.V. unterstützt dieses Projekt. Wir geben <br />Skateistan in Deutschland ein Gesicht. Wir sind regelmäßig auf <br />Sportveranstaltungen und Messen zu treffen oder organisieren selbst <br />Events mit, um Werbung zu machen für die verrückte Idee, die Welt <br />durch Skateboarding ein bisschen zu verbessern. Wenn ihr uns seht, <br />sprecht uns an. Wir verraten euch alles, was ihr wissen wollt. Und <br />schwatzen euch ein T-Shirt auf – alles für die gute Sache.<br />Als Organisation kann der Verein in Deutschland Spenden sammeln <br />und an das Projekt in Afghanistan weiterleiten. Weil sich Sachspen-<br />den nicht einfach mit der Post nach Afghanistan schicken lassen, <br />sammeln wir sie und organisieren den Transport. Für Skateistan hat <br />das den Vorteil, dass Hilfe ankommt und gezielt eingesetzt werden<br />kann. Für Spender bedeutet das, dass ihr Geld auch wirklich den Kin-<br />dern in Afghanistan zugute kommt. Als gemeinnütziger Verein unter-<br />liegen wir der Kontrolle deutscher Behörden, die uns von Amtswegen <br />auf die Finger sehen. Deshalb können Helfer ihre Spenden auch von <br />der Steuer absetzen – schließlich darf sich Hilfe auch lohnen.<br />Skateistan e.V. ist die deutsche Adresse des Projekts. Wir stehen in <br />ständigem Kontakt mit den engagierten Leuten, die in Afghanistan <br />helfen. Wir wissen deshalb immer genau, was dort gerade am meis-<br />ten gebraucht wird und können versuchen, es in Deutschland zu <br />organisieren. Außerdem vermitteln wir Interessierte gerne weiter,<br />egal ob für Interviews oder um einfach nur zu fragen, was die Jungs <br />dort eigentlich so antreibt jeden Tag.",
      "tax_deductible": true,
      "donations_prohibited": false,
      "closed_at": null,
      "donor_count": 13,
      "donated_amount_in_cents": 90700,
      "requested_amount_in_cents": 536300,
      "progress_percentage": 16,
      "contact": {
        "name": "Bertram W.",
        "picture": {
          "fallback": true,
          "links": [
            {
              "rel": "fill_100x100",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/303/864/fill_100x100_original_fazila_movie.jpg"
            },
            {
              "rel": "original",
              "href": "https://asset1.betterplace.org/uploads/user/profile_picture/000/303/864/crop_original_original_fazila_movie.jpg"
            }
          ]
        },
        "links": [
          {
            "rel": "platform",
            "href": "https://www.betterplace.org/de/users/bertram_w"
          },
          {
            "rel": "contact_data",
            "href": "https://api.betterplace.org/de/api_v4/users/303864/contact_data.json"
          }
        ]
      },
      "profile_picture": {
        "fallback": true,
        "links": [
          {
            "rel": "fill_960x500",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/013/904/fill_960x500_profile_thumb_fazila_2.png"
          },
          {
            "rel": "fill_618x322",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/013/904/fill_618x322_profile_thumb_fazila_2.png"
          },
          {
            "rel": "fill_270x141",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/013/904/fill_270x141_profile_thumb_fazila_2.png"
          },
          {
            "rel": "original",
            "href": "https://asset1.betterplace.org/uploads/group/profile_picture/000/013/904/crop_original_profile_thumb_fazila_2.png"
          }
        ]
      },
      "links": [
        {
          "rel": "self",
          "href": "https://api.betterplace.org/de/api_v4/fundraising-events/13904.json"
        },
        {
          "rel": "platform",
          "href": "https://www.betterplace.org/de/fundraising-events/bertrams_muenster_marathon_2013_for_skateistan"
        },
        {
          "rel": "new_client_donation",
          "href": "https://www.betterplace.org/de/fundraising-events/13904/client_donations/new?client_id=%7Bclient_id%7D",
          "templated": true
        },
        {
          "rel": "new_donation",
          "href": "https://www.betterplace.org/de/fundraising-events/13904/donations/new"
        }
      ]
    }
  ]
}
```

