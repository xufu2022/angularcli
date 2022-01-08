# Angular Cli

version

    ng v
    ng new ngtest --defaults --skip-install (generate the app using default settings and skip npm install)

vs code extension 
    angualr essential

https://angular.io/cli
https://github.com/angular/angular-cli


## Generating new application

    ng new my-app
    ng new my-app --dry-run (don't write the files, but report them)
    ng new my-app --skip-install (generate without npm install)
    ng new my-app --defaults (use the default (no prompt))

    ng new --help 

    ng new my-app 
        --style scss  (Styles should use SASS)
        --prefix ma (set the default selector prefix)
        --skip-git (don’t add the project to git)
        --skip-tests (Don’t generate spec files)
        --routing (Add a default routing module)
        --strict (Use strict mode)
        --dry-run (Verify the flle names)

    ng new my-app --routing --style scss --prefix ma

Many flags can be combined

-   Ideal for settings that should exist throughout the app
-   Some flags change the configuration in angular.json

## Configuring the Angular CLI

Options to Configure the CLI

-   ng new <some-flags>
-   Manually edit angular.json
-   ng config <jsonPath> <value>

    ng config schematics.@schematics/angular:component.styleext scss


### Setting the Angular CLI’s Configuration

-   Use ng config
-   Indicate the json path
-   The --global (or –g) flag sets your global angular.json file

    ng config schematics.@schematics/angular:component.styleext scss

## Linting

-   ng lint my-app --help
-   ng lint my-app --format stylish
-   ng lint my-app --fix

https://github.com/angular-eslint/angular-eslint

# Generating code from Blueprints

    ng generate component customer      ng g c customer
    ng generate service customer-data
    ng generate class customer-model

-   Common Component Blueprint Options

| Options      | Alias | Description |
| ----------- | ----------- | ----------- |
| --inline-template      | -t       | Will the template be in the .ts file|
| inline-style   | -s        | Will the style be in the .ts file? |
|--spec || Generate a spec? |
|--view-encapsulation |-v| View encapsulation strategy|
|--change-detection |-c| Change detection strategy|
|--dry-run |-d| Report the files, don’t write them|

## Common Ways to Generate Components

-   $ ng generate component pet
-   $ ng generate component pet --inline-template --inline-style

## Commonly Used Commands

    $ ng g c pet    --flat              Don’t create a /pet folder
                    --inline-template   Put the template in the .ts file
                    --inline-style      Put styles in the .ts file
                    --prefix my         Prefix the component with my-

    ng g c pet -st --flat --prefix my   Combine aliases

## More Blueprints

-   $ ng g service      customer-data Alias s
-   $ ng g pipe         init-caps Alias p
-   $ ng g class        customer-model Alias cl
-   $ ng g directive    search Alias d
-   $ ng g interface    orders Alias i
-   $ ng g enum         gender Alias e

-   $ ng generate module sales
-   $ ng g m sales

    ng g p shared/init-caps -m app.module

## NgModule BluePrints

Use ng generate module <options>
Consider if we want routing


## Getting Help

    $ ng g --help 
    $ ng g c --help 
    $ ng g s --help 

# Generating Routing Features

Generate a new NgModule with **ng g module <name> <options>**

Define a module and a separate routing module with **--routing**

    $ ng g m sales --routing sales.module.ts & sales-routing.module

## Generating an App with Routing Features

    ng new sales --routing

## Guards

Generate a guard for routes **ng g guard <name>**

    ng g guard auth

Adding Routing Features with the Angular CLI

    ng new sales --routing
    ng g m admin --routing
    ng g c admin/users

# Building and Serving

**Builds**

-   Compile the app to an output directory
-   Build targets determine the output
-   All builds use bundling
-   Prod builds add uglification and tree-shaking


     ng build --help
     ng build

## Development Builds

-   Ideal for development
-   Output to /dist/[your app] folder, by default (see angular.json)

## Exploring the Build Bundles

| File|  Description| 
| ----------- | ----------- |
|main.js |App code|
|polyfills.js |Platform polyfills|
|styles.s |Styles|
|vendor.js |Angular and other vendor files|

## Exploring the Source in the Output

    npm install webpack-bundle-analyzer --save-dev
    ng build --stats-json
    npx webpack-bundle-analyzer dist/my-app/stats.json

    npm install source-map-explorer --save-dev
    ng build
    npx source-map-explorer dist/my-app/main.js

## Comparing Dev and Prod Build Targets

|       | ng build | ng build --prod |
| ----------- | ----------- | ----------- |
|Environment| environment.ts| environment.prod.ts|
|Cache-busting| only images referenced in css |all build files|
|Source maps| generated|not generated|
|Extracted CSS| global CSS output to .js |yes, to css file(s)|
|Uglification| no |yes|
|Tree-Shaking| no|yes|
|AOT|no| yes|
|Bundling| yes| yes|


## Common ng build Options

| Options      | Alias | Description |
| ----------- | ----------- | ----------- |
|--source-map| |   Generate a source map|
|--aot| |Ahead of Time compilation|
|--watch| -w |Watch and rebuild|
|--prod| -e |Shortcut for prod env and target|

## Serving Angular

-   ng serve --help

Common ng serve Options

| Options      | Alias | Description |
| ----------- | ----------- | ----------- |
|--open | -o| Opens in the default browser|
|--port || Port to listen to when serving|
|--live-reload || Reload when changes occur|
|--ssl || Serve using HTTPS|
|--proxy-config || Proxy configuration file|

## Adding New Capabilities

ng add <package>


-   $ ng add @angular/pwa
-   $ ng add @angular/material
-   $ ng add @angular/elements
-   $ ng add @ng-bootstrap/schematics

