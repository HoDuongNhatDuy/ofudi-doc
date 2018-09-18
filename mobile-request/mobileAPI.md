
**Please make sure all API have base params: (Return code and message defined**
 [here](../returnCode.md))
```json
{
  "code": 200
  "message": "Success"
  "body": {...}
}
```
# User

## Get user info

API: `api/getuserinfo/{userid}/{token}`

- Method: GET
- Response:

```json
{
  "code": 200,
  "message": "Success",
  "body": {
    "name": "Lý Anh Vũ",
    "city": "Hồ Chí Minh",
    "country": "Việt Nam",
    "description": "I am passionate about my work. Because I love what I do, I have a steady source of motivation that drives me to do my best. In my last job, this passion led me to challenge myself daily and learn new skills that helped me to do better work.",
    "avatarUrl": "https://s3-alpha.figma.com/img/b972/4386/b2e75e65ea7c4288f256661a20679ae2",
    "smallAvatarUrl": "https://s3-alpha.figma.com/img/b972/4386/b2e75e65ea7c4288f256661a20679ae2",
    "imagesUrl": [
      "https://s3-alpha.figma.com/img/e38a/a2f4/39d41edf0dbefead620036a6c1bbae44",
      "https://s3-alpha.figma.com/img/f4d2/d905/111aaf3c2002ed8cb0eca9ead92eaeac",
      "https://s3-alpha.figma.com/img/861b/7878/7e3293db5611908c3c258c47b8b1ece0"
    ],
    "hobbyTags": [
      "Phượt",
      "Ăn",
      "Mua Sắm",
      "Nghe nhạc",
      "Hello World"
    ],
    "id": "566490e9c81877d8ba1f8082a1eff6ee",
    "email": "hanld@vng.com.vn",
    "gender": "0",
    "old": "18",
    "isVerified": true,
    "isHost": true,
    "houses": [
      {
        "id": "f2d09b4ea5c7743eb8ec1547ad47d00d",
        "bannerurl": "https://s3-alpha.figma.com/img/7c25/721e/df68f241e211f880c86c16d13002332b",
        "city": "Tam đảo",
        "country": "Việt Nam"
      }
    ]
  }
}
```
Description param:

| Param             |      Type      |  Description                                                                 |
|-------------------|:--------------:|-----------------------------------------------------------------------------:|
| `name`            | String         |  _                                                                           |
| `city`            | String         |  _                                                                           |
| `country`         | String         |  _                                                                           |
| `description`     | String         |  _                                                                           |
| `avatarUrl`       | String         |  _                                                                           |
| `smallAvatarUrl`  | String         |  <p align="left">Avatar has scaled wih small size from origin avatar</p>     |
| `imagesUrl`       | List of String |  <p align="left">List of images shown as gallery in tab account</p>          |
| `hobbyTags`       | List of String |  _                                                                           |
| `id`              | String         |  <p align="left">A primary key to identify user, generate by server</p>      |
| `email`           | String         |  _                                                                           |
| `gender`          | int            |  <p align="left">Only accept 3 value: <br> `0`: `Male`<br> `1`: `Female`<br> `2`: `Unknow`</p> |
| `old`             | int            |  _                                                                           |
| `isVerified`      | boolean        |  _                                                                           |
| `isHost`          | boolean        |  <p align="left">`true` if `houses` is  NOT empty</p>                        |
| `houses`          | List of House  |  _                                                                           |


House model:

| Param             |      Type      |  Description                                                                 |
|-------------------|:--------------:|-----------------------------------------------------------------------------:|
| `id`              | String         |  _                                                                           |
| `bannerurl`       | String         |  _                                                                           |
| `city`            | String         |  _                                                                           |
| `country`         | String         |  _                                                                           |
| ...               | String         |  _                                                                           |

# Host

## Get list hosts

API: `api/host/{userid}/{query param: isVerify, locale, radius ,.. }`

- Method: GET
- Response:

```json
{
  "code": 200,
  "message": "Success",
  "body": [
    {
      "hostid": "566490e9c81877d8ba1f8082a1eff6ee",
      "hostname": "Lý Anh Vũ",
      "city": "Seoul",
      "country": "Korean",
      "isVerified": true,
      "avatarUrl": "https://s3-alpha.figma.com/img/d8f6/e236/d0ad04a6b2f877bf80990a605038fdc1",
      "distance": 10
    },
    {
      "hostid": "d67e5332287e105484d3dd8cbcb107bc",
      "hostname": "Lê Bá Quý",
      "city": "Hồ Chí Minh",
      "country": "Việt Nam",
      "isVerified": false,
      "avatarUrl": "https://s3-alpha.figma.com/img/ea38/6b11/3c4ce6f55e7c399a9172cf9da0511a0f",
      "distance": 100.0
    }
  ]
}
```
