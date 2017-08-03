# Errors
> Example of an error related to an object:

```json
{
  "errors": [
    {
      "source": {
        "pointer": "/data/attributes/last_name"
      },
      "detail": "can't be blank"
    }
  ]
}
```

> Example of error not related to an object:

```json
{
  "errors": {
    "detail": "error message"
  }
}
```

The API uses the following error codes:

Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request was not formatted correctly
401 | Unauthorised -- The authorization key and secret were incorrect
403 | Forbidden -- The user does not have access to an endpoint or object
404 | Not Found -- The specified object could not be found for the user
406 | Not Acceptable -- Request format was not JSON
422 | Unprocessable Entity - The request was OK but there were errors
500 | Internal Server Error -- We had a problem with our server