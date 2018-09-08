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
## Get token
- URL: /api/auth/token
- Method: POST
- Header: Basic authorization
- Parameters:
- Body:
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
