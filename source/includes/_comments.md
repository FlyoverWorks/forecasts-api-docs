
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