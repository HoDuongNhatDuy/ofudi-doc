# Welcome to Ofudi APIs!
- Default content type: application/json
# Authentications
## Register
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
## Get token
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
## Refresh token
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
## Send reset password request
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
## Reset password
# User
## Get
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
