<link rel="shortcut icon" type="image/x-icon" href="https://www.tocc.tech/assets/img/favicon.ico">
<img src="https://www.tocc.tech/assets/img/logo/logo.svg" alt="drawing" style="width:200px;"/> 

# TOCC API Documentation
## Access Token
The first step before using any API endpoints is to obtain an Authentication Token. This token will then be used to authenticate your API calls. 

### Getting an access token for the TOCC API
**Request Type:**
`POST` 

**Authentication Url**
```
https://auth.eu.tocc.tech/api/getToken
```
You can execute a client credentials exchange to get an access token for the TOCC API. 
Here is an example. Simply replace `CLIENT-ID` and `CLIENT-SECRET` with your own values.

```
curl --request POST \
  --url https://auth.eu.tocc.tech/api/getToken \
  --header 'content-type: application/json' \
  --data '{"client_id":"CLIENT-ID","client_secret":"CLIENT-SECRET","audience":"https://api.eu.tocc.tech","grant_type":"client_credentials"}'
```

### Response

```json
{
  "access_token": "eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6InJnTTQ3ODFjeHhFUXQzY2hPc0E3VyJ9eyJpc3MiOiJodHRwczovL3RvY2MuZXUuYXV0aDAuY29tLyIsInN1YiI6IlA1U1l3SlZPSnJwOWdPRVk5NmlWc1hLN0RzbEdiVEVIQGNsaWVudHMiLCJhdWQiOiJczovL2FwaS5ldS50b2NjLnRlY2giLCJpYXQiOjE2OTUzMjA1OTksImV4cCI6MTY5NTQwNjk5OSwiYXpwIjoiUDVTWXdKVk9KcnA5Z09FWTk2aVZzWEs3RHNsR2JURUgiLCJndHkiOiJjbGllbnQtY3JlZGVudGlhbHMifQkQAZbSBpkqUHmgh8yTak0KXVwbfk0zMAAFNKf9tjPbgK2jgxbBVM6jGV6QP1YTgnl7-50GLw4wQub-HlmtjvyOve6v4DfjIA-HRqLeefRnvLoo9SGYpUBd5KDuj2LUtqCXfLyWKpB43Nn41zDvEoqQN0i4Lp8cDDCBVGA756HndSPhZsOAoNugHC0N3cao9EjVrwyyeXRViIGwiLVdKx2Swpr1UpMqu2dOFQpvNM19jvzyWl3nnEDVPeGffrIKgifKzFkSj0A5BA9AXP3_gthSO2PJbCQa4z743IRR3wBwhvxAQTIkA3Jix1I16C6IAkr-Oypzy7ckl8ZrRhPtcg",
  "token_type": "Bearer"
}
```
**That's it!**
Now that the application has an `access_token`, it is now able to make authorized calls to the API.

```
curl --request GET \
  --url http://path_to_tocc_api_endpoint/ \
  --header 'authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCIsImtpZCI6InJnTTQ3ODFjeHhFUXQzY2hPc0E3VyJ9.eyJpc3MiOiJodHRwczovL3RvY2MuZXUuYXV0aDAuY29tLyIsInN1YiI6IlA1U1l3SlZPSnJwOWdPRVk5NmlWc1hLN0RzbEdiVEVIQGNsaWVudHMiLCJhdWQiOiJodHRwczovL2FwaS5ldS50b2NjLnRlY2giLCJpYXQiOjE2OTUzMjA1OTksImV4cCI6MTY5NTQwNjk5OSwiYXpwIjoiUDVTWXdKVk9KcnA5Z09FWTk2aVZzWEs3RHNsR2JURUgiLCJndHkiOiJjbGllbnQtY3JlZGVudGlhbHMifQ.kQAZbSBpkqUHmgh8yTak0KXVwbfk0zMAAFNKf9tjPbgK2jgxbBVM6jGV6QP1YTgnl7-50GLw4wQub-HlmtjvyOve6v4DfjIA-HRqLeefRnvLoo9SGYpUBd5KDuj2LUtqCXfLyWKpB43Nn41zDvEoqQN0i4Lp8cDDCBVGA756HndSPhZsOAoNugHC0N3cao9EjVrwyyeXRViIGwiLVdKx2Swpr1UpMqu2dOFQpvNM19jz-vzyWl3nnEDVPeGffrIKgifKzFkSj0A5BA9AXP3_gthSO2PJbCQa4z743IRR3wBwhvxAQTIkA3Jix1I16C6IAkr-Oypzy7ckl8ZrRhPtcg'
```

### Sending the token API
You can use this `bearer token` with an `Authorization Header` in your request to obtain authorized access to the TOCC API.