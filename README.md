# Child Mind Institute - Curious Admin

This repository is used for the shared API utilities of the [Curious](https://mindlogger.org/) application stack.

## Getting Started

* Curious Admin - [GitHub Repo](https://github.com/ChildMindInstitute/mindlogger-admin)
* Curious Backend - [GitHub Repo](https://github.com/ChildMindInstitute/mindlogger-backend-refactor)
* Curious Mobile App - [GitHub Repo](https://github.com/ChildMindInstitute/mindlogger-app-refactor)
* Curious Shared API Utilities - **This Repo**
* Curious Web App - [GitHub Repo](https://github.com/ChildMindInstitute/mindlogger-web-refactor)

## Features

See Curious's [Knowledge Base article](https://mindlogger.atlassian.net/servicedesk/customer/portal/3/topic/4d9a9ad4-c663-443b-b7fc-be9faf5d9383/article/337444910) to discover the Curious application stack's features.

## Technologies

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

* [Typescript](https://www.typescriptlang.org/) - TypeScript is JavaScript with syntax for types
* [React](https://reactjs.org/) - A JavaScript library for building user interfaces
* [Material UI](https://mui.com/) - Library of React UI components
* [Redux Toolkit](https://redux-toolkit.js.org/) - Global state manager for JavaScript applications
* [RTK Query](https://redux-toolkit.js.org/rtk-query/overview) - Data fetching and caching tool, included in Redux Toolkit <sup>[[1]](#footnote-1)</sup>
* [Axios](https://axios-http.com/) - Promise-based HTTP Client, used by RTK Query to execute queries
* [React-app-rewired](https://github.com/timarney/react-app-rewired/) - All the benefits of create-react-app without the limitations of "no config"

### Testing

See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

* `npm run test` - Launches the test runner in the interactive watch mode.
* `npm run test:coverage` - Generate test coverage report
* `npm run test:junit` - Generate a junit xml report
* `npm run test:related` - Runs tests only for modified files
* `npm run test:nowatch` - Runs test suite once with the `watchAll=false` flag

## Environment Variables

| Key                              | Required | Default value         | Description                                                    |
| -------------------------------- | -------- | --------------------- | -------------------------------------------------------------- |
| REACT_APP_API_DOMAIN             | yes      | null                  | Curious Backend API base URL                                |
| REACT_APP_WEB_URI                | yes      | <http://localhost:5173> | Base URL of the Curious respondent web app                  |
| REACT_APP_ENV                    | no       | null                  | Environment to run the app in (`prod` or `staging`)            |
| REACT_APP_DEVELOP_BUILD_VERSION  | no       | null                  | Footer app build number                                        |
| REACT_APP_MIXPANEL_TOKEN         | no       | null                  | Mixpanel token                                                 |
| REACT_APP_LAUNCHDARKLY_CLIENT_ID | no       | null                  | LaunchDarkly client key to choose target environment           |
| REACT_APP_DD_APP_ID              | no       | ""                    | DataDog RUM App ID                                             |
| REACT_APP_DD_CLIENT_TOKEN        | no       | ""                    | DataDog RUM Client token                                       |
| REACT_APP_DD_VERSION             | no       | local                 | Current admin panel version                                    |
| REACT_APP_DD_TRACING_URLS        | no       | <http://localhost:3000> | Comma separated URL prefixes that Datadog is allowed to trace. |

## Developer Notes

### Development Status

This repository is a work in progress and is not yet officially supported.

<a id="footnote-1"></a>

### <sup>[1]</sup> Migration to RTK Query

Currently only a subset of API calls have been migrated to use RTK Query. The remaining unmigrated calls still use the following approaches:

* Queries are done via a custom hook, `useAsync`, a rudimentary querying mechanism that is similar to RTK Query's `useLazyQuery` syntax, but lacks caching.
  * Sometimes Redux state, with API calls being made inside thunks, is inconsistently used to loosely mimic "cache" for certain entities.
* Mutations are done by calling individual mutation functions directly, lacking integrated cache invalidation.

Migration of such relics is a work-in-progress, with the goal of all API calls, including API-based Redux thunks, being converted to simpler RTK Query syntax. All new API calls should use RTK Query.

## License

Delayed Open Source Attribution License 1.0 (DOSA-1.0)

Refer to [LICENSE.md](./LICENSE.md)
