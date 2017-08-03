---
title: AdHub API

language_tabs:
  - shell: cURL

toc_footers:
  - Provided by Adventist Media

includes:
  - errors
  - endpoints
  - api/account_addresses
  - api/account_notifications
  - api/accounts
  - api/activities
  - api/affiliations
  - api/alerts
  - api/approaches
  - api/attendees
  - api/brands
  - api/calendars
  - api/campaigns
  - api/categories
  - api/contact_addresses
  - api/contact_notifications
  - api/contacts
  - api/event_series
  - api/event_sessions
  - api/events
  - api/teams
  - api/languages
  - api/memberships
  - api/notes
  - api/partners
  - api/religions
  - api/studies

search: true
---

# Introduction

Welcome to the AdHub API documentation. You can use the API to access Team related endpoints. The API doesn't cover endpoints specific to organisations.

To begin, you'll need to contact [Adventist Media](http://adventistmedia.org.au) to request an application key and secret.

# Good to know

AdHub is focused around the idea of a contact - a person who is either a church member or a non-church member.

A contact can be sent an invitation to activate their account allowing them to view all teams they memberships to with a role of team_member, leader or owner. (By default they will have the role "no_role")

Throughout the documentation we will refer to a contact with an activated account as a user.

# Making Requests

## Headers
When writing your own AdHub client, please ensure you set the *Accept* header to `Accept: application/vnd.adhub.v1+json` where v1 represents the API's version number. The latest version is currently v1

If you do not set the Accept header, the API will still work however you may get unexpected data or errors.

All requests other than the signin endpoint require a token in the header `Authorization: Bearer token_goes_here`

## Tokens

There are two types of tokens used to make a request to an endpoint.

A contact tokens is received after sign in and can be used query endpoints related the users account, tokens or app defaults.

For each team the user has membership too, a team token is required to interact with endpoints related to the team.

With this in mind, data received from the API relating to a team (contacts, events, etc) and stored locally should have a team_id column (or similar) to separate the users data by team.

Tokens do not expire but the user can sign in to the Hub via a web browser and remove an applications access therefore deleting the tokens.

## Responses

All requests will return a JSON response using the [JSON API](http://jsonapi.org) specification.

# Authentication


## Sign In
```shell
curl -X POST https://adhubapi.adventistchurch.com/api/account/signin
-H "Accept: application/vnd.adhub.v1+json"
-H "X-Api-Key: adhub_app_key"
-H "X-Api-Secret: adhub_app_secret"
-H "Content-type: application/json"
-d '{"provider_token": "provider_access_token"}'
```
```json
{
  "data": {
    "id": "1",
    "type": "app_tokens",
    "attributes": {
      "contact_id": "5",
      "team_id": null,
      "token": "V4saems7F97MnCf7efDojfgC8qU6JsGTKfEgZz6RFf555dsQFM"
    }
  }
}
```
`https://adhubapi.adventistchurch.com/api/account/signin`

Before authenticating with AdHub, you'll first need to authenticate the user through myAdventist using OAuth 2.
After authenticating the user through myAdventist, you will receive a myAdventist access token that can be exchanged for a AdHub API contact token for future requests.

<aside class="notice">
For more information on myAdventist, please consult the South Pacific Division of the Seventh-day Adventist Churches Information Services department.
</aside>

To get the AdHub API contact token, send a POST request to `https://adhubapi.adventistchurch.com/api/account/signin`.
The request must include the headers `X-Api-Key` and `X-Api-Secret` where the API key and secret will be provided by Adventist Media.

The following fields are required:

### Fields

Field | Description | Notes
----- | ----------- | -----
provider_token<br> *datetime* | The OAuth access token you received from myAdventist after successfully logging the user in | Required



## Sign out
```shell
curl -x DELETE https://adhubapi.adventistchurch.com/api/account/signout
-H "Authorization: Bearer contact_token"
-H "Accept: application/vnd.adhub.v1+json"
```
```json
{
  "success": true
}
```
`https://adhubapi.adventistchurch.com/api/account/signout`

To sign out from AdHub send a DELETE request. This will delete all of the users tokens associated with the app. This has the effect that if the user was to have signed in on multiple devices, all devices would be signed out.

## Team Tokens
```shell
curl https://adhubapi.adventistchurch.com/api/account/team_tokens
-H "Authorization: Bearer contact_token"
-H "Accept: application/vnd.adhub.v1+json"
```
```json
{
  "data": [
      {
          "id": "2",
          "type": "app_tokens",
          "attributes": {
            "contact_id": "5",
            "team_id": "2",
            "token": "KEE3Pwi9GfBopSeisFC9gdrNHdWRgG5pwY4Dfqjve2sjhT8YCC"
          }
      },
      {
          "id": "3",
          "type": "app_tokens",
          "attributes": {
            "contact_id": "5",
            "team_id": "3",
            "token": "NBYBeUG6PLAWaZs9WV5HgcreQpWYoTs4U899zs3z4ExsjSUrD9"
          }
      }
    ]
}
```
`https://adhubapi.adventistchurch.com/api/account/team_tokens`

As a user can belong to multiple teams so your app should allow the user to switch between teams.
Sending a request to team tokens will give you tokens for all active teams the contact has membership too with a role.


# Account Activation

The API allows you to activate a users account.

Before trying to activate the account you will need the users invite token. You should first verify the invite token is valid with the `invite_token_introspect` endpoint. Once the invite token is verified you can then have the have the user sign in or create a myAdventist account (this process happens outside of the AdHub API) to retrieve a myAdventist token that can be used to activate the users AdHub Account.

## Invite Token Introspect

```shell
curl https://adhubapi.adventistchurch.com/api/account/invite_token_introspect
-H "Accept: application/vnd.adhub.v1+json"
-H "X-Api-Key: adhub_app_key"
-H "X-Api-Secret: adhub_app_secret"
-H "Content-type: application/json"
-d '{"invite_token": "vf6MdJefq7q4eT5fWSuTjmie"}'
```
```json
{
    "data": {
        "id": "48",
        "type": "contacts",
        "attributes": {
            "contact_id": "48",
            "first_name": "Sally",
            "last_name": "Bix",
            "email": "sallybix@email.com",
            "invite_token": "vf6MdJefq7q4eT5fWSuTjmie",
            "invite_token_expires_at": "2017-09-02T23:59:59.999+10:00",
            "invited_by": "James Randell",
            "team": "Wahroonga"
        }
    }
}
```
`https://adhubapi.adventistchurch.com/api/account/invite_token_introspect`

Verify an invite token for a pending user account is still valid. Invite tokens expire 30 days after they were created.

## Activate

```shell
curl -X POST https://adhubapi.adventistchurch.com/api/account/activate
-H "Accept: application/vnd.adhub.v1+json"
-H "X-Api-Key: adhub_app_key"
-H "X-Api-Secret: adhub_app_secret"
-H "Content-type: application/json"
-d '{"invite_token": "vf6MdJefq7q4eT5fWSuTjmie", "provider_token": "provider_access_token"}'
```
```json
{
  "data": {
    "id": "1",
    "type": "app_tokens",
    "attributes": {
      "contact_id": "48",
      "team_id": null,
      "token": "D1saemZz6RFf555dsQFMs7F97MnCf7efDojfgC8qU6JsGTKfEg"
    }
  }
}
```
`https://adhubapi.adventistchurch.com/api/account/activate`

Providing a valid invite token and provider token will successfully activate a pending users account. The user will then be automatically signed in and the JSON response is the same as if you had called `/api/account/signin`