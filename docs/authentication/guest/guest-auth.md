# Guide to Guest Authentication
This method allows you to create a guest instance of an account that can be used to access the API in a barebones way. It comes with many limitations, such as being only able to send 5 messages to bots. Due to this, **it is highly preferred to use [account authentication](../account/account-auth.md) instead of this method.**

# Step #1: Lazy Authentication

## Request

| URL | Method |
| - | - |
| https://beta.character.ai/chat/auth/lazy/ | `POST` |

**Headers**
| Header | Value |
| - | - |
| Content-Type | application/json |

**Payload**
```json
{
	"lazy_uuid": "{Version 4 UUID}"
}
```

## Example Response

```json
{
	"success": true,
	"token": "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX",
	"uuid": "{Version 4 UUID}"
}
```
###### The UUID is the same one from the request's payload.

# Step #2: Create Guest Account

## Request

| URL | Method |
| - | - |
| https://beta.character.ai/chat/user/ | `POST` |

**Headers**
| Header | Value |
| - | - |
| Authorization | Token  XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX |
###### Use the token you got from Step 1's response

## Example Response
```json
{
	"user": {
		"user": {
			"username": "Guest-000000000000000-0000-0000-0000-000000000000",
			"id": 111111,
			"first_name": "",
			"account": null,
			"is_staff": false
		},
		"is_human": true,
		"name": "Guest"
	}
}
```


