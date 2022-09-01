# Demote [POST]

```/api/ranking/demote/```

This endpoint demotes the specified user.

## Request Body

| Body      | Description           | Type              |
| ----------- | ---------------------|--------------- |
| `userId`       | The user who you want to demote | `INTEGER` |
| `groupId`    | The group which the user is in | `INTEGER` | 

## Examples

=== "Javascript"
    ```javascript
    async function sendReqest() {
        const response = await fetch('https://api.secureservice.app/api/ranking/demote', {
            method: 'POST',
            headers: {
            'Content-Type': 'application/json',
            'key': 'YOUR GAMEKEY HERE'
            },
            body: JSON.stringify({ userId: 'USER ID HERE', groupId: 'GROUP ID HERE' })
        });
        return response.json();
    }
    ```
=== "Luau/Lua 5.2"
    ```lua
    local HttpService = game:GetService("HttpService")
    local URL = "https://api.secureservice.app/api/ranking/demote"
    local function request()
	local response = HttpService:RequestAsync(
		{
			Url = URL, 
			Method = "POST",
			Headers = {
				["Content-Type"] = "application/json",
                ["key"] = "YOUR GAMEKEY HERE"
			},
			Body = HttpService:JSONEncode({ userId = "USER ID HERE", groupId = "GROUP ID HERE"})
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
