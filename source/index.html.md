---
title: Cultivate Forecasts API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

includes:
- pagination
- badges
- clarifications
- comments
- earned_badges
- memberships
- prediction_sets
- questions
- scores
- stars
- surveys
- users
- votes

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Kittn API
---


# Authentication

> Request:

```shell
curl "https://yoursite.cultivateforecasts.com/oauth/token" \
  -X POST \
  -d grant_type=password \
  -d email=user@example.com \
  -d password=password
```

> Response:

```json
{
  "access_token": "b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75",
  "token_type": "bearer",
  "expires_in": 7200,
  "created_at": 1438910165
}
```

To access the Cultivate Forecasts API, you need an oauth token. You can generate one by making a POST request to `/oauth/token` with email, password, and grant_type parameters.

### HTTP Request

`POST https://yoursite.cultivateforecasts.com/oauth/token`

### Query Parameters

Parameter | Value
--------- | -----------
grant_type | password
email | Your email address
password | Your password


For subsequent requests, you must include your token as part of an authorization header.
