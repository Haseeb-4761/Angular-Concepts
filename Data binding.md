# Data Binding in Angular

Data binding in Angular is a mechanism to synchronize data between the component and the view (HTML). It allows the dynamic exchange of data, enabling seamless interaction between the user interface and the application logic.

---

## Types of Data Binding

### 1. **Interpolation (One-Way Binding)**

- Binds data from the component to the HTML template.
- Syntax: `{{ expression }}`

#### Example:
In the component:
```typescript
export class AppComponent {
  title = 'Welcome to Angular';
}
```

In the template:
```html
<h1>{{ title }}</h1>
```

---

### 2. **Property Binding (One-Way Binding)**

- Binds data from the component to an HTML element's property.
- Syntax: `[property]="expression"`

#### Example:
In the component:
```typescript
export class AppComponent {
  imageUrl = 'assets/logo.png';
}
```

In the template:
```html
<img [src]="imageUrl" alt="Logo">
```

---

### 3. **Event Binding (One-Way Binding)**

- Binds an event from the template to a method in the component.
- Syntax: `(event)="expression"`

#### Example:
In the component:
```typescript
export class AppComponent {
  onClick() {
    console.log('Button clicked!');
  }
}
```

In the template:
```html
<button (click)="onClick()">Click Me</button>
```

---

### 4. **Two-Way Binding**

- Combines property binding and event binding to synchronize data between the component and the template.
- Syntax: `[(ngModel)]="property"`

#### Example:
In the component:
```typescript
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  name = '';
}
```

In the template:
```html
<input [(ngModel)]="name" placeholder="Enter your name">
<p>Hello, {{ name }}!</p>
```

> **Note:** To use `ngModel`, you need to import `FormsModule` in your module:
```typescript
import { FormsModule } from '@angular/forms';

@NgModule({
  declarations: [AppComponent],
  imports: [BrowserModule, FormsModule],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule {}
```

---

## Summary

| Type                | Direction       | Syntax                      | Use Case                        |
|---------------------|-----------------|-----------------------------|---------------------------------|
| **Interpolation**   | Component -> View | `{{ expression }}`          | Displaying dynamic content.     |
| **Property Binding**| Component -> View | `[property]="expression"`  | Setting DOM properties.         |
| **Event Binding**   | View -> Component | `(event)="expression"`      | Handling user interactions.     |
| **Two-Way Binding** | Component <-> View | `[(ngModel)]="property"`   | Synchronizing form data.        |

---

## Resources

- [Angular Official Documentation on Data Binding](https://angular.io/guide/binding-overview)
- [Two-Way Binding in Angular](https://angular.io/guide/forms-overview)
