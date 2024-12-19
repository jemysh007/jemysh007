# Angular Cheat Sheet

This cheat sheet provides a quick reference to common Angular concepts, components, services, directives, and more.

## Table of Contents

1. [Introduction](#introduction)
2. [Angular CLI](#angular-cli)
3. [Modules](#modules)
4. [Components](#components)
5. [Templates](#templates)
6. [Data Binding](#data-binding)
7. [Directives](#directives)
8. [Services and Dependency Injection](#services-and-dependency-injection)
9. [Routing](#routing)
10. [Forms](#forms)
11. [Pipes](#pipes)
12. [HTTP Client](#http-client)
13. [Lifecycle Hooks](#lifecycle-hooks)
14. [Best Practices](#best-practices)

---

## Introduction

Angular is a platform for building mobile and desktop web applications. It provides a framework for building client-side applications using HTML, CSS, and JavaScript/TypeScript.

---

## Angular CLI

The Angular CLI is a command-line interface tool that helps to initialize, develop, scaffold, and maintain Angular applications.

### Installing Angular CLI

```bash
npm install -g @angular/cli
```

### Creating a New Project

```bash
ng new my-app
```

### Running the Application

```bash
cd my-app
ng serve
```

---

## Modules

Modules are used to organize an application into cohesive blocks of functionality.

### Creating a Module

```typescript
// src/app/app.module.ts
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { AppComponent } from './app.component';

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

---

## Components

Components are the building blocks of an Angular application.

### Creating a Component

```typescript
// src/app/app.component.ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'my-app';
}
```

### Component Template

```html
<!-- src/app/app.component.html -->
<h1>{{ title }}</h1>
```

---

## Templates

Templates define the view for a component.

### Interpolation

```html
<!-- src/app/app.component.html -->
<p>{{ title }}</p>
```

### Property Binding

```html
<!-- src/app/app.component.html -->
<img [src]="imageUrl">
```

### Event Binding

```html
<!-- src/app/app.component.html -->
<button (click)="onClick()">Click me</button>
```

### Two-Way Binding

```html
<!-- src/app/app.component.html -->
<input [(ngModel)]="name">
<p>Hello, {{ name }}!</p>
```

---

## Data Binding

Data binding is used to bind data from the component to the view.

### String Interpolation

```html
<!-- src/app/app.component.html -->
<p>{{ title }}</p>
```

### Property Binding

```html
<!-- src/app/app.component.html -->
<img [src]="imageUrl">
```

### Event Binding

```html
<!-- src/app/app.component.html -->
<button (click)="onClick()">Click me</button>
```

### Two-Way Binding

```html
<!-- src/app/app.component.html -->
<input [(ngModel)]="name">
<p>Hello, {{ name }}!</p>
```

---

## Directives

Directives are classes that add additional behavior to elements in your Angular applications.

### Structural Directives

- **ngIf**

```html
<p *ngIf="isVisible">This is visible</p>
```

- **ngFor**

```html
<ul>
  <li *ngFor="let item of items">{{ item }}</li>
</ul>
```

### Attribute Directives

- **ngClass**

```html
<p [ngClass]="{ 'active': isActive }">This is a paragraph</p>
```

- **ngStyle**

```html
<p [ngStyle]="{ 'color': color }">This is a paragraph</p>
```

---

## Services and Dependency Injection

Services are used to share data and functionality across components.

### Creating a Service

```typescript
// src/app/data.service.ts
import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root'
})
export class DataService {
  getData() {
    return ['data1', 'data2', 'data3'];
  }
}
```

### Using a Service

```typescript
// src/app/app.component.ts
import { Component, OnInit } from '@angular/core';
import { DataService } from './data.service';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent implements OnInit {
  data: string[];

  constructor(private dataService: DataService) {}

  ngOnInit() {
    this.data = this.dataService.getData();
  }
}
```

---

## Routing

Routing allows you to navigate between different views or components.

### Setting Up Routes

```typescript
// src/app/app-routing.module.ts
import { NgModule } from '@angular/core';
import { RouterModule, Routes } from '@angular/router';
import { HomeComponent } from './home/home.component';
import { AboutComponent } from './about/about.component';

const routes: Routes = [
  { path: '', component: HomeComponent },
  { path: 'about', component: AboutComponent }
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule { }
```

### Using Router Outlet

```html
<!-- src/app/app.component.html -->
<nav>
  <a routerLink="/">Home</a>
  <a routerLink="/about">About</a>
</nav>
<router-outlet></router-outlet>
```

---

## Forms

Angular provides two approaches to handling forms: template-driven and reactive forms.

### Template-Driven Forms

```html
<!-- src/app/app.component.html -->
<form #form="ngForm" (ngSubmit)="onSubmit(form)">
  <input name="name" ngModel required>
  <button type="submit">Submit</button>
</form>
```

### Reactive Forms

```typescript
// src/app/app.component.ts
import { Component, OnInit } from '@angular/core';
import { FormBuilder, FormGroup, Validators } from '@angular/forms';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent implements OnInit {
  form: FormGroup;

  constructor(private fb: FormBuilder) {}

  ngOnInit() {
    this.form = this.fb.group({
      name: ['', Validators.required]
    });
  }

  onSubmit() {
    console.log(this.form.value);
  }
}
```

```html
<!-- src/app/app.component.html -->
<form [formGroup]="form" (ngSubmit)="onSubmit()">
  <input formControlName="name" required>
  <button type="submit">Submit</button>
</form>
```

---

## Pipes

Pipes transform data in the template.

### Using Built-in Pipes

```html
<!-- src/app/app.component.html -->
<p>{{ birthday | date }}</p>
<p>{{ price | currency }}</p>
<p>{{ name | uppercase }}</p>
```

### Creating a Custom Pipe

```typescript
// src/app/exponential-strength.pipe.ts
import { Pipe, PipeTransform } from '@angular/core';

@Pipe({ name: 'exponentialStrength' })
export class ExponentialStrengthPipe implements PipeTransform {
  transform(value: number, exponent: string): number {
    let exp = parseFloat(exponent);
    return Math.pow(value, isNaN(exp) ? 1 : exp);
  }
}
```

```html
<!-- src/app/app.component.html -->
<p>{{ 2 | exponentialStrength: 10 }}</p>
```

---

## HTTP Client

The HTTP client module allows you to make HTTP requests.

### Importing HttpClientModule

```typescript
// src/app/app.module.ts
import { HttpClientModule } from '@angular/common/http';

@NgModule({
  imports: [
    HttpClientModule
  ],
  // ...other properties
})
export class AppModule { }
```

### Making HTTP Requests

```typescript
// src/app/data.service.ts
import { HttpClient } from '@angular/common/http';
import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root'
})
export class DataService {
  constructor(private http: HttpClient) {}

  getData() {
    return this.http.get('https://api.example.com/data');
  }
}
```

```typescript
// src/app/app.component.ts
import { Component, OnInit } from '@angular/core';
import { DataService } from './data.service';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent implements OnInit {
  data: any;

  constructor(private dataService: DataService) {}

  ngOnInit() {
    this.dataService.getData().subscribe(data => {
      this.data = data;
    });
  }
}
```

---

## Lifecycle Hooks

Lifecycle hooks are methods that Angular calls at specific points in a component's lifecycle.

### Common Lifecycle Hooks

- `ngOnInit()`: Called once the component is initialized.
- `ngOnChanges()`: Called when an input property changes.
- `ngOnDestroy()`: Called just before the component is destroyed.

Example:

```typescript
// src/app/app.component.ts
import { Component, OnInit, OnDestroy } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent implements OnInit, OnDestroy {
  ngOnInit() {
    console.log('Component initialized');
  }

  ngOnDestroy() {
    console.log('Component destroyed');
  }
}
```

---

## Best Practices

- **Use Angular CLI**: Use Angular CLI for project setup and development.
- **Follow Angular Style Guide**: Follow the official Angular style guide for best practices.
- **Use Reactive Forms**: Prefer reactive forms over template-driven forms for better scalability.
- **Use Services for Business Logic**: Keep business logic in services and keep components focused on the view.
- **Use Lazy Loading**: Use lazy loading for modules to improve application performance.
- **Use TrackBy with ngFor**: Use `trackBy` with `ngFor` to improve performance when rendering lists.

---

## Conclusion

This Angular cheat sheet covers all the essential Angular concepts and techniques you’ll need for building modern web applications. Whether you are creating components, managing state, or handling events, this guide will help you work more effectively with Angular.
