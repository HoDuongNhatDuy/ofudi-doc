# Welcome to Ofudi APIs!
- API requested from Mobile team [here](mobile-request/mobileAPI.md).
Feel free to comment and edit it.
- Default content type: application/json
# 1. Admin
## 1.1. Authentications
### 1.1.1. Register
- URL: /api/auth/register
- Method: POST
- Header
- Parameters
- Body
	```
	{  
		"username": "user1",  
		"password": "123",  
		"email": "user1@mailinator.com"  
	}
	```
- Success response `201 Created`
	```
	{
		"username": "user1",
		"email": "user1@mailinator.com",
		"roles": [
			"member"
		],
		"_id": {
			"$id": "5b93f8028568a62094001402"
		}
	}
	```
### 1.1.2. Get token
- URL: /api/auth/token
- Method: POST
- Header: Basic authorization
- Parameters:
- Body:
- Success response `201 Created`
	```
	{
		"access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpYXQiOjE1MzY0MjQyMTUsImV4cCI6MTUzNjQyNzgxNSwianRpIjoiNkJUYUsyVGV3TkRFZWlXM0NiZFBwdSIsInN1YiI6InVzZXIxIn0.f2igxRFOkzkcJf6wsshowKVj9NqeE7JcbZN_iIPNT2U",
		"refresh_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpYXQiOjE1MzY0MjQyMTUsImV4cCI6MTUzOTAxNjIxNSwianRpIjoiNlN1amZkQ0FoR3ljNjJCNTZLOE5abSIsInN1YiI6InVzZXIxIn0.T8ooIOZjU324og7j2JDeTFznYYg40tfWyceZBWq_QHo",
		"expires": 1536427815
	}
	```
### 1.1.3. Refresh token
- URL: /api/auth/refresh-token
- Method: POST
- Header:
- Parameters:
- Body:
	```
	{  
		"refresh_token": "eyJ.dfgd.dfgd"  
	}
	```
- Success response `201 Created`
	```
	{
		"access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpYXQiOjE1MzY0MjQyMTUsImV4cCI6MTUzNjQyNzgxNSwianRpIjoiNkJUYUsyVGV3TkRFZWlXM0NiZFBwdSIsInN1YiI6InVzZXIxIn0.f2igxRFOkzkcJf6wsshowKVj9NqeE7JcbZN_iIPNT2U",
		"refresh_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpYXQiOjE1MzY0MjQyMTUsImV4cCI6MTUzOTAxNjIxNSwianRpIjoiNlN1amZkQ0FoR3ljNjJCNTZLOE5abSIsInN1YiI6InVzZXIxIn0.T8ooIOZjU324og7j2JDeTFznYYg40tfWyceZBWq_QHo",
		"expires": 1536427815
	}
	```
### 1.1.4. Send reset password request
After sending request, a `Reset Code` will be sent to customer via email
- URL: /api/auth/send-reset-password-request
- Method: POST
- Header:
- Parameters:
- Body:
	```
	{  
		"email": "user1@mailinator.com"  
	}
	```
### 1.1.5. Reset password
## 1.2. User
### 1.2.1. Get
- URL: /api/users
- Method: GET
- Header: Bearer Token
- Parameters:
 page: (optional)
- Body: 
- Success response `200 OK`
	```
	{
		"rows": 2,
		"pages": 1,
		"users": [
			{
				"_id": "5b9147b88568a624d8002512",
				"username": "user1",
				"email": "user1@mailinator.com",
				"roles": [
					"member"
				]
			},
			{
				"_id": "5b93f8028568a62094001402",
				"username": "user2",
				"email": "user2@mailinator.com",
				"roles": [
					"member"
				]
			}
		]
	}
	```
# 2. Member
## 2.1. Authentications
### 2.1.1. Verify Facebook account
- URL: /api/member/verify-facebook-account
- Method: POST
- Header: Bearer Facebook_Token
- Parameters:
- Body: 
- Success response `200 OK`
	```
	{
	    "_id": "5ba534d08568a60b600036a4",
	    "facebookId": "1874330452687355",
	    "onBoarding": true
	}
	```
### 2.1.2. Revoke Facebook token
- URL: /api/member/revoke-facebook-token
- Method: POST
- Header: Bearer Facebook_Token
- Parameters:
- Body: 
- Success response `200 OK`
	```
	{
	    "message": "Revoked token successfully"
	}
	```
## 2.2. Profile
### 2.2.1. Update
- URL: /api/member/update-profile
- Method: POST
- Header: Bearer Facebook_Token
- Parameters:
- Body: 
	```
	{
		"name": "Lý Anh Vũ",
		"city": "Hồ Chí Minh",
		"country": "Việt Nam",
		"hobbyTags": [
			"Phượt",
			"Ăn",
			"Mua Sắm",
			"Nghe nhạc",
			"Hello World"
		 ],
		"email": "hanld@vng.com.vn",
		"gender": "0",
		"old": "18",
		"isHost": true
	}
	```
- Success response `200 OK`
	```
	{
		"_id": "5ba534d08568a60b600036a4",
		"facebookId": "1874330452687355",
	    	"facebookToken": "EAAETKIAArI8BAJQKvcIU...uoQUtyMZD",
	    	"facebookTokenExpiredAt": 1538064000,
	    	"avatarThumbnailUrl": "/uploads/images/avatars/4dcb1909316f7e0172d33d750c80f1ad_thumbnail.jpg",
	    	"avatarUrl": "/uploads/images/avatars/4dcb1909316f7e0172d33d750c80f1ad.jpg",
	    	"name": "Lý Anh Vũ",
	    	"city": "Hồ Chí Minh",
	    	"country": "Việt Nam",
	    	"hobbyTags": [
			"Phượt",
			"Ăn",
			"Mua Sắm",
			"Nghe nhạc",
			"Hello World"
	    	],
	    	"email": "hanld@vng.com.vn",
	    	"gender": "0",
	    	"old": "18",
	    	"isHost": true,
	    	"onBoarding": false
	}
	```
### 2.2.2. Upload avatar
- URL: /api/member/upload-avatar
- Method: POST
- Header: Bearer Facebook_Token
- Parameters:
- Body: 
	+ avatar: File Type
- Success response `200 OK`
	```
	{
		"avatarUrl": "/uploads/images/avatars/b0a7f019830ff6ca4b9f38de6f9b89a4.png",
		"avatarThumbnailUrl": "/uploads/images/avatars/b0a7f019830ff6ca4b9f38de6f9b89a4_thumbnail.png"
    }
	```
### 2.2.3. Get profile
- URL: /api/member/get-personal-info
- Method: GET
- Header: Bearer Facebook_Token
- Parameters:
- Body: 
	```
	{
	    "_id": "5bbcab9541cc104c2354c4a2",
	    "facebookId": "1905622459558234",
	    "facebookToken": "EAAepKaWilCkBAJ3qyGZAqR6mO1kFtByXg...JfM3jkjddRifcZD",
	    "facebookTokenExpiredAt": 1539446400
	}
	```
- Success response `200 OK`
	```
	{
		"_id": "5ba534d08568a60b600036a4",
		"facebookId": "1874330452687355",
	    	"facebookToken": "EAAETKIAArI8BAJQKvcIU...uoQUtyMZD",
	    	"facebookTokenExpiredAt": 1538064000,
	    	"avatarThumbnailUrl": "/uploads/images/avatars/4dcb1909316f7e0172d33d750c80f1ad_thumbnail.jpg",
	    	"avatarUrl": "/uploads/images/avatars/4dcb1909316f7e0172d33d750c80f1ad.jpg",
	    	"name": "Lý Anh Vũ",
	    	"city": "Hồ Chí Minh",
	    	"country": "Việt Nam",
	    	"hobbyTags": [
			"Phượt",
			"Ăn",
			"Mua Sắm",
			"Nghe nhạc",
			"Hello World"
	    	],
	    	"email": "hanld@vng.com.vn",
	    	"gender": "0",
	    	"old": "18",
	    	"isHost": true,
	    	"onBoarding": false,
		"files": [
			{
			    "_id": "5bc8a0b98568a62c60002b52",
			    "basename": "eaf1e4244177e5695643d83927f18cdf",
			    "extension": "jpg",
			    "filename": "eaf1e4244177e5695643d83927f18cdf.jpg",
			    "path": "/uploads/member-files/eaf1e4244177e5695643d83927f18cdf.jpg",
			    "size": 776564,
			    "type": "image",
			    "timestamp": 1539875001,
			    "thumbnail": "/uploads/member-files/eaf1e4244177e5695643d83927f18cdf_thumbnail.jpg",
			    "medium": "/uploads/member-files/eaf1e4244177e5695643d83927f18cdf_medium.jpg",
			    "authorUserId": "5ba534d08568a60b600036a4"
			},
			{
			    "_id": "5bc8a1388568a62c60002b53",
			    "basename": "b35091a88e76f2c07ed9986ce813ab3c",
			    "extension": "jpg",
			    "filename": "b35091a88e76f2c07ed9986ce813ab3c.jpg",
			    "path": "/uploads/member-files/b35091a88e76f2c07ed9986ce813ab3c.jpg",
			    "size": 776564,
			    "type": "image",
			    "timestamp": 1539875128,
			    "thumbnail": "/uploads/member-files/b35091a88e76f2c07ed9986ce813ab3c_thumbnail.jpg",
			    "medium": "/uploads/member-files/eaf1e4244177e5695643d83927f18cdf_medium.jpg",
			    "authorUserId": "5ba534d08568a60b600036a4"
			}
		]
	}
	```
## 2.3. Articles
### 2.3.1. Get latest news
- URL: /api/member/articles/latest
- Method: GET
- Header: Bearer Facebook_Token
- Parameters: 
	+ page: optional
- Body: 
- Success response `200 OK`
	```
	{
	    "rows": 3,
	    "pages": 1,
	    "articles": [
		{
		    "_id": "5ba911940b2d5d15c8c2c99b",
		    "title": "3. Tú Làn - Thiên Đường Vô Danh trong vùng đất của KING KONG",
		    "subtitle": "Tú Làn - Thiên Đường Vô Danh",
		    "createdAt": 1537610472,
		    "tag": [
			"du lịch",
			"miền bắc"
		    ],
		    "headerImages": [
		    	{
				authorUserId: "5bb70cb97c43c631d05a92ef"
				basename: "9646f46d83bc2459730094348cada1a2"
				extension: "jpg"
				filename: "9646f46d83bc2459730094348cada1a2.jpg"
				medium: "/uploads/member-files/9646f46d83bc2459730094348cada1a2_medium.jpg"
				path: "/uploads/member-files/9646f46d83bc2459730094348cada1a2.jpg"
				selected: false
				size: 496105
				thumbnail: "/uploads/member-files/9646f46d83bc2459730094348cada1a2_thumbnail.jpg"
				timestamp: 1540265599
				type: "image"
				_id: "5bce967fc551d428200069b4"
			},
			{...}
		    ],
		    "relatedNews": [],
		    "components": [
			{
			    "text": "World's simplest random hex generator. Just press Generate ..."
			},
			{
			    "text": "World's simplest random hex generator. Just press Generate ...",
			    "image": {
			    	authorUserId: "5bb70cb97c43c631d05a92ef"
				basename: "9646f46d83bc2459730094348cada1a2"
				extension: "jpg"
				filename: "9646f46d83bc2459730094348cada1a2.jpg"
				medium: "/uploads/member-files/9646f46d83bc2459730094348cada1a2_medium.jpg"
				path: "/uploads/member-files/9646f46d83bc2459730094348cada1a2.jpg"
				selected: false
				size: 496105
				thumbnail: "/uploads/member-files/9646f46d83bc2459730094348cada1a2_thumbnail.jpg"
				timestamp: 1540265599
				type: "image"
				_id: "5bce967fc551d428200069b4"
			    },
			    "imageCaption": "This is image caption"
			}
		    ]
		},
		{...},
		{...}
	    ]
	}
	```
### 2.3.2. Get news detail
- URL: /api/member/articles/{NEWS_ID}
- Method: GET
- Header: Bearer Facebook_Token
- Parameters: 
- Body: 
- Success response `200 OK`
	```
	{
	    "_id": "5ba9070ccbdaba15c8226b57",
	    "tilte": "3. Tú Làn - Thiên Đường Vô Danh trong vùng đất của KING KONG",
	    "subtilte": "Tú Làn - Thiên Đường Vô Danh",
	    "createdAt": 1537610472,
	    "tag": [
		"ăn uống",
		"miền bắc"
	    ],
	    "headerImages": [
		{
			authorUserId: "5bb70cb97c43c631d05a92ef"
			basename: "9646f46d83bc2459730094348cada1a2"
			extension: "jpg"
			filename: "9646f46d83bc2459730094348cada1a2.jpg"
			medium: "/uploads/member-files/9646f46d83bc2459730094348cada1a2_medium.jpg"
			path: "/uploads/member-files/9646f46d83bc2459730094348cada1a2.jpg"
			selected: false
			size: 496105
			thumbnail: "/uploads/member-files/9646f46d83bc2459730094348cada1a2_thumbnail.jpg"
			timestamp: 1540265599
			type: "image"
			_id: "5bce967fc551d428200069b4"
		},
		{...}
	    ],
	    "components": [
		{
		    "text": "World's simplest random hex generator. Just press Generate ..."
		},
		{
		    "text": "World's simplest random hex generator. Just press Generate ..."
		},
		{
		    "image": {
			authorUserId: "5bb70cb97c43c631d05a92ef"
			basename: "9646f46d83bc2459730094348cada1a2"
			extension: "jpg"
			filename: "9646f46d83bc2459730094348cada1a2.jpg"
			medium: "/uploads/member-files/9646f46d83bc2459730094348cada1a2_medium.jpg"
			path: "/uploads/member-files/9646f46d83bc2459730094348cada1a2.jpg"
			selected: false
			size: 496105
			thumbnail: "/uploads/member-files/9646f46d83bc2459730094348cada1a2_thumbnail.jpg"
			timestamp: 1540265599
			type: "image"
			_id: "5bce967fc551d428200069b4"
		    },
		    "imageCaption": "This is image caption"
		}
	    ],
	    "relatedNews": [
		{
		    "_id": "5ba905cf0b2d5d15c8c2c998",
		    "tilte": "1. Tú Làn - Thiên Đường Vô Danh trong vùng đất của KING KONG",
		    "subtilte": "Tú Làn - Thiên Đường Vô Danh",
		    "createdAt": "1537610470",
		    "tag": [
			"du lịch",
			"miền bắc"
		    ],
		    "headerImages": [
			{
				authorUserId: "5bb70cb97c43c631d05a92ef"
				basename: "9646f46d83bc2459730094348cada1a2"
				extension: "jpg"
				filename: "9646f46d83bc2459730094348cada1a2.jpg"
				medium: "/uploads/member-files/9646f46d83bc2459730094348cada1a2_medium.jpg"
				path: "/uploads/member-files/9646f46d83bc2459730094348cada1a2.jpg"
				selected: false
				size: 496105
				thumbnail: "/uploads/member-files/9646f46d83bc2459730094348cada1a2_thumbnail.jpg"
				timestamp: 1540265599
				type: "image"
				_id: "5bce967fc551d428200069b4"
			},
			{...}
		    ],
		    "components": [
			{
			    "image": {
				authorUserId: "5bb70cb97c43c631d05a92ef"
				basename: "9646f46d83bc2459730094348cada1a2"
				extension: "jpg"
				filename: "9646f46d83bc2459730094348cada1a2.jpg"
				medium: "/uploads/member-files/9646f46d83bc2459730094348cada1a2_medium.jpg"
				path: "/uploads/member-files/9646f46d83bc2459730094348cada1a2.jpg"
				selected: false
				size: 496105
				thumbnail: "/uploads/member-files/9646f46d83bc2459730094348cada1a2_thumbnail.jpg"
				timestamp: 1540265599
				type: "image"
				_id: "5bce967fc551d428200069b4"
			    },
			    "imageCaption": "This is image caption"
			},
			{
			    "text": "World's simplest random hex generator. Just press Generate ...",
			    "imageURL": "https://image.thanhnien.vn/665/uploaded/dinhson/2018_09_24/42295280_395318397670283_1000988436670185472_n_dffb.jpg",
			    "imageCaption": "This is image caption"
			}
		    ]
		}
	    ]
	}
	```
## 2.4. Files
### 2.4.1. Upload multiple files
- URL: /api/member/files/upload-multiple
- Method: POST
- Header: Bearer Facebook_Token
- Parameters:
- Body: 
	+ files[]: File Type
	+ files[]: File Type
- Example: ![alt text](https://i.imgur.com/fJ56sp2.png "Demo")
- Success response `201 Created`
	```
	[
	    {
		"basename": "85755fa71be2dd9542ec9066f3a0543b",
		"extension": "jpg",
		"filename": "85755fa71be2dd9542ec9066f3a0543b.jpg",
		"path": "/uploads/member-files/85755fa71be2dd9542ec9066f3a0543b.jpg",
		"size": 1078250,
		"type": "image",
		"timestamp": 1539441444,
		"thumbnail": "/uploads/member-files/85755fa71be2dd9542ec9066f3a0543b_thumbnail.jpg",
		"_id": "5bc203248568a60ee40052e2"
	    },
	    {
		"basename": "44bd34f1a4ffdf24eebe84437868e256",
		"extension": "jpg",
		"filename": "44bd34f1a4ffdf24eebe84437868e256.jpg",
		"path": "/uploads/member-files/44bd34f1a4ffdf24eebe84437868e256.jpg",
		"size": 485743,
		"type": "image",
		"timestamp": 1539441444,
		"thumbnail": "/uploads/member-files/44bd34f1a4ffdf24eebe84437868e256_thumbnail.jpg",
		"_id": "5bc203248568a60ee40052e3"
	    }
	]
	```
