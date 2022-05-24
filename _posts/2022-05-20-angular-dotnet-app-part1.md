---
title: Building the skeleton of an Angular 12 and .NET 6 Application - Part 1
author: Adithya Vijay
date: 2022-05-20 11:00:00 +0550
categories: [Blogging, programming]
tags: [development programming dotnet6 angular12]     # TAG names should always be lowercase
---

### Introduction
In this blog, we'll be looking at how to build the structure of an application with .NET 6 as the backend and Angular 12 as the frontend. In addition we'll be using SQL database and use Entity Framework Core as the ORM for data access. Here, we will mainly focus on the .NET 6 / backend part.

### Setting up the Development Environment
We have to install the following softwares:
1. .NET 6
2. Node.js
3. Visual Studio Code
4. Postman  

The first step is to download and install [.NET 6](https://dotnet.microsoft.com/en-us/download) latest release
As we are using typescript and Angular in the frontend, we need a javascript engine that allows us to run our javascript application. It is also used to compile our typescript that we use to write the Angular code into javascript. Thus, we also need to insall [Node.js](https://nodejs.org/en/)
We can use Visual Studio Code as the IDE to code the application. It can be used to write both the Angular and .NET Code.
We use [Postman](https://www.postman.com/downloads/) for API Testing.

### Building the Walking Skeleton
A Walking Skeleton is a tiny implementation of the system that performs a small end-to-end function. It need not use the final architecture, but it should link together the main architectural components.  

The architecture and the functionality can then evolve in parallel.  

In simple terms, we will have some data in the DB. We will create an API project that fetches the data from the database. We will create an Angular project that can query the API and recieve the data from our API that comes from the DB and display it in the client browser.

### Creating .NET API Project
We will be building the .NET API project using the dotnet cli (command line interface). The first thing to check is if dotnet was installed successfully. This can be done using:

```
dotnet --info
```

To get help:

```
dotnet -h
```

To get contextual help

```
dotnet new -h (use the name of command which we need help for)
```

To create gitignore file

```
dotnet new gitignore
```

The steps to be followed are:
1. Create a solution file - ``` dotnet new sln ```
2. Create Web API project - ``` dotnet new webapi -o API```
3. Add API project into solution - ``` dotnet sln add API ```

### Setting up VSCode for C# development
Useful extensions for better c# development on VSCode are:
1. C# for VSCode by Omnisharp
2. C# Extensions by JosKreativ (for creating class directly with template)
3. Material icon theme by Philipp Kief
4. Nuget Gallery by psiclo
5. SQLite by alexcvzz
Other basics setup to be done:
1. Enable Autosave
2. Add assets files (build and debug) - will add a .vscode folder with launch.json, tasks.json

### Differences in .NET 5 and .NET 6 API projects
In the .NET 5 project we will have both startup.cs and program.cs files. The .NET6 will have only program.cs file. There are implicit global using statements in .NET 6 and there is also the nullable option. If it is ON, we need to provide a '?' on any of the properties that could be null.
The program.cs class has no main method. It is defined implicitly. It just has the code of both the ConfigureServices and Configure methods in the startup.cs

### Familiarising .NET API Project
To make the https certificate of dotnet trused by the browser, use the following command

```
dotnet dev-certs https --trust
```

1. To build the project: ```dotnet build```
2. To run the project: ```dotnet run``` - This runs the API server at https://localhost:5001/  

**How it works** (A bit technical)  

1. Program.cs  

Every .NET application has a *program.cs* class. Within this class is the Main method. When the dotnet run command is executed, it looks for the main method and executes any of the code inside this method. The main method calls another method inside the program class called CreateHostBuilder. This method Uses Host.CreateDefaultBuilder method which initialises a new instance of HostBuilder with pre-configured defaults. It sets the root-path: where to get files that are part of our project. It loads the configuration. It sets up logging, and returns an IHostbuilder. It also points to use the *startup.cs* class.  

2. Startup.cs  

The startup class has a constructor, ConfigureServices(), and Configure() methods.

Our Configuration is injected into the startup class through the constructor [This means the configuration provided in the files like appsettings.json, appsettings.development.json, userSecrets etc]

- ConfigureServices() - It is often referred to as the Dependency Injection container. If we want to make a class or service available to other areas of our application, we can add them inside this container and .NET core will take care of the creation and destruction of these classes.
- Configure() - This is used to configure the HTTP pipeline. As we make a request from our browser to our controller endpoint, the request goes through a series of middleware on the way in and the way out. The default middlewares used are: redirection, routing, authorization, and the middleware to use the endpoints and map to controllers. It looks inside the controller to see what endpoints are available and map them accordingly.

3. LaunchSettings.json
When we run the application using ```dotnet run```, Then it takes a look inside API section in the launchsettings.json to check which url to launch the app.
We can also use ```dotnet watch run``` to use a filewatcher to examine the filechanges in the terminal.

### Entity Framework Core
An Entity is the abstraction of a physical thing. As for basics we'll create a user Entity.

```
public class AppUser
{
    public int Id { get; set; }
    public string UserName { get; set; }
}
```

Entity framework is an object relational mapper (ORM). It translates our code into SQL commands that updates tables in the DB.
Earlier we used to use ADO.NET to perform database operations which was cumbersome. So Microsoft introduced the entity framework.
When using Entity Framwork we need to add an important class which derives from `DbContext` class that we get with Entity Framework.
This class acts as the bridge between our Domain (Entity classes) and the Database. DbContext is the primary class we use to interact with the database.
Entity framework allows us to write LINQ (language intergrated queries). EF supports different database providers like SQL Server, SQLite, Oracle, etc
The database provider is responsible for translating the LINQ queries to a SQL Command. 

DbContext: - Suppose we have a class called DataContext which inherits DbContext, then it should have a constructor which takes in DbContextOptions.
The options to the constructor will be passed when we add the DataContext as a service in the startup.cs DI configureservices.
We will pass in the connection string as one of the option of datacontext.
We will define the connection string inside the appsettings.developement.json file. This config is then passed into the startup class and then to datacontext.
This class will also contain the `DbSet<Entity> Name {get; set; }` where Name defines the table name in sql.

**Features**:
- Allows to query database using LINQ.
- Allows to keep track of changes in our entities.
- Allows to save - insert, update, delete to db using savechanges method.
- Uses concurrency to protect overwriting changes made by another user since data was fetched from DB.
- Deals with transactions.
- First level caching out of box. (repeated querying returns data from cache insted of hitting the db)
- Offers built in conventions
- Offers migrations

We are abstracted away from the database. So code/entity isn't affected by the DB.
It has Code-First and Data-First approaches to create database/code. The commonly used method is code-first approach.

To make use of Entity framework, we need to install 
- Microsoft.EntityFrameworkCore.Sqlite (version matching dotnet runtime version)
- Microsoft.EntityFrameworkCore.Design

To manage the db ie, create database and tables via EF, we need to install a tool called dotnet-ef

```
dotnet tool install --global dotnet-ef --version 6.0.0
```
1. Adding migration
Creating a migration based on the code we have written (the entities and datacontext)
This will create a database schema / code to create our database.

```
dotnet ef migrations add InitialCreate -o Data/Migrations
```
The migration will add Up and Down methods.

2. Updating database
After adding the migrations. We can create/update the database by adding/removing the tables.

```
dotnet ef database update
```

3. Droping database
Incase you want to delete the database.

```
dotnet ef database drop
```

### Creating API Controllers
1. An API Controller will have an attribute called [APIController]. This signifies that this class is of type apicontroller.
2. We also need [Route] attribute for this controller. how the user reaches the api controller from the client eg:- [Route("api/[controller]")]
3. A controller needs to derive from a ControllerBase.

We can Get, Post, Put, Delete using controllers by using [HttpGet], [HttpPost] attributes etc.

API Calls should be asynchronous. By doing this we can make the application more scalable.
