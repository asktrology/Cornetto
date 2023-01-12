# Asktrology Horoscope Comment API (Cornetto)

API Endpoint: 
```
https://asktrology.com/cornetto
```

Api key is valid for all requests. This parameter must be delivered with the header property "x-api-key".

## `[GET] /countries` (Country List)

Sample Request:
```
curl --location --request POST 'https://asktrology.com/cornetto/user' \
--header 'x-api-key: {APIKEY}'
```

Sample Respone:
```JSON
{
    "countries": [
        "Germany",
        "Turkey",
        "..."
    ]
}
```

## `[GET] /cities?country={country}` (City List)

Sample Request:
```
curl --location --request POST 'https://asktrology.com/cornetto/cities?country={country}' \
--header 'x-api-key: {APIKEY}'
```

Request Description: 
| Property | Description |
| --- | --- |
| country | String in Country List |

Sample Respone:
```JSON
{
    "cities": [
        "Adana",
        "Adiyaman",
        "..."
    ]
}
```

## `[POST] /user` (User Create)

Sample Request:
```
curl --location --request POST 'https://asktrology.com/cornetto/user' \
--header 'x-api-key: {APIKEY}' \
--header 'Content-Type: application/json' \
--data-raw '{"id": 1, "birthdate": "1971-01-01", "birthtime": "00:00", "country": "Turkey", "city": "Istanbul"}'
```

Payload Description: 
| Property | Description |
| --- | --- |
| id | User Id created by requester |
| birthdate | User's date of birth (Format: YYYY-MM-DD) |
| birthtime | User's time of birth (Format: HH:MM) |
| country | Country of birth of the user |
| city | City of birth of the user |

Sample Respone:
```JSON
{
    "message": "User created.",
    "comment": "6bc5054ab963e44364d2594118089a62"
}
```

## `[GET] /user?id={id}` (Get User & Create Comment)

Sample Request:
```
curl --location --request POST 'https://asktrology.com/cornetto/user?id={id}' \
--header 'x-api-key: {APIKEY}'
```

Request Description: 
| Property | Description |
| --- | --- |
| id | The id sent at creation by requester |

Sample Respone:
```JSON
{
    "user": {
        "id": "1",
        "birthdate": "1971-01-01",
        "birthtime": "00:00",
        "country": "Turkey",
        "city": "Istanbul",
        "created_at": "2023-01-01 00:00:00"
    },
    "comment": "6bc5054ab963e44364d2594118089a62"
}
```

## `[POST] /comment` (Get Comment & Horoscope Detail)

Sample Request:
```
curl --location --request POST 'https://asktrology.com/cornetto/comment' \
--header 'x-api-key: {APIKEY}' \
--header 'Content-Type: application/json' \
--data-raw '{"comment": "6bc5054ab963e44364d2594118089a62"}'
```

Payload Description: 
| Property | Description |
| --- | --- |
| comment | Hash transmitted as a result of user creation |

Sample Respone:
```JSON
{
    "zodiac": {
        "key": "Aries",
        "value": "Koç"
    },
    "comment": {
        "start": "2023-01-09 00:00:00",
        "end": "2023-01-15 23:59:59",
        "text": "Lorem ipsum dolor sit amet. Qui voluptatibus praesentium sit ratione neque ad laborum amet vel eaque consectetur sed aliquid atque ut eius impedit. Qui perferendis cupiditate hic placeat quas id beatae quia aut omnis numquam.\nSit laudantium quaerat sed rerum modi sed tenetur pariatur hic sint obcaecati. Aut eius ullam est repudiandae minus qui officia sapiente sit alias debitis qui voluptas eaque ea voluptatem laborum. Aut perferendis quia et voluptatem excepturi est voluptas omnis ea velit deleniti qui minima deleniti sed repellat asperiores.\nEst galisum fugiat hic eius voluptas eos voluptatibus nisi aut quis placeat sit exercitationem autem sit consequatur veritatis. Vel eius error aut laborum consequatur et provident eligendi in quam laudantium aut corrupti repellat."
    }
}
```
