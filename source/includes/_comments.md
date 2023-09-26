
# Comments

## Comments List

Shows a list of comments that exist on the site.

> Request:

```shell
curl "https://yoursite.cultivateforecasts.com/api/v1/comments" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75"
```

> Response:

```json
{
    "comments": [
        {
            "id": 439,
            "commenter_type": "Ident::Membership",
            "content": "anonymous comment",
            "commentable_id": 563,
            "commentable_type": "Forecast::Question",
            "children_count": 0,
            "parent_id": null,
            "created_at": "2020-11-13T16:29:58.124Z",
            "updated_at": "2020-11-13T16:29:58.124Z",
            "anonymous": true,
            "commentable_name": "question-name-8"
        },
        {
            "id": 436,
            "commenter_type": "Ident::Membership",
            "content": "comment 2",
            "commentable_id": 563,
            "commentable_type": "Forecast::Question",
            "children_count": 0,
            "parent_id": null,
            "created_at": "2020-11-13T16:29:58.051Z",
            "updated_at": "2020-11-13T16:29:58.051Z",
            "anonymous": false,
            "membership_username": "TheTank17",
            "membership_avatar_url": "http://test-1.lvh.me/assets/default_theme/v18/ident/default_avatars/level-1-1-2585542198c786697ecae8838813bd0a558e8b40bee4f21676d05e014d3ccc52.png",
            "commenter_id": 1207,
            "commentable_name": "question-name-8"
        },
        {
            "id": 435,
            "commenter_type": "Ident::Membership",
            "content": "comment 1",
            "commentable_id": 563,
            "commentable_type": "Forecast::Question",
            "children_count": 1,
            "parent_id": null,
            "created_at": "2020-11-13T16:29:58.030Z",
            "updated_at": "2020-11-13T16:29:58.030Z",
            "anonymous": false,
            "membership_username": "TheTank16",
            "membership_avatar_url": "http://test-1.lvh.me/assets/default_theme/v18/ident/default_avatars/level-1-1-2585542198c786697ecae8838813bd0a558e8b40bee4f21676d05e014d3ccc52.png",
            "commenter_id": 1206,
            "commentable_name": "question-name-8"
        }
    ]
}
```

### HTTP Request

`GET https://yoursite.cultivateforecasts.com/api/v1/comments`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
page | 0 | Pagination page number
created_before | none | Returns only history records created before the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
created_after | none | Returns only history records created after the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
updated_before | none | Returns only history records updated before the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
updated_after | none | Returns only history records updated after the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
include_replies | false | Whether to include comment replies
commentable_id | none | The ID of the resource to scope the list of comments to. E.g. a question ID, if you want only comments from that question
commentable_type | none | If commentable_id is provided, this must be provided. Valid options: `Forecast::Question`, `Ident::Site`, and `Cms::Post`


### Attribute Descriptions

Parameter | Type | Description
--------- | ------- | -----------
id | integer | The id of the comment
commenter_type | string | The type of resource that created the comment
content | string | The comment text
commentable_id | integer | The ID of the resource where this comment was made (e.g. a question or a blog post) 
commentable_type | string | The type of resource where this comment was made (e.g. a question or a blog post) 
commentable_name | string | The name of the resource where this comment was made (e.g. the question's text or blog post's title)
children_count | integer | The number of replies that have been made to this comment
parent_id | integer | If this was a reply, the ID of the comment it was replying to
created_at | datetime | The creation timestamp
updated_at | datetime | The timestamp of when this comment was last updated
anonymous | boolean | Whether this comment was made anonymously
membership_username | string | The username of the user who created the comment
membership_avatar_url | string | The URL of the user's avatar image
commenter_id | integer | The ID of the membership/user who made the comment





## Comment Creation

Creates a comment. The comment will be attributed to the owner of the oauth token that you're using to submit the request. To reply to another comment, you should include a `parent_id` parameter containing the ID of the comment to which you're replying.

> Request:

```shell
curl -X "POST" "https://yoursite.cultivateforecasts.com/api/v1/comments" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75" \
  -H "Content-Type: application/json" \
  -H "Accept: application/json" \
	-d "{\"parent_id\": 123, \"commentable_id\":959,\"commentable_type\":\"Forecast::Question\",\"comment\":{\"content\":\"And now his watch has ended.\"}}"
```

> Request body example:

```json
{
  "commentable_id": 959,
  "commentable_type": "Forecast::Question",
  "comment": {
    "content": "And now his watch has ended."
  }
}
```


> Response:

If the comment is not a reply, the response contains the newly created comment.

If the comment is a reply (ie. a `parent_id` was given), the response contains the parent comment and its children.

```json
// When creating a non-reply comment:
{
  "id": 1177,
  "commentable_id": 959,
  "commentable_type": "Forecast::Question",
  "children_count": 0,
  "parent_id": null,
  "created_at": "2023-09-26T15:16:07.461Z",
  "updated_at": "2023-09-26T15:16:07.461Z",
  "net_votes_count": 0,
  "anonymous": false,
  "membership_username": "TheTank2",
  "membership_avatar_url": "/assets/default_theme/v18/ident/default_avatars/level-1-1-b9c925ca8bbd1b06f41ec78eecb73e098a6f1dc741c688684307fa6d59917c69.png",
  "commenter_id": 2265,
  "commenter_type": "Ident::Membership",
  "commentable_name": "question-name ff632fd942fc",
  "content": "And now his watch has ended.",
  "content_html": "\u003cdiv class=\"content\"\u003e\n  \n\u003cdiv class=\"raw_content\"\u003e\n  And now his watch has ended.\n\u003c/div\u003e\n\u003c/div\u003e"
}

// When creating a reply comment:
{
  "id": 1195,
  "commentable_id": 959,
  "commentable_type": "Forecast::Question",
  "children_count": 0,
  "parent_id": null,
  "created_at": "2023-09-26T15:57:22.074Z",
  "updated_at": "2023-09-26T15:57:22.074Z",
  "net_votes_count": 0,
  "anonymous": false,
  "membership_username": "TheTank4",
  "membership_avatar_url": "/assets/default_theme/v18/ident/default_avatars/level-1-1-b9c925ca8bbd1b06f41ec78eecb73e098a6f1dc741c688684307fa6d59917c69.png",
  "commenter_id": 2264,
  "commenter_type": "Ident::Membership",
  "commentable_name": "question-name d43b5b6bbbe0",
  "content": "comment\n 1",
  "content_html": "\u003cdiv class=\"content\"\u003e\n  \n\u003cdiv class=\"raw_content\"\u003e\n  \u003cbr\u003ecomment\u003cbr\u003e 1\n\u003c/div\u003e\n\u003c/div\u003e",
  "children": [
    {
      "id": 1196,
      "commentable_id": 959,
      "commentable_type": "Forecast::Question",
      "children_count": 0,
      "parent_id": 123,
      "created_at": "2023-09-26T15:57:22.113Z",
      "updated_at": "2023-09-26T15:57:22.113Z",
      "net_votes_count": 0,
      "anonymous": false,
      "membership_username": "TheTank2",
      "membership_avatar_url": "/assets/default_theme/v18/ident/default_avatars/level-1-1-b9c925ca8bbd1b06f41ec78eecb73e098a6f1dc741c688684307fa6d59917c69.png",
      "commenter_id": 2265,
      "commenter_type": "Ident::Membership",
      "content": "And now his watch has ended.",
      "content_html": "\u003cdiv class=\"content\"\u003e\n  \n\u003cdiv class=\"raw_content\"\u003e\n  And now his watch has ended.\n\u003c/div\u003e\n\u003c/div\u003e"
    }
  ]
}
```

### HTTP Request

`POST https://yoursite.cultivateforecasts.com/api/v1/comments`


### Comment Parameters

Parameter | Required? | Description
--------- | --------- | -----------
parent_id | No | The ID of another comment to which this is a reply.
commentable_id | Yes | The ID of the commentable that this comment should be attached to. Most likely a question ID.
commentable_type | Yes | The type of commentable that this comment should be attached to. Most likely `Forecast::Question`.
comment.content | Yes | The text of the comment.
