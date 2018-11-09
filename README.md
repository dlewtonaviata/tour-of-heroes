# TourOfHeroes

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 7.0.4.

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

===

# Angular Setup

## Installing
You will need `node` and `npm`, which we should already have from using React. The below line will install Angular globally on your system. You may need to run it with `sudo`... (Find that article that shows how to keep from needing `sudo` with `npm`.)

```bash
npm install -g @angular/cli
```

## Creating an App
Angular provides excellent support for starting a project without needing to do a lot of setup. The tutorial online requests that you use the defaults, but for our purposes, we'll select Angular Routing and SCSS as our setup options.

```bash
$ ng new tour-of-heroes
? Would you like to add Angular routing? Yes
? Which stylesheet format would you like to use? SCSS   [ http://sass-lang.com   ]
```

The previous command generates an application directory with the name `tour-of-heroes` in your current working directory. This application already has routing set up and uses SCSS for styles. This application can be run by switching to the `tour-of-heroes` directory that was created, and running the `ng serve` command.

**Note:** Once the application is served, it will automatically update as we make and save our changes.

# Angular Basics
There are a number of concepts to cover to create an Angular application, but Components and Services are fundamental. Components are associated with the data model and the view, while services are associated with accessing and editing that data.

## Components
In Angular, components represent basic building blocks of an application. They should be small and self-contained in order to facilitate re-use, either throughout the application or as part of a component library. In general, components are made up of three parts, as listed below. Minimal code is genereated for each part, along with a unit test, when you crate a component with the following command.


```
ng generate component <component-name>
```

**Tip:** Learn about the `ng generate` command, as it can create many useful things, and you will likely use it a lot.

* Template File
* Class File
* Stylesheet File

The three parts of the component will be generated as separate files in the `app/<component-name>` sub-directory. The file names will look like `<component-name>.component.(html|ts|scss)`. The test file has a similar pattern, but will end in `.spec.ts`. These files, and their purposes are covered in the following discussion.

**Note:** The `.ts` extension is used because Angular actually uses TypeScript, a superset of JavaScript that allows type annotations and some static type-checking.

### Component Files
#### Template
The template for a component is in the `*.component.html` generated file. The template file uses a syntax that allows almost all valid HTML, but it also allows some Angular-specific additions. The template file is the basic view of the component, but can have behavior through bindings with items defined in the class file, and styles in the stylesheet. Most importantly, this file is **_declarative_**.

#### Class File
If the template for a component is thought of as the view, then the class can be thought of as the model/controller. The only thing a class needs to be a component is to be wrapped with a `@Component` decorator that has appropriate arguments. Nothing actually needs to be done within the class itself; it can be empty. The decorator, which is actually a higher-order function, takes as an argument an object of options that define aspects of how the component should be rendered, including:

* The tag used in other component templates when displaying this component
* The template this component uses when it is rendered
* An array of links to the stylesheets the template for this component uses.

This is the minimum set of options that should be provided to the decorator in the object argument, but there are others that may be useful, which you can learn about by reading the Angular documentation.

#### Stylesheet
Components in Angular should be self-contained, re-usable units, which should include their styling. This is easily accomplished by having the stylesheet for a component near to the component template. In Angular, that stylesheet can be one of CSS, SCSS, SASS, LESS, or Stylus, which is determined on project initialization. Whichever selection is made, the styles for a component apply only to that component template and are _**not**_ inherited by children of the component, which allows for easier (_read_: contained) styles.

### Bindings
In Angular, since the template for a component and the model/controller are in separate files with differing syntax, there needs to be a way to combine them. Angular component templates have a special syntax that allows declaring the existence of bindings between the component template and component class. There are a few different syntaxes for bindings, each with different meanings, as discussed here.

#### Interpolation

Interpolation is likely the simplest binding to understand, though, technically it's syntax sugar for another binding. Interpolation works, for the most part, as expected. When interpolating a value into a template, the value replaces the text indicating that there should be inteprolation. The template syntax is `{{<value-to-interpolate>}}` where `<value-to-interpolate>` is a template expression.

Template expressions evaluate to av value. They can simply be the name of a variable or constant, or they can be a more advanced expressions that look much like JavaScript. There are a few differences, however, as some operators (`?`, `|`, `!`) have different meanings in template expressions. Most importantly, though, template expressions that involve calculations should be fast and without side-effects.
