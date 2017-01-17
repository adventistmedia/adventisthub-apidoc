---
title: Adventist Hub API

language_tabs:
  - shell: cURL

toc_footers:
  - Provided by Adventist Media

includes:
  - errors
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

Welcome to the Adventist Hub API! You can use our API to access Kittn API endpoints, which can get information on various cats, kittens, and breeds in our database.

We have language bindings in Shell and Ruby. You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.


# Authentication

> To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>