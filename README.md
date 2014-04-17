![betterplace.org](images/betterplace.jpg "betterplace.org")

# The betterplace.org API Version 4

This is the latest API for betterplace.org. It's a REST-style API that returns
JSON for serialization.
It incorporates some ideas from [hypermedia apis](https://www.google.de/search?q=hypermedia+api)
like the link-strukture.

**Please provide feedback:** Please don't hesitate to provide any feedback about the API and this documentation
at developers@betterplace.org.

**Mailing list for service announcements:** Please send an email to tjo@betterplace.org
to subscribe to the api-v4-mailing list to receive service announcements about updates
and scheduled downtimes.


## Table of content

### Public API

* General information [↓ below](#general-information)
* HTTP Result Codes and Error Messages [↓ below](#http-result-codes-and-error-messages)
* Changelog [↓ below](#changelog)
* Known issues [↓ below](#known-issues)
* Code examples [↓ below](#code-examples)
* Example apps [↓ below](#example-apps)
* [**Projects** List and Search](sections/projects_list.md)
* [**Project** Details](sections/project_details.md)
* [Project **Needs** List](sections/needs_list.md)
* [Project **Need** Details](sections/need_details.md)
* [Project **Blog Posts** List](sections/blog_posts_list.md)
* [Project **Blog Post** Details](sections/blog_post_details.md)
* [Project **Opinions** List](sections/opinions_list.md)
* [Project **Opinion** Details](sections/opinion_details.md)
* [Project **Pictures** List](sections/project_pictures_list.md)
* [Project **Picture** Details](sections/project_picture_details.md)
* [**Volunteering** List and Search](sections/volunteering_list.md)
* [**Volunteering** Details](sections/volunteering_details.md)
* [**Organisations** List](sections/organisations_list.md)
* [**Organisation** Details](sections/organisation_details.md)
* [**MatchingFunds** List](sections/matching_funds_list.md)
* [**MatchingFund** Details](sections/matching_fund_details.md)
* [**MatchingFund** Projects List](sections/matching_fund_projects_list.md)
* TODO [**User** Details](sections/user_details.md)
* TODO [**Fundraising Events** List and Search](sections/fundraising_events_list.md)
* TODO [**Fundraising Event** Details](sections/fundraising_event_details.md)


### Organisations

* [ThirdPartyApp custom donation form for organisations](donation_form/third_party_app_donation_form.md)


### Client API

This part of the API can only be used in agreement with betterplace.org.
Please [contact someone at betterplace solutions](http://www.betterplace-solutions.de/#buergerzeitung)
for more information.

* [**Client** Details/Statistics](sections/client_details.md)
* [**Client** Donations List](sections/client_donations_list.md)
* [**Client** Projects List and Search](sections/projects_list.md) – See client section and ⁂1
* [**Client** Project Details](sections/project_details.md) – See client section and ⁂1
* [**Client** Blog Posts List](sections/blog_posts_list.md) – See client section
* [**Client** Project Opinions List](sections/opinions_list.md) – See client section
* [**Client** Project-Tags List](sections/client_project_tags_list.md) – See client section
* [**Client** Project-Tag Projects List](sections/client_project_tag_projects_list.md) – See client section
* [**Client** Contact Data Details](sections/contact_data_details.md) – See client section

*(⁂1) Client projects:* Clients projects are projects on betterplace.org that are
associated with a client-user. This way clients can control what projects
are visible on their plattform.

*Request-URLs:* Clients have to prepend some requests with their client-id.
For projects that would be `/clients/PERMALINK/projects.json` and `/clients/PERMALINK/projects/ID.json`.
More information can be found in the description of each request.

*Error Code:* If you request data for a project that is not part of the client
projects, the API will return a `404` HTTP code.

*Usage example:* The local german newspaper "Trierischer Volksfreund"
has it's own donation portal at ["Meine Hilfe zählt"](http://www.meine-hilfe-zaehlt.de/).
All data are pulled from this api. In addition they use the betterplac.rog whitelabel donation form, which
is another service betterplace.org provides for clients.


### Client Authentication

In order to use some special features of the betterplace API, you need to authenticate yourself with an API-Token. These tokens are provided by betterplace, please
[contact betterplace solutions](http://www.betterplace-solutions.de/#buergerzeitung) if you are interested.

To authenticate with a token you'll need to pass it as an additional http header `Api-Token` or with an additional http parameter `api_token`.

* [Contact Data Details](sections/contact_data_details.md)


## General information

* The API is https only, all non-https requests will be redirected accordingly
* The response format is json, the request format extention .json
* The response language is defined by the URL-language-prefix (/en/, /de/ (default))
* We support [Cross-origin resource sharing (CORS)](http://en.wikipedia.org/wiki/Cross-origin_resource_sharing), so no proxy or JSONP is required
* No Authentication: All api calls are public at the moment but there will be
  feature that require authentication in the future.

### Request parameter format

The `order` and `facets` request parameters accept multiple key-value-parameter.
We use the same convention as the [Google Static Maps API V2](https://developers.google.com/maps/documentation/staticmaps/#URL_Parameters).

Example: `foo:bar|lorem:ipsum`

This way you may specify a primary and secondaray sort order: `order=rank:ASC|created_at:DESC`

* Split key and value by a colon `:`
* Split multiple key-value-parameter by a pipe `|` (`%7C`)
* [URL encode](http://de.wikipedia.org/wiki/URL-Encoding) all params, so the Pipe becomes `%7C`
* Note that for readability-reasons we don't URL encode the params in this documentation


### List parameters and attributes

The following request parameters can be set for all list views.

<table>
  <tr>
    <th>Parameter</th>
    <th>Description</th>
    <th>Default</th>
  </tr>
  <tr>
    <td><code>page</code></td>
    <td>Used to paginate through the list</td>
    <td>1</td>
  </tr>
  <tr>
    <td><code>per_page</code></td>
    <td>The number of entries per page</td>
    <td>20</td>
  </tr>
</table>

The following attributes are returned in all list view responses:

<table>
  <tr>
    <th>Attribute</th>
    <th>Description</th>
    <th>Example</th>
  </tr>
  <tr>
    <td><code>total_entries</code></td>
    <td>Count of all entries</td>
    <td>23</td>
  </tr>
  <tr>
    <td><code>offset</code></td>
    <td>The number of entries that are skipped before the current listing begins, <code>= max(page - 1, 0) * per_page</code></td>
    <td>0</td>
  </tr>
  <tr>
    <td><code>total_pages</code></td>
    <td>Count of all pages, based on <code>per_page</code></td>
    <td>42</td>
  </tr>
  <tr>
    <td><code>current_page</code></td>
    <td>What page we are on</td>
    <td>1</td>
  </tr>
  <tr>
    <td><code>per_page</code></td>
    <td>Number of entries per page</td>
    <td>20</td>
  </tr>
</table>


## HTTP Result Codes and Error Messages

### Error Messages

If an error occurs, a JSON response messages is returned with a `name` and `reason` (optional).
Clients that use the betterplace.org-staging-environment will also see a `backtrace` and `message`.

Example:

```json
{
  "name": "ActiveRecord::RecordNotFound",
  "reason": "Record Not Found",
  "backtrace": [
    "/path/to/file:23:in `method'",
    "/path/to/file:42:in `method2'"
  ],
  "message": "Couldn't find Project with id=666"
}
```

### HTTP Result Codes

The following HTTP result codes can be returned:

* HTTP Code `200` if all is good and `304` if this good thing has not been modified (based on ETag).

* HTTP Code `404` is returned if a requested resource could not be found.

* HTTP Code `400` is returned if a requested resource could not be created or updated,
  if the submitted data was invalid.

* HTTP Code `500` is returned if a software error on the server was encountered.

* HTTP Code `403` is returned if a resource requires [client authentication](#client-authentication) but no client was authenticated.


## Changelog
* 2014-03-04: Remove all deprecated picture links from responses.
* 2014-01-26: Remove the beta-flag; add matching-fund api; add code and usage examples; minor improvements
* 2013-06-20: Add client.pool_balance_in_cents property, see doc for details
* 2013-06-14: Add platform-link to blog_posts-details
* 2013-05-15: Opinions have a link to the project now. All API-link are "api.betterplace.org" now (not www. anymore). Opinions have have a facets=has_message-Feature now.
* 2013-04-19: Change the naming of api-docu-files to follow rails-pluralization-convention.
* 2013-04-19: Added 'client project-tag list' (a list of all project-tags for a client) and 'client project-tag projects list' (a list of all projects for a client-project-tag).
* 2013-04-18: Fixed project opinions. Add client opinions-feature. Note that many of the opinions-facets changed! Please re-read this part of the documentation.
* 2013-04-17: Add project pictures API. Please note the DEPRICATION warning for the project- and volunteering-profilepicture (sizes large, profile and thumb are deprecated and therefore renamed.)
* 2012-04-15: Add "Client Project-Tag Project List".
* 2012-03-03: Add picture size 'large' and 'original' to image list for projects. Please note that the images-part of the API ist still beta and might change slightly in the future.
* 2012-03-28: The project-list now returns the full result-set for each project. The minimal result set is gone for now but will be added later. The default-number of results changed to 20 for all lists.
* 2012-05~15: Add known issues, improve documentation, remove opinion.with_donation, add opinion.donated_amount_in_cents, project.description returns html now
* 2012-03-13: Update TOC, fix opinions-details and -list response, fix empty documentation (@tordans)
* 2012-03-12: Several updates to readme, updates to descriptions for clients, updated opinions-docu, added know-issues and changelog sections (@tordans)
* 2012-03-11: Initial version (@betterplace)


## Known issues

Please contact developers@betterplace.org for more information

1. Documentation: Not all resources have a documentation-url as part of the json
1. Documentation: The response-table does not show the root-documentation for response-elements with sub-elements (for example carrier.name is documented but carrier is not)
1. Blogposts: There is no way yet to filter BlogPosts from PayoutBlogPost


## Code examples

* Using the API with PHP: https://gist.github.com/svjv1160/7749784
* _Please send us your code examples to developers@betterplace.org_


## Example apps

* The "Deutsch Tansanianische Partnerschaft" uses this API to present their betterplace.org projects right on their website: [Project list](http://www.dtpev.de/unterstuetzen/projekte), [Project details](http://www.dtpev.de/unterstuetzen/projekte/one-child-one-light)
* _Please send us your sites to developers@betterplace.org_


## API V1, V2, V3

betterplace.org has three deprecated APIs. For more information contact product@betterplace.org.


## About betterplace.org

Learn more about betterplace at http://www.betterplace.org/de/how_it_works

## License of this documentation

See the [license file](LICENSE).
