You can control mirr.OS via JSON-API REST calls.

[[_TOC_]]

# External control of multiboards
* Use case: you have created several boards and want to control which board is displayed via an external service. *

First you need to know the board ID. The board ID starts at "1" and is counted up. So the second board has the ID "2" and so on. If a board is deleted, the ID is not assigned again, but the count is continued.

If you want to get all board IDs before, you can do this with the following command:

` curl "http://glancr.local/api/boards?fields[boards]=id" `

The command to control the boards would be

```
curl -X "PATCH" "http://glancr.local/api/settings/system_activeboard" \
     -H 'Content-Type: application/vnd.api+json' \
     -d $'{
  "data": {
    "id": "system_activeboard",
    "type": "settings",
    "attributes": {
      "value": "board-id-here"
    }
  }
}'
```
