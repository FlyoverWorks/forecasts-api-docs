
# Prediction Sets / Forecasts

A prediction set is the primary model for storing individual user forecasts within Cultivate Forecasts. Prediction sets have one prediction for each possible answer in the question.

## Prediction Sets List

> Request:

```shell
curl "https://yoursite.cultivateforecasts.com/api/v1/prediction_sets" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75"
```

> Response:

```json
{
  "prediction_sets": [
    {
      "id": 50,
      "membership_id": 5,
      "question_id": 2,
      "created_at": "2015-08-04T00:21:40.730Z",
      "updated_at": "2015-08-04T00:21:40.730Z",
      "comment_id": 123,
      "rationale": "7 -  Well, we have to end apartheid for one. And slow down the nuclear arms race, stop terrorism and world hunger. We have to provide food and shelter for the homeless, and oppose racial discrimination and promote civil rights, while also promoting equal rights for women.",
      "predictions": [
        {
          "id": 64,
          "type": null,
          "answer_id": 4,
          "membership_id": 5,
          "forecasted_probability": "0.3333",
          "starting_probability": "0.3333",
          "final_probability": "0.3333",
          "filled_at": null,
          "created_at": "2015-08-04T00:21:40.733Z",
          "updated_at": "2015-08-04T00:21:40.733Z",
          "confidence_level": null,
          "made_after_correctness_known": false
        },
        {
          "id": 65,
          "type": null,
          "answer_id": 5,
          "membership_id": 5,
          "forecasted_probability": "0.3333",
          "starting_probability": "0.3333",
          "final_probability": "0.3333",
          "filled_at": null,
          "created_at": "2015-08-04T00:21:40.741Z",
          "updated_at": "2015-08-04T00:21:40.741Z",
          "confidence_level": null,
          "made_after_correctness_known": false
        },
        {
          "id": 66,
          "type": null,
          "answer_id": 6,
          "membership_id": 5,
          "forecasted_probability": "0.3333",
          "starting_probability": "0.3333",
          "final_probability": "0.3333",
          "filled_at": null,
          "created_at": "2015-08-04T00:21:40.754Z",
          "updated_at": "2015-08-04T00:21:40.754Z",
          "confidence_level": null,
          "made_after_correctness_known": false
        }
      ]
    }
  ]
}
```

### HTTP Request

`GET https://yoursite.cultivateforecasts.com/api/v1/prediction_sets`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
page | 0 | Pagination page number
membership_id | none | Returns predictions for a single membership
question_id | none | Returns predictions for a single question
filter | none | Filters the question list. Possible values: `comments_with_links`, `comments_following`
created_before | none | Returns only prediction sets created before the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
created_after | none | Returns only prediction sets created after the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
updated_before | none | Returns only prediction sets updated before the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
updated_after | none | Returns only prediction sets updated after the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)


### Attribute Descriptions

Parameter | Type | Description
--------- | ------- | -----------
id | integer | The id of the prediction set
membership_id | integer | The id of the membership that submitted the prediction set
question_id | integer | The id of the question that this prediction set belongs to
rationale | string | The text of the rationale (if any) that the user submitted with the forecast
predictions.id | integer | The id of the prediction
predictions.answer_id | integer | The id of the answer this prediction belongs to
predictions.membership_id | integer | The id of the membership that submitted the prediction
predictions.filled_at | date | The timestamp of when the prediction was processed. This timestamp is used for scoring
predictions.made_after_correctness_known | boolean | Whether or not the prediction was submitted after the "correctness" of the answer was already known
predictions.forecasted_probability | float | The probability estimate that the user submitted with the forecast
predictions.starting_probability | float | The consensus probability of the answer prior to incorporating this forecast
predictions.final_probability | float | The consensus probability of the answer prior to incorporating this forecast


## Prediction Set Creation

This endpoint can be used to submit new prediction sets. All prediction sets require a question id as part of the URL and must include parameters for the prediction set. See below for a list of required parameters. All parameters must be nested under a "prediction_set" key (see example request body below).


> Request:

```shell
curl -X "POST" "https://yoursite.cultivateforecasts.com/api/v1/questions/1/prediction_sets" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75" \
  -H "Content-Type: application/json" \
  -H "Accept: application/json" \
	-d "{\"prediction_set\":{\"rationale\":\"An api prediction\",\"predictions_attributes\":[{,\"forecasted_probability\":0.42,\"answer_id\":140}]}}"
```

> Request body example:

```json
{
  "prediction_set": {
    "rationale": "An api prediction",
    "predictions_attributes": [
      {
        "forecasted_probability": 0.42,
        "answer_id": 140
      }
    ]
  }
}
```


> Response:

The response contains the newly created prediction set and associated prediction(s).

```json
{
    "id": 17,
    "type": "Forecast::OpinionPoolPredictionSet",
    "membership_id": 233,
    "membership_username": "TheTank38",
    "membership_avatar_url": "/assets/default_theme/v18/ident/default_avatars/level-1-1-b9c925ca8bbd1b06f41ec78eecb73e098a6f1dc741c688684307fa6d59917c69.png",
    "question_id": 56,
    "created_at": "2021-12-02T19:55:14.055Z",
    "updated_at": "2021-12-02T19:55:14.101Z",
    "question_name": "question-name 51ff26bb6cc0",
    "discover_question_id": 832,
    "rationale": "An api prediction",
    "comment_id": 21,
    "predictions": [
        {
            "id": 33,
            "type": "Forecast::Prediction",
            "answer_id": 140,
            "membership_id": 233,
            "created_at": "2021-12-02T19:55:14.063Z",
            "updated_at": "2021-12-02T19:55:14.099Z",
            "made_after_correctness_known": false,
            "forecasted_probability": 0.42,
            "starting_probability": 0.5,
            "final_probability": 0.42,
            "answer_name": "answer-name-29"
        }
    ],
    "question": {
        "active?": true,
        "state": "active",
        "binary?": true,
        "comments_count": 1,
        "correct_answer_became_highest_probability_answer_at": null,
        "correct_answer_became_highest_probability_days_before_close": null,
        "correct_answer_became_highest_probability_percentage_of_question": null,
        "closed_at": null,
        "created_at": "2021-12-02T19:55:13.987Z",
        "description": "question-desc ec45d76206ef",
        "discover_question_id": 832,
        "ends_at": "2021-12-09T19:55:00.000Z",
        "exclusive?": true,
        "external_source": null,
        "external_id": null,
        "featured": false,
        "id": 56,
        "image": null,
        "membership_id": 1019,
        "name": "question-name 51ff26bb6cc0",
        "number_bins": "disabled",
        "answers_count": 1,
        "post_forecast_survey_id": null,
        "prediction_sets_count": 1,
        "predictors_count": 1,
        "predictions_must_sum_to_100?": false,
        "published_at": "2021-12-02T19:55:12.984Z",
        "resolved_at": null,
        "resolved?": false,
        "resolution_notes": [],
        "site_id": 138,
        "starts_at": "2021-12-02T19:55:00.000Z",
        "type": "Forecast::Binary::Question",
        "updated_at": "2021-12-02T19:55:14.103Z",
        "use_ordinal_scoring": false,
        "voided_at": null,
        "void_reason": null,
        "metadata": {},
        "brier_score": "9.99",
        "scoring_start_time": "2021-12-02T14:55:12.984-05:00",
        "scoring_end_time": null,
        "answers": [
            {
                "id": 140,
                "discover_answer_id": null,
                "active?": true,
                "binary?": true,
                "correctness_known_at": null,
                "created_at": "2021-12-02T19:55:13.991Z",
                "description": "answer-desc-29",
                "display_probability": "42%",
                "ended?": false,
                "ends_at": null,
                "membership_id": 1019,
                "positions_count": 1,
                "predictions_count": 1,
                "probability_formatted": "42%",
                "question_id": 56,
                "question_name": "question-name 51ff26bb6cc0",
                "resolved_at": null,
                "resolved_by_id": null,
                "resolved?": false,
                "resolving?": false,
                "sort_order": 29,
                "status": null,
                "type": "Forecast::Binary::Answer",
                "updated_at": "2021-12-02T19:55:14.079Z",
                "name": "answer-name-29",
                "normalized_probability": 0.42,
                "probability": 0.42
            }
        ],
        "clarifications": []
    }
}
```

### HTTP Request

`POST https://yoursite.cultivateforecasts.com/api/v1/question/:question_id/prediction_sets`


### Prediction Set Parameters

Parameter | Required? | Description
--------- | --------- | -----------
rationale | Configurable per site | Contains the rationale/explanation/comment for why the user is making this forecast.
predictions_attributes | Yes | An array of prediction objects that are part of this prediction set. Valid parameters for a prediction are listed below.

### Prediction Parameters

Parameter | Required? | Description
--------- | --------- | -----------
answer_id | Yes | The answer id on which the user is forecasting.
forecasted_probability | Yes | The probability assigned to this answer by the user. Should be a float between 0 and 1.
