# Asktrology Horoscope Comment API (Cornetto)

API Endpoint: 
```
https://asktrology.com/cornetto
```

Api key is valid for all requests. This parameter must be delivered with the header property "x-api-key".

## `[POST] /user` (User Create)

Sample Request:
```
curl --location --request POST 'https://asktrology.com/cornetto/user' \
--header 'x-api-key: {APIKEY}' \
--header 'Content-Type: application/json' \
--data-raw '{"name": "John Doe", "email": "johndoe@gmail.com", "birthdate": "1971-01-01", "birthtime": "00:00", "gender": "1"}'
```

Payload Description: 
| Property | Description |
| --- | --- |
| name | User's name and surname |
| email | User's e-mail information |
| birthdate | User's date of birth (Format: YYYY-MM-DD) |
| birthtime | User's time of birth (Format: HH:MM) |
| gender | 0: Non Binary, 1: Femela, 2: Male |

Sample Respone:
```JSON
{
    "message": "User created and horoscope calculation done.",
    "comment": "6bc5054ab963e44364d2594118089a62"
}
```

## `[POST] /comment` (Get Comment & Horoscope Detail)

Sample Request:
```curl --location --request POST 'https://asktrology.com/cornetto/comment' \
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
