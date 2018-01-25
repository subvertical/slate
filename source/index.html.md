---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby

toc_footers:
  - <a href='https://app.verticalchange.com/signup'>Sign Up for an Account</a>
  # - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the VerticalChange API! You can use our API to access various API endpoints, to interact with your data.

<!-- Base URL: [https://api.verticalchange.com](https://api.verticalchange.com) -->

# Authentication

VerticalChange uses API authentication tokens to allow access to the API. You can retrieve an authentication token by calling the `/sessions` API endpoint.

VerticalChange API server expects the API authentication token to be included in all API requests to the server in a header that looks like the following:

`Authorization: API_AUTH_TOKEN`

<aside class="notice">
You must replace <code>API_AUTH_TOKEN</code> with your personal API authentication token.
</aside>

## Get Authentication Token

```ruby
require 'rest-client'

user = { email: 'email@example.com', password: 'password' }
headers = { Accept: 'application/vnd.verticalchange.v1' }

RestClient.post 'https://api.verticalchange.com/sessions', user, headers
```

```shell
curl --request POST \
  --url https://api.verticalchange.com/sessions \
  --header 'Accept: application/vnd.verticalchange.v1' \
  --form email=email@example.com \
  --form password=password
```

> The above command returns JSON structured like this:

```json
{
    "auth_token": "227c9de96736..."
}
```

This endpoint retrieves the authentication token.

### HTTP Request

`POST https://api.verticalchange.com/sessions`

### Parameters

Parameter | Description
--------- | -----------
email | Your email address
password | Your password

## Delete Authentication Token

```ruby
require 'rest-client'

headers = { Accept: 'application/vnd.verticalchange.v1' }

RestClient.delete 'https://api.verticalchange.com/sessions/API_AUTH_TOKEN', headers
```

```shell
curl --request DELETE \
  --url https://api.verticalchange.com/sessions/<API_AUTH_TOKEN> \
  --header 'Accept: application/vnd.verticalchange.v1' \
```

> The above command returns no content.

This endpoint deletes the authentication token.

### HTTP Request

`DELETE https://api.verticalchange.com/sessions/<API_AUTH_TOKEN>`

### URL Parameters

Parameter | Description
--------- | -----------
API_AUTH_TOKEN | The authentication token.

# Reports

## Get All Reports

```ruby
require 'rest-client'

headers = {
  Authorization: 'API_AUTH_TOKEN',
  Accept: 'application/vnd.verticalchange.v1'
}

RestClient.get 'https://api.verticalchange.com/reports', headers
```

```shell
curl --url https://api.verticalchange.com/reports \
  --header 'Accept: application/vnd.verticalchange.v1' \
  --header 'Authorization: API_AUTH_TOKEN'
```

> The above command returns JSON structured like this:

```json
[
  {...}
]
```

This endpoint retrieves all reports.

### HTTP Request

`GET https://api.verticalchange.com/reports`

<aside class="success">
Remember — authentication is required.
</aside>

## Get a Specific Report

```ruby
require 'rest-client'

headers = {
  Authorization: 'API_AUTH_TOKEN',
  Accept: 'application/vnd.verticalchange.v1'
}

RestClient.get 'https://api.verticalchange.com/reports', { id: 55 }, headers
```

```shell
curl --url https://api.verticalchange.com/reports/55 \
  --header 'Accept: application/vnd.verticalchange.v1' \
  --header 'Authorization: API_AUTH_TOKEN'
```

> The above command returns JSON structured like this:

```json
{
  "id": 55,
  ...
}
```

This endpoint retrieves a specific report.

<!-- <aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside> -->

### HTTP Request

`GET https://api.verticalchange.com/reports/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the report to retrieve

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
name | Report | Report name
report_fields | All fields | All Report fields.
require_form_result | true | Require form result
contact_type | Person | Person, Group, and ProgramContact.
include_participants | false | Include participants in the response
worksheet | details | [TBD]

# Headers

VerticalChange API requires two headers—for versioning and authorization purposes—to be presents in all API calls.

### Required Headers

Parameter | Value | Purpose
--------- | ----------- | -----------
Accept | `application/vnd.verticalchange.v1` | To set the versioning.
Authorization | `API_AUTH_TOKEN` | To authenticate API calls.

<aside class="notice">
You must replace <code>API_AUTH_TOKEN</code> with your personal API authentication token.
</aside>
