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
				"_id": {
					"$id": "5b9147b88568a624d8002512"
				},
				"username": "user1",
				"email": "user1@mailinator.com",
				"roles": [
					"member"
				]
			},
			{
				"_id": {
					"$id": "5b93f8028568a62094001402"
				},
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
	    "userId": {
		"$id": "5ba534d08568a60b600036a4"
	    },
	    "facebookId": "1874330452687355"
	}
	```
## 2.2. Profile
### 2.2.1. Upload avatar
- URL: /api/member/upload-avatar
- Method: POST
- Header: Bearer Facebook_Token
- Parameters:
- Body: 
- Success response `200 OK`
	```
	{
		"avatarUrl": "/uploads/images/avatars/b0a7f019830ff6ca4b9f38de6f9b89a4.png",
		"avatarThumbnailUrl": "/uploads/images/avatars/b0a7f019830ff6ca4b9f38de6f9b89a4_thumbnail.png"
    }
	```
