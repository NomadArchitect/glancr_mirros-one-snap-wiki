## Backend / API
The backend is implemented as an API-only Ruby on Rails app. Setup instructions for development are [in the repository](glancr/mirrOS_api). The API provides resourceful endpoints for all data structures, plus a handful of utility endpoints e. g. for fetching frontend templates. The RESTful endpoints adhere to the [JSON:API 1.0 specification](https://jsonapi.org/specification), so other API clients can interact with the backend in a standardized way.

## Management app
Implemented as a JavaScript single-page application with Vue.js. Due to the highly interconnected data model of mirr.OS resources, most state is kept in a central Vuex store.

## Display app
