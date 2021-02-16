
# Surveys

## Survey Detail

Shows a survey and its responses

> Request:

```shell
curl "https://yoursite.cultivateforecasts.com/api/v1/surveys/:id" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75"
```

> Response:

```json
{
  "id": 142,
  "name": "survey-2",
  "user_id": 660,
  "created_at": "2021-02-16T20:20:55.872Z",
  "updated_at": "2021-02-16T20:20:55.872Z",
  "published": false,
  "description": "survey-description-2",
  "instructions": "survey-instructions-2",
  "randomize_page_order": false,
  "survey_pages": [
    {
      "id": 283,
      "name": "survey-page-3",
      "survey_id": 142,
      "user_id": 1003,
      "page_number": 1,
      "created_at": "2021-02-16T20:20:55.878Z",
      "updated_at": "2021-02-16T20:20:55.878Z",
      "time_limit": null,
      "type": null,
      "content": null,
      "acceptance_checkbox_text": null,
      "randomize_question_order": false,
      "survey_questions": [
        {
          "id": 421,
          "name": "survey-question-name-5",
          "content": "question-content-5",
          "answer_type": "dropdown",
          "survey_page_id": 283,
          "created_at": "2021-02-16T20:20:55.885Z",
          "updated_at": "2021-02-16T20:20:55.885Z",
          "response_forcing": "force",
          "image_url": null,
          "survey_answers": [
            {
              "id": 607,
              "value": "answer-value-7",
              "survey_question_id": 421,
              "created_at": "2021-02-16T20:20:55.886Z",
              "updated_at": "2021-02-16T20:20:55.886Z",
              "image_url": null
            },
            {
              "id": 608,
              "value": "answer-value-8",
              "survey_question_id": 421,
              "created_at": "2021-02-16T20:20:55.888Z",
              "updated_at": "2021-02-16T20:20:55.888Z",
              "image_url": null
            }
          ]
        },
        {
          "id": 422,
          "name": "survey-question-name-6",
          "content": "question-content-6",
          "answer_type": "text",
          "survey_page_id": 283,
          "created_at": "2021-02-16T20:20:55.889Z",
          "updated_at": "2021-02-16T20:20:55.889Z",
          "response_forcing": "not_required",
          "image_url": null,
          "survey_answers": []
        }
      ]
    },
    {
      "id": 284,
      "name": "survey-page-4",
      "survey_id": 142,
      "user_id": 1004,
      "page_number": 2,
      "created_at": "2021-02-16T20:20:55.881Z",
      "updated_at": "2021-02-16T20:20:55.881Z",
      "time_limit": null,
      "type": null,
      "content": null,
      "acceptance_checkbox_text": null,
      "randomize_question_order": false,
      "survey_questions": [
        {
          "id": 423,
          "name": "survey-question-name-7",
          "content": "question-content-7",
          "answer_type": "radio",
          "survey_page_id": 284,
          "created_at": "2021-02-16T20:20:55.892Z",
          "updated_at": "2021-02-16T20:20:55.892Z",
          "response_forcing": "suggest",
          "image_url": null,
          "survey_answers": [
            {
              "id": 609,
              "value": "answer-value-9",
              "survey_question_id": 423,
              "created_at": "2021-02-16T20:20:55.894Z",
              "updated_at": "2021-02-16T20:20:55.894Z",
              "image_url": null
            },
            {
              "id": 610,
              "value": "answer-value-10",
              "survey_question_id": 423,
              "created_at": "2021-02-16T20:20:55.896Z",
              "updated_at": "2021-02-16T20:20:55.896Z",
              "image_url": null
            }
          ]
        },
        {
          "id": 424,
          "name": "survey-question-name-8",
          "content": "question-content-8",
          "answer_type": "numeric",
          "survey_page_id": 284,
          "created_at": "2021-02-16T20:20:55.898Z",
          "updated_at": "2021-02-16T20:20:55.898Z",
          "response_forcing": "not_required",
          "image_url": null,
          "survey_answers": [
            {
              "id": 611,
              "value": "answer-value-11",
              "survey_question_id": 424,
              "created_at": "2021-02-16T20:20:55.900Z",
              "updated_at": "2021-02-16T20:20:55.900Z",
              "image_url": null
            },
            {
              "id": 612,
              "value": "answer-value-12",
              "survey_question_id": 424,
              "created_at": "2021-02-16T20:20:55.902Z",
              "updated_at": "2021-02-16T20:20:55.902Z",
              "image_url": null
            }
          ]
        }
      ]
    }
  ],
  "survey_responses": [
    {
      "id": 235,
      "user_id": 658,
      "survey_id": 142,
      "created_at": "2021-02-16T20:20:55.903Z",
      "updated_at": "2021-02-16T20:20:55.903Z",
      "status": "completed",
      "page_order": [
        "283",
        "284"
      ],
      "survey_question_responses": [
        {
          "id": 562,
          "survey_question_id": 421,
          "survey_answer_id": 607,
          "survey_response_id": 235,
          "created_at": "2021-02-16T20:20:55.914Z",
          "updated_at": "2021-02-16T20:20:55.914Z",
          "question_content": "*question-content-5",
          "answer_content": "answer-value-7"
        },
        {
          "id": 563,
          "survey_question_id": 422,
          "survey_answer_id": null,
          "survey_response_id": 235,
          "created_at": "2021-02-16T20:20:55.916Z",
          "updated_at": "2021-02-16T20:20:55.916Z",
          "question_content": "question-content-6",
          "answer_content": "I am the one who knocks."
        },
        {
          "id": 564,
          "survey_question_id": 423,
          "survey_answer_id": 607,
          "survey_response_id": 235,
          "created_at": "2021-02-16T20:20:55.918Z",
          "updated_at": "2021-02-16T20:20:55.918Z",
          "question_content": "question-content-7",
          "answer_content": "answer-value-7"
        },
        {
          "id": 565,
          "survey_question_id": 424,
          "survey_answer_id": null,
          "survey_response_id": 235,
          "created_at": "2021-02-16T20:20:55.921Z",
          "updated_at": "2021-02-16T20:20:55.921Z",
          "question_content": "question-content-8",
          "answer_content": [
            611,
            612
          ]
        }
      ]
    }
  ]
}
```

### HTTP Request

`GET https://yoursite.cultivateforecasts.com/api/v1/surveys/:id`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
responses_page | 0 | Pagination page number for the list of survey responses

### Attribute Descriptions

Parameter | Type | Description
--------- | ------- | -----------
id | integer | The id of the survey
site_id | integer | The id of the site this survey belongs to
name | string | The name of the survey
created_at | datetime | The creation timestamp for the survey
updated_at | datetime | The timestamp for the most recent update of this survey
published | boolean | Whether or not this survey has been published
description | string | The description of the survey
instructions | string | Instructions to be presented to the user at the start of the survey
randomize_page_order | boolean | Whether or not the pages in the survey will be presented to the user in random order