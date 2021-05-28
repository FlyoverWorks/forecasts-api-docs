
# Scores

## Scores List

This API returns a list of score records. There are three types of score records: `QuestionBrierScore` (a score for a single question), `ChallengeBrierScore` (a score for all questions in a challenge), and `SiteBrierScore` (an overall score).

If a given record has a `prediction_made_by_id` value, that indicates that it is a score for a specific predictor. If the `prediction_made_by_id` is null, that indicates that it represents the crowd's score.


> Request:

```shell
curl "https://yoursite.cultivateforecasts.com/api/v1/scores" \
  -H "Authorization: Bearer b95b4f848cd226e55b7a42f6a8e8669350730270f5a91d64b6c70328b0156d75"
```

> Response:

```json
{
    "scores": [
        {
            "id": 10,
            "type": "Forecast::SiteBrierScore",
            "value": "0.25",
            "scoreable_id": 13,
            "scoreable_type": "Ident::Site",
            "site_id": 13,
            "period_started_at": null,
            "period_ended_at": null,
            "created_at": "2021-05-28T12:37:18.827Z",
            "updated_at": "2021-05-28T13:37:18.850Z",
            "ordinal_scoring_enabled": false,
            "use_price": false,
            "scoring_strategy_id": 2,
            "relative_brier_score": null,
            "comparison_brier_score_for_relative": null,
            "participation_rate": null,
            "prediction_made_by_id": 3,
            "prediction_made_by_type": "Ident::Membership",
            "forecasted_probability": null,
            "forecast_type": null
        },
        {
            "id": 8,
            "type": "Forecast::ChallengeBrierScore",
            "value": "0.25",
            "scoreable_id": 2,
            "scoreable_type": "Forecast::Challenge",
            "site_id": 2,
            "period_started_at": null,
            "period_ended_at": null,
            "created_at": "2021-05-26T13:37:18.758Z",
            "updated_at": "2021-05-28T13:37:18.790Z",
            "ordinal_scoring_enabled": false,
            "use_price": false,
            "scoring_strategy_id": 2,
            "relative_brier_score": null,
            "comparison_brier_score_for_relative": null,
            "participation_rate": null,
            "prediction_made_by_id": 3,
            "prediction_made_by_type": "Ident::Membership",
            "forecasted_probability": null,
            "forecast_type": null
        },
        {
            "id": 5,
            "type": "Forecast::QuestionBrierScore",
            "value": "0.25",
            "scoreable_id": 5,
            "scoreable_type": "Forecast::Question",
            "site_id": 2,
            "period_started_at": null,
            "period_ended_at": null,
            "created_at": "2021-05-26T13:37:18.578Z",
            "updated_at": "2021-05-28T13:37:18.679Z",
            "ordinal_scoring_enabled": false,
            "use_price": false,
            "scoring_strategy_id": 2,
            "relative_brier_score": null,
            "comparison_brier_score_for_relative": null,
            "participation_rate": null,
            "prediction_made_by_id": 1,
            "prediction_made_by_type": "Aggregation::Method",
            "forecasted_probability": null,
            "forecast_type": null,
            "discover_question_id": null
        }
    ]
}
```

### HTTP Request

`GET https://yoursite.cultivateforecasts.com/api/v1/scores`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
page | 0 | Pagination page number
score_type | none | Returns scores of a specific type. Possible values: `question`, `challenge`, `site`
membership_id | none | If this ID is present, the endpoint will give back scores for only that membership/user
with_membership_id | none | If the value of this parameter is `true`, only scores with a membership_id set will be returned
without_membership_id | none | If the value of this parameter is `true`, only scores without a membership_id set will be returned
scoreable_id | none | Filters scores to include only scores for a single scoreable. This can be the id of an `question`, `challenge`, or `site` record. If a value is passed for this parameter, the `score_type` record must also be set. So if you wanted scores for just a single question, you would pass `score_type=question&scoreable_id=123`
predictor_type | none | Filters scores to include only predicotrs of a certain type. Possible values: `user`, `team`
include_daily_scores | false | If `true`, a `daily_scores` attribute will be included with `question` scores that includes a breakdown of the predictor's daily scores for that question.
created_before | none | Returns only scores created before the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
created_after | none | Returns only scores created after the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
updated_before | none | Returns only scores updated before the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)
updated_after | none | Returns only scores updated after the passed date. Date should be in iso8601 format (e.g. 2015-08-23T15:43:11-05:00)


### Attribute Descriptions

Parameter | Type | Description
--------- | ------- | -----------
id | integer | The id of the score
type | string | The type of score
value | float | The actual score value
scoreable_id | integer | The id of the record receiving the score. A "scoreable" is something that can receive a score in the system. This can be a membership, answer, question, challenge, or site. Combine with `scoreable_type` to determine the record receiving the score.
scoreable_type | string | The type of record receiving the score
period_started_at | date | The start date of the time period being scored
period_ended_at | date | The end date of the time period being scored
ordinal_scoring_enabled | boolean | Ordinal scoring can be enabled for questions where certain answers are "closer" to being correct than others (e.g. when the answers are buckets of numbers). This flag indicates whether ordinal scoring was enabled for this score.
use_price | boolean | A true value indicates that the stock price was used to generate this score (only applicable to prediction markets)
scoring_strategy_id | integer | A scoring strategy defines a set of settings used for scoring forecasts. This indicates the id of the strategy used to generate this score
relative_brier_score | float | The relative brier score
median_brier_score_for_relative | float | The median brier score for all forecasters in this answer+period combination, which is used to compute a relative brier score
participation_rate | float | The percentage of the days that the question ran in which the user was participating
prediction_made_by_id | integer | The id of the record that submitted the forecast that generated this score. Typically a membership, but can also be a team or an external predictor
prediction_made_by_type | type | The type of the record that submitted the forecast that generated this score.
site_id | integer | The id of the site that generated the score.
