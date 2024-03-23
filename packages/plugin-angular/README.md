# @bugsnag/plugin-angular

A [@bugsnag/js](https://github.com/bugsnag/bugsnag-js) integration for [Angular](https://angular.io/).

This package enables you to integrate Bugsnag's error reporting with an Angular (v2+) application at a detailed level. It provides an implementation of the `@angular/core` `ErrorHandler` which you can use to capture and report unhandled errors in your app.

Reported errors will contain useful debugging info from Angular's internals, such as the component and context.

## Installation

```sh
npm i --save @bugsnag/js @bugsnag/plugin-angular
# or
yarn add @bugsnag/js @bugsnag/plugin-angular
```

## Usage

In your the root of your angular app, typically `app.module.ts`:

```typescript
// Import bugsnag-js and @bugsnag/plugin-angular
import { BugsnagErrorHandler } from '@bugsnag/plugin-angular'
import Bugsnag from 'bugsnag-js'

// configure Bugsnag ASAP, before any other imports
Bugsnag.start('API_KEY')

// create a factory which will return the Bugsnag error handler
export function errorHandlerFactory() {
  return new BugsnagErrorHandler()
}

import { ErrorHandler, NgModule } from '@angular/core'
// ... other imports omitted for brevity

@NgModule({
  /* Pass the BugsnagErrorHandler class along to the providers for your module */
  providers: [ { provide: ErrorHandler, useFactory: errorHandlerFactory } ]
  /* other properties passed to the decorator omitted for brevity */
})
```

## Support

* Check out the [documentation](https://docs.bugsnag.com/platforms/browsers/)
* [Search open and closed issues](https://github.com/bugsnag/bugsnag-js/issues?q=is%3Aissue) for similar problems
* [Report a bug or request a feature](https://github.com/bugsnag/bugsnag-js/issues/new)

## License

This package is free software released under the MIT License. See [LICENSE.txt](./LICENSE.txt) for details.
