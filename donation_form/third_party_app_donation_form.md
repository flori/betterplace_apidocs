# ThirdPartyApp custom donation form for organisations (BETA)


*BETA: This is the first draft of this documentation. Please send us feedback at product@betterplace.org. Or via pull request. Thanks!*


## Introduction

The ThirdPartyApp custom donation form for organisations is a special donation form that can be used in agreement with betterplace. It allows a deeper integration of the donation form in existing webapplication of the organisation.

It is meant for those organisation that want to develop and maintain a custom donation experience for their donors.

Please note that his part this page has nothing to do with the json-API v4 that is described in this repository. It is documented here since both feature are often used at the same time.


**Exampels:**

* [Ablass App](http://www.ablass-app.de/), where you can clean your conscious
* [Donatify me](http://donatify.me/), where you can get Edward to do stuff for you
* _Please send your app URL to product@betterplace.org_


**About the two regular donation forms on betterplace.org:**

betterplace.org provides a number of different donation forms for organisations and projects. The two most important once being the project donation form that donors use when browsing on betterplace.org and the external donation form (iframe) that projects can embed in their organisations' website.
You can read more about those form in the help section on betterplace.org ([DE](http://www.betterplace.org/c/hilfe/themen/spendensammler/geldspenden/), [EN](http://www.betterplace.org/c/help/topics/collectdonations/)).



## How the ThirdPartyApp custom donation form is different:

<table>
  <tr>
    <th></th>
    <th>Project donation form</th>
    <th>External donation form</th>
    <th>ThirdPartyApp donation form</th>
  </tr>
  <tr>
    <th>Userflow</th>
    <td>betterplace.org project page → donation form → postdonation pages → project opinions page</td>
    <td>organisation or project webpage → donation section with iframe → same page with postdonation page</td>
    <td>organisation or project webapplication → some user interaction → link to ThirdPartyApp donation form → postdonation page inside the projects' webappliction</td>
  </tr>
  <tr>
    <th>Customization</th>
    <td>Project name</td>
    <td>Project name, Color, Default Amount, Size</td>
    <td>Project name, Input parameter, Postdonation URL, But no styling</td>
  </tr>
  <tr>
    <th>URL path</th>
    <td>/projects/ID/donations/new</td>
    <td>/projecst/ID/iframe_donations/new</td>
    <td>/projects/ID/client_donations/new?client_id=ThirdPartyApp</td>
  </tr>
</table>


## How to get it

Other than with the external donation form the ThirdPartyApp donation form needs to be set up by betterplace.org.
Please make sure that you can agree to the terms of use below and send us an email with the following information.

We will check your proposal and get back to you.

This is a special service in testing and in beta – so no promises!

**E-Mail:** (all data is required)

```
* My project URL on betterplace:
* Description of the webapplication that I plan to build:
* This is the URL that users should be redirected to after a successfull donation (the "callback URL"):
* This email-address should be used for updates and new:
```

Mailto:product@betterplace.org


## Terms of use

This is a special service in testing. Nothing is final or fixed. And it's beta. So don't say we didn't warn you!

* There is no support from the betterplace.org team for this feature other than this documentation
* All terms of use and privacy policy of betterplace.org apply
* We will inform you about changes 7 days ahead via the email-contact that you provide
* Should we consider discontinuing this service we will inform you 3 month ahead
* The code that you write to integrate this donation form in your flow has to be open sourced under Apache License 2.0 for everyonce benefit



## How to use it

After everything is set up by betterplace.org (see above), you just need to construct the donation form URL and make sure your callback URL can handle the response.


### Donation form URL and input parameter

*Example:*
<pre>
https://www.betterplace.org/de/projects/480/client_donations/new?client_id=ablass&donation_presenter%5Bdonation_amount%5D=15&donation_presenter%5Bdonation_client_reference%5D=wZo2aZCjJHA2CONAXxIQHt
</pre>

<table>
  <tr>
    <td>
      <code>https://www.betterplace.org/</code>
    </td>
    <td>
      Lets start with the domain
    </td>
  </tr>
  <tr>
    <td>
      <code>en/</code>,
      <code>de/</code>
    </td>
    <td>
      The language for the form
    </td>
  </tr>
  <tr>
    <td>
      <code>projects/1114/</code>,
      <code>fundraising-events/seeds-of-kindness-3/</code>
    </td>
    <td>
      The receiver type and id of the donation.
    </td>
  </tr>
  <tr>
    <td>
      <code>client_donations/new?client_id=YOUR_APP_ID</code>
    </td>
    <td>
      The path to the donation form. <code>YOUR_APP_ID</code> will be provided by betterplace.org (see 'How to get it').
    </td>
  </tr>
  <tr>
    <td>
      <code>&donation_presenter[donation_amount]=6</code>
    </td>
    <td>
      OPTIONAL: You can pre-set the donation amount in euro
    </td>
  </tr>
  <tr>
    <td>
      PLANNED: <code>&donation_amount_readonly=true</code>
    </td>
    <td>
      OPTIONAL: You can specify if the input field for the donation amount (the default or your pre-set amount) should be readonly. This ways users cannot change the amount (easily). –– This feature is not yet implemented!
    </td>
  </tr>
  <tr>
    <td>
      <code>&donation_presenter[donation_client_reference]=123</code>
    </td>
    <td>
      OPTIONAL – But this is basically why you would want to use the ThirdPartyApp donation form in the first place. It allows you to give each donation/donor a unique ID in your application. We will send this ID back to you via the callback url. This way you can track which donation went through.
    </td>
  </tr>
</table>



### Redirect URL and response parameter

This URL is part of the configuration that needs to be done by betterplace.org (see 'How to get it'). We will redirect the donor to this URL after a successfull donation. We will also extend the URL with the following reponse parameter.

*Cool urls dont change:* We cannot change this URL after we created you ThirPartyApp ID. Please consider redirecting inside your application.

*Example:*
<pre>
https://www.you-app.cool/callback.php?status=DONATION_COMPLETE&donation_client_reference=wZo2aZCjJHA2CONAXxIQHt
</pre>

<table>
  <tr>
    <td>
      <code>https://www.you-app.cool/callback.php</code>
    </td>
    <td>
      The callback URL you provide
    </td>
  </tr>
  <tr>
    <td>
      <code>status=DONATION_COMPLETE</code>
    </td>
    <td>
      The status which tells you all is good. Its a bit redundant since there is only this one status ;-)
    </td>
  </tr>
  <tr>
    <td>
      <code>donation_client_reference=123123</code>
    </td>
    <td>
      The same value that you provided when opening the donation form via <code>donation_presenter[donation_client_reference]</code>
    </td>
  </tr>
  <tr>
    <td>
      <code>receiver_type=project&receiver_id=1114</code>,
      <code>receiver_type=group&receiver_id=seeds-of-kindness-3</code>
    </td>
    <td>
      The receiver type and id that you specified when opening the form. "Group" stands for "Fundraising Event".
    </td>
  </tr>
  <tr>
    <td>
      <code>amount=6</code>
    </td>
    <td>
      The amount that was actually donated. This corresponts to <code>donation_presenter[donation_amount]</code> unless the user changed it.
    </td>
  </tr>
  <tr>
    <td>
      <code>donation_token=STRING</code>
    </td>
    <td>
      A unique token that identifies this donation. You have to store this token in your application to reconcile the donation later – see chapter below.
    </td>
  </tr>
</table>



### Reconciliation

Once you receive the DONATION_SUCCESS message via the redirect URL you can be sure that the donation arrived in our betterplace.org database. BUT: There are a few ways that this donation might be canceled again later (by the bank or the user most likely).

That is why we have an API endpoint [client_donation_details](../sections/client_donation_details.md) that allows you to check the status foreach donation. For that you need the **donation token** that is part of the response params to the redirect URL.

Only donations that are marked as 'confirmed' are really confirmed for good.

Usually the state of a donation will only change during the first 14 days. In some cases however the bookback might take place later. Therefore the trigger to check the donations should probably not be time-based but based on the `open_amount_in_cents` from the [projects-json api response](../sections/project_details.md). Whenever this number changes whithout you getting new donations, you need to check the reconciliation of all donation.



## Clients of betterplace.org / Whitelabeling

The core for this ThirdPartyApp donation form is the technology that runs our client donation forms. The main difference being, that client donation forms are always whitelabeled to fit the design of the client application. Please get in touch for more information.



## Feedback

Please send us feedback at product@betterplace.org

