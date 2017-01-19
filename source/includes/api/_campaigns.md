# Campaign

The current Hub team and parent HQ teams campaigns available for selection.

## Fields

Field | Description | Notes
----- | ----------- | -----
name<br> *string* | Name of campaign | Read-only
summary<br> *string* | Summary of campaign | Read-only
location<br> *string* | Where the campaign is happening | Read-only
category_id<br>*integer* | ID of the category the campaign belongs too | Read-only
start_date<br>*date* | Start date | Read-only
end_date<br>*date* | End date | Read-only
created_at<br> *datetime* | When the campaign was created | Read-only
updated_at<br> *datetime* | When the campaign was last updated | Read-only


## List campaigns
```shell
curl https://api.adventisthub.com/api/campaigns
-H "Authorization: Bearer token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "data": [
    {
      "id": "5",
      "type": "campaigns",
      "attributes": {
        "name": "Insight Sydney",
        "summary": "",
        "category_id": 9,
        "created_at": "2016-11-23T15:10:44.225+11:00",
        "updated_at": "2016-11-23T15:10:44.225+11:00",
        "location": "",
        "start_date": "2016-11-25",
        "end_date": null
      }
    },
    {
      "id": "2",
      "type": "campaigns",
      "attributes": {
        "name": "Last Empire",
        "summary": "Marketing campaign for the upcoming event",
        "category_id": 11,
        "created_at": "2016-11-17T07:47:40.680+11:00",
        "updated_at": "2016-12-05T14:27:07.873+11:00",
        "location": "Chatswood, NSW",
        "start_date": "2016-11-17",
        "end_date": "2016-12-01"
      }
    }
  ]
}
```

`GET /api/campaigns`

An array of all campaigns.