# What is Angular?

Angular is a JavaScript Framework which allows you to create reactive Single-Page-Applications (SPA). It gives the user a very reactive user experience (UX). It is one HTML file and a bunch of JavaScript code we get from the server and JavaScript changes the DOM as per the action on the browser.

## Angular Versioning

AngularJS - 1st version (totally different) (Failure due to fundamental laws)
Angular 2 - 2016 - Rewritten
Angular 3 - was skiped for internal reason
Angular 4
......
Angular 10,11,12,13,14,15
Very backward compatible

## Angular CLI

Angular projects are bit more elaborate regarding their build workflow. There are couple of files need to be converted before they can run in the browser and CLI takescare of them. Also it heavily optimize the code, so we ship optmized version to the browser.

npm install -g @angular/cli
ng new my-first-project
cd my-first-project
ng serve ===> to run and bring up development server and for development optimized app

routing - n
styling - css

localhost:4200

## Editing the first App

package.json - contains dependencies
devDependencies - for development
node_modules - all dependencies provided in package.json will be installed inside node_modules
component always as a template(html file), css and typescript file
app.component.ts - provides definition of the component, it will be converted to js
data-binding
directive ngModel
<input type="text" [(ngModel)]="name" />
\<p>{{ name }}\</p>

**ngModel** directive will assign the input to the name model.
inorder to make it work, u need to import formmodule in app.module.ts
to install bootstrap locally - npm install --save bootstrap@3

To add new styles, edit angular.json project>architect>build>styles

"styles": [
"node_modules/bootstrap/dist/css/bootstrap.min.css",
"src/styles.css"
],

## How an angular gets loaded?

index.html file is served by the browser **\<app-root>**
\<app-root> root component

@Component({
selector: 'app-root',
templateUrl: './app.component.html',
styleUrls: ['./app.component.css'],
})
export class AppComponent {
name = 'Eswari ';
}

**main.ts** - first code which is executed
import { platformBrowserDynamic } from '@angular/platform-browser-dynamic';

import { AppModule } from './app/app.module';

platformBrowserDynamic().bootstrapModule(AppModule)
.catch(err => console.error(err));

platformBrowserDynamic().bootstrapModule(AppModule) --- this line bootstrap appmodule by passing it as argument

app.module.ts inturn bootstraps app.component.ts " bootstrap: [AppComponent]"

import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { FormsModule } from '@angular/forms';
import { AppComponent } from './app.component';

@NgModule({
declarations: [AppComponent],
imports: [BrowserModule, FormsModule],
providers: [],
bootstrap: [AppComponent],
})
export class AppModule {}
