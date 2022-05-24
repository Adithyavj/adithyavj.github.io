---
title: Building the skeleton of an Angular 12 and .NET 6 Application - Part 2
author: Adithya Vijay
date: 2022-05-24 11:00:00 +0550
categories: [Blogging, programming]
tags: [development programming dotnet6 angular12]     # TAG names should always be lowercase
---

### Introduction
In this blog, we'll be looking at how to build the structure of an application with .NET 6 as the backend and Angular 12 as the frontend. This is the second part of the blog where we'll be creating the Angular 12 application. Please read part one of the blog [here](https://blog.adithyavj.in/posts/angular-dotnet-app/) on how to create the .NET 6 API.

### Versions
Angular has a major release every 6 months. The current lastest version when writing this blog is Angular 13. However we will be creating our application using Angular 12. To run Angular 12 install nodejs version greater than 16.10.

### Setup/Installation
To check the currently installed node version run ``` node --version ```
To install Angular version 12 globally run the following command in the terminal

```
npm install -g @angular/cli@12
```

To check the installed angular version run ``` ng --version ```

To create a new Angular application (with strict mode off) run the following command

```
ng new <app-name> --strict false
```
- say Y (yes) to Angular routing
- select css as sytlesheet format

### Running the application
To run the Angular application, cd into the directory containing the angular app and run the following command:

```
ng serve
```

This will start the Angular development server and compile the typescript files in the application into javascript and serve the js files from memory (the complied js files are not physical files, they are stored in memory). 


### Angular File Structure
Angular is a single page application. Our single page is index.html file. It has a tag called <app-root> in the body tag. This is an Angular component that will be loaded into our index.html when the app is running. If we inspect the page that is created on running the app, we can see 5 javascript files that were created when we compiled and ran the application. What happens behind the scenes when we run the application is : These js file references get injected into our index.html page by a utility called **web pack**. Angular does this itself.
1. Component  

<app-root> is our app.component file present in the src->app->app.component.ts. This component has a class named AppComponent. It has a decorator `@Component`. Typescript supports decorators. This is a way of giving a normal class extra powers. Here, it gives a class the ability to be and Angular component. This provides configuration meta data that determines how the component should be processed, instantiated, and used at runtime.
Component is the basics UI building block of an Angular application. Components will provide the data for the view inside the browser.
Each component has:
- selector
- templateUrl
- styleUrls

Angular components will always create seperate files for the html and css files (to make it more structured). We can pass data from our component.ts to our view component.html. This is done using interpolation `{{title}}`. 

```
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'client';
}
```

How does Angular provide the app.component to the index.html. How is it bootstrapped?
The browser doesn't know what <app-root> tag is and it gets this from the js files.  

2. Module  

Every Angular application has to have atleast one module. In a standard angular file, it is `app.module.ts` file. Inside it we have a decorator `@NgModule` to tell angular that this is an Angular module. 
Angular module file has:
- declarations
- imports
- providers
- bootstrap
The module file declares the components that are available in our application. They will be in the declaration array.
We can import other angular modules into the app.module in the imports array.
We also have a bootstrap element to bootstrap any components when our application loads. The AppComponent is bootstrapped when the module file app.module.ts is bootstrapped. The AppComponent file is the one we see in the index.html file.  

```
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';

import { AppRoutingModule } from './app-routing.module';
import { AppComponent } from './app.component';

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule,
    AppRoutingModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```  

3. Main.ts  

How is the app.module.ts file bootstrapped?
The main.ts file has platformbrowserdynamic which is responsible for providing the code to bootstrap our AppModule. Once the AppModule is bootstrapped by the main.ts, it then bootstraps the AppComponent. AppComponent is declared as a selector inside the index.htm as <app-root>. 

Typescript gets it's configuration from `tsconfig.json` file  

4. Angular.json 

It provides necessary configurations to angular cli. We provide extra scripts, styles to our app in this file. While building the app, the builder looks at this file to find the entry point of the application which is main.ts which bootstraps AppModule.

### Setting up VSCode for Angular development
Useful extensions for better angular development on VSCode are:
1. Angular Language Service
2. Angular Snippets
3. Brackets pair colorizer

### Lifecycle Events/Lifecycle Hooks
Angular has different lifecycle events. A component instance has a lifecycle that starts when an Angular instantiates the component class and renders the component view along with its child views. The lifecycle ends when Angular destroys the component instance and removes its rendered template from the DOM. We can use lifecycle hook methods to tap into key events int he lifecycle of a component.

1. NgOnInit:
When we make an http request to an API, it is an asynchronous request. It will take some time to fetch the data and bring it back. So, it cannot be done in the constructor and  is done in the NgInit() lifecycle method.
Angular handles asynchronous code using Observables. We have to subscribe to the observable to get the data.

### Making an http request to the API
To make an http request from Angular to the .NET Core API, we have to add the `HttpClientModule` to the app.modules.ts. Then add this as a dependency injection to the constructor of the app.component.ts class and use the get method to call the api.

```
this.http.get('https://localhost:5001/api/users').subscribe(response => {
      this.users = response;
    }, error => {
      console.log(error);
    });
```

While making this request, we are likely to face the CORS(Cross Origin Resource Sharing) error.

### Resolving CORS
CORS is a security mechanism. This is built into all mordern web browsers. It blocks all the http requests from our front-end to any API that is not in the same origin.
Here API is running at `localhost:5001` and client at `localhost:4200`, thus different origins. We are not allowed to get resources that exists in a different origin unless the resource says that it's okay.

This can be solved at the API side by adding the following configs in the startup.cs

```
 - in configureservices part
services.AddCors();
- in configure part after routing
app.UseCors(x => x.AllowAnyHeader().AllowAnyMethod().WithOrigins("http://localhost:4200")); - Adds a CORS middleware to your web application pipeline to allow cross domain requests.
```
When this is done, `access-control-allow-origin: http://localhost:4200` is added along with the response headers to the api request and it works.

### Displaying data in the html page
To display the users in the html page, we can use the structural directive, loop through the users and list them.
NgFor - Structural directive. It modifies the domain object model in our html

```
<ul>
    <li *ngFor="let user of users">{{user.id}} - {{user.userName}}</li>
</ul>
```

### Adding styling frameworks to the Angular application
- Adding Angular Bootstrap (NgxBootstrap)
The following command will install bootstrap, add stylesheets to angular.json file, add module to app.module.ts

```
ng add ngx-bootstrap
```

- Add font awesome

```
npm install font-awesome
```

### Using https in Angular
To allow angular to user https, add an ssl certificate and key to the angular application and make the following changes in the angular.json file

```
"options": {
      "sslKey": "./ssl/server.key",
      "sslCert": "./ssl/server.crt",
      "ssl": true
    },
```