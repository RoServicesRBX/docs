# SetRank [POST]

```/api/ranking/setrank/```

This endpoint sets the rank of a specified user.

## Request Body

| Body      | Description           | Type              |
| ----------- | ---------------------|--------------- |
| `userId`       | The user who's rank you want to change (id) | `INTEGER` |
| `groupId`    | The group which you want to look for the join request | `INTEGER` | 
| `rankId`    | The rank id you want the user ranked to | `INTEGER` |

## Examples

=== "Javascript"
    ```javascript
    async function sendReqest() {
        const response = await fetch('https://api.secureservice.app/api/ranking/setrank', {
            method: 'POST',
            headers: {
            'Content-Type': 'application/json',
            'key': 'YOUR GAMEKEY HERE'
            },
            body: JSON.stringify({ user: 'USER ID HERE', group: 'GROUP ID HERE', rankid: 'RANK ID HERE' })
        });
        return response.json();
    }
    ```
=== "Luau"
    ```lua
    local HttpService = game:GetService("HttpService")
    local URL = "https://api.secureservice.app/api/ranking/setrank"
    local function request()
	local response = HttpService:RequestAsync(
		{
			Url = URL, 
			Method = "POST",
			Headers = {
				["Content-Type"] = "application/json",
                ["key"] = "YOUR GAMEKEY HERE"
			},
			Body = HttpService:JSONEncode({userId = "USER ID HERE", groupId = "GROUP ID HERE", rankId: "RANK ID HERE"})
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