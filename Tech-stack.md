mirr.OS one is comprised of several individual components. The gist:
- Backend is an API-only Ruby on Rails application

### Backend / API
The backend is implemented as an API-only Ruby on Rails app. Setup instructions for development are [in the repository](https://gitlab.com/glancr/mirrOS_api). The API backend is the central hub that stores management data, settings etc. and triggers data fetching through individual sources. It provides resourceful endpoints for all data structures, plus a handful of utility endpoints e. g. for fetching frontend templates. Resourceful endpoints adhere to the [JSON:API 1.0 specification](https://jsonapi.org/specification), so other API clients can interact with the backend in a standardized way. There are some [endpoints to control core system functionality](https://gitlab.com/glancr/mirros_api/-/blob/develop/config/routes.rb#L52) that are not (yet) implemented as JSON:API conformant. The backend also provides an ActionCable web socket server to push updates out to connected clients.

The backend also schedules various jobs in the background to refresh data, act on user-defined triggers and provides functionality to integrate with the host operating system – e.g. establishing network connections, setting the system time etc. Most of this functionality is currently only implemented for Linux hosts, and specifically Ubuntu Core.

### Management app
JavaScript single-page application with Vue.js. Setup instructions for development are [in the repository](glancr/mirrOS_settings).
The settings app 

### Display app
JavaScript single-page application with Vue.js. Setup instructions for development are [in the repository](glancr/mirrOS_display). After an initial REST fetch of the active board and its related resources, the app receives updates via a web socket connection to Rails Action Cable.


### Extensions
Extension for mirr.OS are essentially Rails engines packaged as Ruby gems. Engines are the built-in “plugin” mechanism for Rails apps, and mirr.OS leverages them to provide developers with a wide range of customizable functionality.