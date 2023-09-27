# Component

Component are key feature in Angular. You build your whole application by composing it from couple of components which you create on your own. When we create new component, its selectors are added inside app.component.html not inside index.html
Component is a typescript class, which angular can instantiate to create objects based on the blueprint that we setup here.
decorators: are typescript feature that allows you to enhance your classes, like enhance element not restricted to class.
provide some metadata to the component decorator
selector: unique selector
import { Component } from '@angular/core';
@Component({
selector: 'app-server',
template: './server.component.html',
})
export class ServerComponent {}

**app module** - it a bundle of functionalities of our app and it basically gives angular the information which features does my app have and use.
We need to register our new component inside our app component under @ngModule > declarations
@NgModule({
declarations: [AppComponent, ServerComponent],
imports: [BrowserModule, FormsModule],
providers: [],
bootstrap: [AppComponent],
})
export class AppModule {}

imports: [BrowserModule, FormsModule], -> helps to import s

## Create component using CLI commands:

ng g c servers
or
ng generate component servers

servers- component name
instead of external template file you can use inline template, meaning u can define your html inside typescript file.

either template or templateUrl needs to be present
import { Component } from '@angular/core';

@Component({
selector: 'app-servers',
template: '\<app-server>\</app-server>',
styleUrls: ['./servers.component.css'],
})
export class ServersComponent {}

or

template: `<app-server></app-server>
			<app-server></app-server>`,
styleUrls: ['./servers.component.css']
for applying styles to the template
or you can use
styles[`h3:{color: green;}`] ==> inline

## selector

\<app-server> = element selector
[app-server] = attribute selector
you can use it with div

<div app-server></div>

servers.component.ts
@Component({
//selector: 'app-servers',
selector: '[app-servers]',
//template: '<app-server></app-server>',
templateUrl: './servers.component.html',
styleUrls: ['./servers.component.css'],
})
export class ServersComponent {}

app.component.html

<h3>I'm in the app component!</h3>
<hr />
<!-- <app-servers></app-servers> -->
<div app-servers></div>

## selector by class

@Component({
//selector: 'app-servers',
//selector: '[app-servers]',
selector: '.app-servers',
//template: '<app-server></app-server>',
templateUrl: './servers.component.html',
styleUrls: ['./servers.component.css'],
})
export class ServersComponent {}

app.component.html
\<h3>I'm in the app component!\</h3>
\<hr />

<!-- <app-servers></app-servers> -->
<!--<div app-servers></div>-->

\<div class="app-servers"></div>

id and sudo selectors like hover, will not work

## Databinding = communication

Communication between typescript code and html

Output Data : 1. String interpolation {{data}} 2. property binding [property] = "data"
React to user events: 1. Event Binding (event)='expression'

## Two way Binding

    [(ngModel)]= "data"

## String Interpolation:

{{}} - u can pass the property name or string, or a function that returns string, ternarry operator.. only condition is you cannot write multiline expression or block code, control expression

<p>{{ "Sever" }} with ID: {{ serverID }} is {{ getServerStatus() }}</p>

## Property binding

export class ServersComponent {
allowNewServer = false;
constructor() {
setTimeout(() => {
this.allowNewServer = true;
}, 2000);
}
}

\<button class="btn btn-primary" [disabled]="!allowNewServer">Add Server\</button>
\<p>{{allowNewServer}}</p>
\<p [innerText]="allowNewServer"></p>

event binding

\<button
class="btn btn-primary"
[disabled]="!allowNewServer"
(click)="onCreateServer()"

> Add Server
> \</button>
> \<p>{{ serverCreationStatus }}\</p>

onCreateServer() {
this.serverCreationStatus = 'Server was Created';
}

input and event

\<label for=""> Server Name:\</label>
\<input
type="text"
name=""
id=""
class="form-control"
(input)="onUpdateServerName($event)"
/>
\<button
class="btn btn-primary"
[disabled]="!allowNewServer"
(click)="onCreateServer()"

> Add Server
> \</button>
> \<p>{{ serverName }}\</p>

## Two way binding

\<input
type="text"
name=""
id=""
class="form-control"
[(ngModel)]="serverName">
/>
\<p>{{ serverName }}\</p>

## What are directives?

Directives are instructions in the DOM. Components are directives

**prebuilt directives**

1. ngIf
   added using an attribute selector. _ngif - _ means structural directive really changing the dom
   \<p *ngIf="serverCreated">Server was created! Name is {{ serverName }}\</p>
   it can take function as expression too, just need to return true or false
   2.ngIf else
   \<p *ngIf="serverCreated; else noServer">
   Server was created! Name is {{ serverName }}
   \</p>
   \<ng-template #noServer>
   \<p>No server was created!\</p>
   \</ng-template>

**attribute directives** : don't add or remove elements. they only change elements they were placed on.
ngStyle
ngClass - add or remove class

\<p
[ngStyle]="{ backgroundColor: getColor() }"
[ngClass]="{ online: serverStatus === 'online' }"

> {{ "Sever" }} with ID: {{ serverID }} is {{ getServerStatus() }}
> \</p>

**\*ngFor** - structural directive, changing the dom
