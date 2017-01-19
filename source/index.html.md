---
title: Adventist Hub API

language_tabs:
  - shell: cURL

toc_footers:
  - Provided by Adventist Media

includes:
  - errors
  - endpoints
  - api/account_addresses
  - api/account_notifications
  - api/account_phone_numbers
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
  - api/contact_phone_numbers
  - api/contacts
  - api/event_series
  - api/event_sessions
  - api/events
  - api/hub_teams
  - api/languages
  - api/partners
  - api/religions
  - api/studies
  - api/tasks

search: true
---

# Introduction

Welcome to the Adventist Hub API documentation. You can use the API to access Hub Team related endpoints. The API doesn't cover endpoints specific to Hub team managers, mentors, or HQ teams.

To begin, you'll need to contact [Adventist Media](http://adventistmedia.org.au) to request an application key and secret.

# Making Requests

## Headers
When writing your own Adventist Hub client, please ensure you set the *Accept* header to `Accept: application/vnd.adventisthub.v1+json` where v1 represents the API's version number. The latest version is currently v1

If you do not set the Accept header, the API will still work however you may get unexpected data or errors.

All requests other than the signin endpoint require a token in the header `Authorization: Bearer token_goes_here`

## Tokens

An Adventist Hub API token is unique to a particular team. This means if a user has membership to multiple Hub teams, you will need a token for each team.

You can use a token for one team to request a token for another team.

With this in mind, data received from the API for the user and stored locally should have a team_id column (or similar) to separate the users data by team.

Tokens do not expire but the user can sign in to the Hub via a web browser and remove an applications access therefore delete the tokens.

## Responses

All requests will return a JSON response using the [JSON API](http://jsonapi.org) specification.

# Authentication


## Sign In
```shell
curl -X POST https://hubapi.adventistchurch.com/api/signin
-H "Accept: application/vnd.adventisthub.v1+json"
-H "X-Api-Key: adventisthub_app_key"
-H "X-Api-Secret: adventisthub_app_secret"
-H "Content-type: application/json"
-d '{"provider": "myadventist", "provider_token": "provider_access_token", "provider_uid": "provider_uid"}'
```
```json
{
  "data": {
    "id": "1",
    "type": "app_tokens",
    "attributes": {
      "user_id": 5,
      "team_id": 2,
      "token": "V4saems7F97MnCf7efDojfgC8qU6JsGTKfEgZz6RFf555dsQFM"
    }
  }
}
```
`https://hubapi.adventistchurch.com/api/signin`

Before authenticating with Adventist Hub, you'll first need to authenticate the user through myAdventist using OAuth 2.
After authenticating the user through myAdventist, you will receive an access token that can be exchanged for a Adventist Hub API token for all future requests.

<aside class="notice">
For more information on myAdventist, please consult the South Pacific Division of the Seventh-day Adventist Churches Information Services department.
</aside>

To get the Adventist Hub API token, send a POST request to `https://hubapi.adventistchurch.com/api/signin`.
The request must include the headers `X-Api-Key` and `X-Api-Secret` where the API key and secret will be provided by Adventist Media.

Remember, when an Adventist Hub token is requested, the token will be unique to the users team. During signin the token will be for the users first team.

The following fields are required:

### Fields

Field | Description | Notes
----- | ----------- | -----
provider<br> *string* | The name of the provider. Should be myadventist | Required
provider_token<br> *datetime* | The OAuth access token you received from myAdventist after successfully logging the user in | Required
provider_uid<br> *datetime* | Providers unique user ID | Required



## Sign out
```shell
curl -x DELETE https://hubapi.adventistchurch.com/api/signout
-H "Authorization: Bearer token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "success": true
}
```
`https://hubapi.adventistchurch.com/api/signout`

To sign out from Adventist Hub send a DELETE request. This will delete all of the users tokens associated with the app. This has the effect that if the user was to have signed in on multiple devices, all devices would be signed out.

## Switching Teams
```shell
curl -x POST https://hubapi.adventistchurch.com/api/team_token/7
-H "Authorization: Bearer token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "data": {
    "id": "53",
    "type": "app_tokens",
    "attributes": {
      "user_id": 5,
      "team_id": 7,
      "token": "ojfgC8qU65dsQFMV4saems7F97MnCf7efDJsGTKfEgZz6RFf55"
    }
  }
}
```
`https://hubapi.adventistchurch.com/api/team_token/{team-id}`

As a user can have multiple teams, your app should allow the user to switch between teams.
To switch teams, you'll need to request a token for the team to be switched too.

To get a list of all teams available to a user, use the Hub Teams endpoint.
