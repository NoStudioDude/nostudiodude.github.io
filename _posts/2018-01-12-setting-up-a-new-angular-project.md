---
layout: post
title:  "Setting up a new angular project"
date:   2018-01-12
categories: Angular Web Development
cover: /assets/post-covers/setup-angular.png
---

Despite all the tutorials on the internet I decided to write my own how-to on how to set up a new angular project. I'm writing this for my future me, since I'm pretty sure I will forget most of the setps I took to start working with Angular.   

Ok, let's get started. Make sure you have NodeJS installed.  

To install NodeJS visit their [website](https://nodejs.org/en/), download and install the latest version.

For this setup we will use [Visual Studio Code](https://code.visualstudio.com/), but you can use any other IDE.

Throughout this setup I will be using the integrated terminal on [Visual Studio Code](https://code.visualstudio.com/), but you are free to use any other console (gitbash, windows console, etc)

If you’re using [Visual Studio Code](https://code.visualstudio.com/), here are a few extensions you can install to help you develop in angular:
    Angular V4 Typescript snippets by johnpapa
    Auto Import by steoates
    Auto-Open Markdown Preview by hnw
    Beautify by HookyQR
    HTML Preview by Thomas Haakon Townsend
  
Ok, let’s start by opening a new terminal window, and let’s install the `Angular CLI` globally:

    npm install @angular/cli --global

Select a folder location for your new project and open the terminal in that folder, for me will be `..\documents\git\demos`

In the terminal create a new angular application by running the following command:

     ng new {application-name} --skip-install

This command will generate a new angular application. If you open that folder in your IDE you should see the following project structure:

![alt text]( {{ "/assets/post-images/project-structure.png" | absolute_url }})

We now need to install the angular dependencies. Navigate to the application’s root folder and execute the following command:

     npm install

We should be able to test our new angular application. For that execute in the terminal:

    ng serve

Congrats, you now have a running angular application. The command `ng serve` will run our application and keep track of changes made. The application will be running on `port 4200`. To see your new application go to your favorite browser and navigate to the following address:

    http://localhost:4200

If you start changing your application code, after saving, your changes will reflect right away. Meaning you don’t need to build and redeploy your angular application to see the effects in place, keep in mind that any addition to the assest folder or any configuration change will require an entire rebuild of the solution. Just `CTRL + C` in the console to stop and type `ng serve` once again.

### Project Folder Structure

App: This folder will contain all your html, css and typescript files.
Assets: This folder will contain all your images or files present in your application
Index.html: This is your main html file, this is the entry point of your application
Styles.css: This is your global styles css. Any styles in here will apply to all html files
Package.json: This file will contain all the dependencies your application uses

### Enabling HTTP and FORMS binding
Open your `src/app/app.module.ts` file and import the `FormsModule` and `HttpModule`:

     import { HttpModule } from ‘@angular/http’;
     import { FormsModule } from ‘@angular/forms’;

Now we need to tell angular to import them to our application, in the `@NgModule` inside the `imports:` array, add `HttpModule` and `FormsModule`.

It should look like this

    @NgModule({
     declarations: [
       AppComponent
     ],
     imports: [
       BrowserModule,
       HttpModule,
       FormsModule
     ],
     providers: [],
     bootstrap: [AppComponent]
    })

And that's it. You’re done, now go and make me a sandwish.