You can control mirr.OS **one** via JSON-API REST calls. In the examples we use _glancr.local_. In case your system does not support bonjour/zeroconf/mDNS, you will need to use the local IP address.

[[_TOC_]]

# External control of multiboards
**Use case:** you have created several boards and want to control which board is displayed via an external service.

First you need to know the board ID. The board ID starts at "1" and is counted up. So the second board has the ID "2" and so on. If a board is deleted, the ID is not assigned again, but the count is continued.

If you want to get all board IDs before, you can do this with the following command:

` curl "http://glancr.local/api/boards?fields[boards]=id" `

The command to set the active board would be

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

# Call system commands externally

In mirr.OS one we have some buttons that allow you to reboot the system etc. without having to open a terminal:

- **reload** restarts the browser
- **restart** boots completely through
- **reset** deletes the settings
- **shut down** and turn off the system

If you want to use external services to trigger these and other commands on a regular basis, you can do so as follows.

` curl "http://glancr.local/api/system/reload_browser" `

You can also call other commands like this. See [routes.rb](https://gitlab.com/glancr/mirros_api/-/blob/develop/config/routes.rb#52) "_Non-resourceful routes for controlling the system_"


