# MyAnotherApp

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 7.3.1.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `--prod` flag for a production build.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via [Protractor](http://www.protractortest.org/).

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI README](https://github.com/angular/angular-cli/blob/master/README.md).



#################################################################################################################################3


## PWA Feature

ngsw-config.json file and manifest.json file add the pwa feature for this app.

To simulate a network issue, disable network interaction for your application. In Chrome:

Select Tools > Developer Tools (from the Chrome menu located at the top right corner).
Go to the Network tab.
Check the Offline box.
The offline checkbox in the Network tab is checked
Now the app has no access to network interaction.

For applications that do not use the Angular service worker, refreshing now would display Chrome's Internet disconnected page that says "There is no Internet connection".

With the addition of an Angular service worker, the application behavior changes. On a refresh, the page loads normally.

If you look at the Network tab, you can verify that the service worker is active.

Requests are marked as from ServiceWorker
Notice that under the "Size" column, the requests state is (from ServiceWorker). This means that the resources are not being loaded from the network. Instead, they are being loaded from the service worker's cache.

What's being cached?
Notice that all of the files the browser needs to render this application are cached. The ngsw-config.json boilerplate configuration is set up to cache the specific resources used by the CLI:

index.html.
favicon.ico.
Build artifacts (JS and CSS bundles).
Anything under assets.
Images and fonts directly under the configured outputPath (by default ./dist/<project-name>/) or resourcesOutputPath. See ng build for more information about these options.
Pay attention to two key points:
The generated ngsw-config.json includes a limited list of cachable fonts and images extentions. In some cases, you might want to modify the glob pattern to suit your needs.

If resourcesOutputPath or assets paths are modified after the generation of configuration file, you need to change the paths manually in ngsw-config.json.

Making changes to your application
Now that you've seen how service workers cache your application, the next step is understanding how updates work.

If you're testing in an incognito window, open a second blank tab. This will keep the incognito and the cache state alive during your test.

Close the application tab, but not the window. This should also close the Developer Tools.

Shut down http-server.

Next, make a change to the application, and watch the service worker install the update.

Open src/app/app.component.html for editing.

Change the text Welcome to {{title}}! to Bienvenue à {{title}}!.

Build and run the server again:
