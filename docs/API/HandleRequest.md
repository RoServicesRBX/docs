# Handle Join Request [POST]

```/api/ranking/handlejoinrequest/```

This endpoint accepts or denies the provided join request.

## Request Body

| Body      | Description           | Type              |
| ----------- | ---------------------|--------------- |
| `userId`       | The user who's join request you want to handle | `INTEGER` |
| `groupId`    | The group which you want to look for the join request | `INTEGER` | 
| `boolean`    | Should the join request be accepted? | `BOOLEAN` |

## Examples

=== "Javascript"
    ```javascript
    async function sendReqest() {
        const response = await fetch('https://api.secureservice.app/api/ranking/handlejoinrequest', {
            method: 'POST',
            headers: {
            'Content-Type': 'application/json',
            'key': 'YOUR GAMEKEY HERE'
            },
            body: JSON.stringify({ userId: 'USER ID HERE', groupId: 'GROUP ID HERE', boolean: true/false })
        });
        return response.json();
    }
    ```
=== "Luau"
    ```lua
    local HttpService = game:GetService("HttpService")
    local URL = "https://api.secureservice.app/api/ranking/handlejoinrequest"
    local function request()
	local response = HttpService:RequestAsync(
		{
			Url = URL, 
			Method = "POST",
			Headers = {
				["Content-Type"] = "application/json",
                ["key"] = "YOUR GAMEKEY HERE"
			},
			Body = HttpService:JSONEncode({userId = "USER ID HERE", groupId = "GROUP ID HERE", boolean: true/false})
		}
	)
         if response.Success then
            print("Status code:", response.StatusCode, response.StatusMessage)
            print("Response body:\n", response.Body)
        else
            print("The request failed:", response.StatusCode, response.StatusMessage)
        end
    end
    
    local success, message = pcall(request)
    if not success then
        print("Http Request failed:", message)
    end
    ```
