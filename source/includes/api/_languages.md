# Language

Spoken languages.

## Fields

Field | Description | Notes
----- | ----------- | -----
name<br> *string* | Name of language | Read-only
code<br> *string* | 3 letter iso639-3 language code | Read-only

## List languages
```shell
curl https://adhubapi.adventistchurch.com/api/app/languages
-H "Authorization: Bearer contact_token"
-H "Accept: application/vnd.adventisthub.v1+json"
```
```json
{
  "data": [
    {
      "id": "20",
      "type": "languages",
      "attributes": {
        "name": "Burmese",
        "code": "bur"
      }
    },
    {
      "id": "18",
      "type": "languages",
      "attributes": {
        "name": "Cantonese",
        "code": "yue"
      }
    }
  ]
}
```

`GET /api/app/languages`

An array of all languages.