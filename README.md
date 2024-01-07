# APIAviator Documentation

## Introduction

APIAviator is an API service that provides the probability of crash, based on a set of values provided in the request. So the probability in which it stops before a given value that will come out on the Aviator game. This documentation provides detailed information on how to use the API to obtain predictions.

## Using the API

To use APIAviator, send an HTTPS request in the following manner:

```plaintext
GET https://aviator.p.rapidapi.com/api?number=[0,1,1,1]
```

Where `[0,1,1,1]` represents an array of values. Follow the schema provided below to correctly form the array.

### Array Formation Schema

The array must be formed following the value guidelines associated with certain outcome ranges. Here's how the outcomes correspond to values:

| Value | Outcome Range      |
|-------|--------------------|
| 0     | < 1.50, < 1.99     |
| 1     | < 2.50, < 2.99     |
| 2     | < 3.99, < 4.99     |
| 3     | < 6, < 20, > 20    |


### Example Request

```plaintext
GET https://aviator.p.rapidapi.com/api?number=[0,1,1,1]
```

### Example Response

The API will return a value indicating the life prediction or a "wait" value indicating the player should not play. The output will be accompanied by the associated life probability for each value.

```plaintext
2 - 60.1%
1.2 - 26.61%
3 - 4.5%
4 - 8.79%
```

The data is read so that the indicated number represents the value at which the player should stop playing. For example, if the returned value is 2, Aviator will stop before reaching 2.

## Integration Example

```python
import requests

url = "https://aviator.p.rapidapi.com/api"
querystring = {"number": "[0,1,1,1]"}

headers = {
    'X-RapidAPI-Host': "aviator.p.rapidapi.com",
    'X-RapidAPI-Key': "your-rapidapi-key"
}

response = requests.request("GET", url, headers=headers, params=querystring)

print(response.text)
```

Replace "your-rapidapi-key" with your personal RapidAPI key.

For further details and assistance, contact APIAviator support.
