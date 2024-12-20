# Data Binding in Angular: Detailed Explanation

Data binding is the communication bridge between the TypeScript component and the HTML template. Angular provides several types of data binding techniques for building dynamic and interactive user interfaces.

---

## 1. **String Interpolation**

- **Type**: One-way data binding.
- **Direction**: Component to Template.
- **Usage**: Embed expressions within HTML to display component properties.
- **Syntax**: `{{ expression }}`

### Example:

```typescript
export class AppComponent {
  title = "Welcome to Angular!";
}
```

```html
<h1>{{ title }}</h1>
```

- **Output**: Displays `Welcome to Angular!` in the `<h1>` tag.

you can also do computation within the set of curly `{{}}` braces.

```html
<h1>{{ title * 3 }}</h1>
```

- **Output**: Displays "Welcome to Angular!Welcome to Angular!Welcome to Angular!"

Or can do even more complex operations within curly braces. Basically these set of braces are for to execute any TypeScript valid code.

---

## 2. **Property Binding**

- **Type**: One-way data binding.
- **Direction**: Component to Template.
- **Usage**: Bind values to HTML element properties, such as `src`, `disabled`, or `value`.
- **Syntax**: `[property]="expression"`

### Example:

```typescript
export class AppComponent {
  imageUrl = "assets/logo.png";
  isDisabled = true;
}
```

```html
<img [src]="imageUrl" alt="Logo" /> <button [disabled]="isDisabled">Click Me</button>
```

- **Output**: The image's `src` is set, and the button is disabled.

Instead of `[] brackets` you can also use `bind-` keyword like `bind-src = "imageUrl"` but it's not very common.

---

## 3. **Attribute Binding**

- **Type**: One-way data binding.
- **Direction**: Component to Template.
- **Usage**: Set attribute values of HTML elements.
- **Syntax**: `bind-attribute="expression"` or `[attr.attribute-name]="expression"`

### Example:

```typescript
export class AppComponent {
  customAriaLabel = "This is a custom label";
}
```

```html
<div [attr.aria-label]="customAriaLabel">Accessible Content</div>
```

- **Output**: Adds `aria-label="This is a custom label"` to the `<div>`.

> **Note**: Use attribute binding for global attributes like `aria-label`, `role`, etc., that are not directly tied to DOM properties.

---

## 4. **Event Binding**

- **Type**: One-way data binding.
- **Direction**: Template to Component.
- **Usage**: Handle user interactions (e.g., `click`, `input`, `submit`).
- **Syntax**: `(event)="expression"`

### Example:

```typescript
export class AppComponent {
  onClick() {
    console.log("Button clicked!");
  }
}
```

```html
<button (click)="onClick()">Click Me</button>
```

- **Output**: Logs "Button clicked!" when the button is clicked.

---

## 5. **Two-Way Binding with `ngModel`**

- **Type**: Two-way data binding.
- **Direction**: Component to Template and Template to Component.
- **Usage**: Synchronize input fields with component properties.
- **Syntax**: `[(ngModel)]="property"` or `bind-value="property"`

### Example with `ngModel` on Input:

```typescript
import { Component } from "@angular/core";

@Component({
  selector: "app-root",
  templateUrl: "./app.component.html",
  styleUrls: ["./app.component.css"],
})
export class AppComponent {
  username = "";
}
```

```html
<input [(ngModel)]="username" placeholder="Enter your name" />
<p>Hello, {{ username }}!</p>
```

- **Output**: Updates the paragraph dynamically as you type in the input field.

### Example with `bind-value`:

```html
<input bind-value="username" placeholder="Enter your name" />
```

### Applying `ngModel` to Different Form Elements:

#### On a Dropdown:

```typescript
export class AppComponent {
  selectedOption = "option1";
  options = ["option1", "option2", "option3"];
}
```

```html
<select [(ngModel)]="selectedOption">
  <option *ngFor="let option of options" [value]="option">{{ option }}</option>
</select>
<p>You selected: {{ selectedOption }}</p>
```

#### On a Checkbox:

```typescript
export class AppComponent {
  isChecked = false;
}
```

```html
<input type="checkbox" [(ngModel)]="isChecked" />
<p>Checkbox is {{ isChecked ? 'checked' : 'unchecked' }}</p>
```

#### On a Radio Button:

```typescript
export class AppComponent {
  gender = "";
}
```

```html
<label> <input type="radio" [(ngModel)]="gender" value="male" /> Male </label>
<label> <input type="radio" [(ngModel)]="gender" value="female" /> Female </label>
<p>Selected gender: {{ gender }}</p>
```

> **Note**: To use `ngModel`, ensure you import `FormsModule` in your module:

```typescript
import { FormsModule } from "@angular/forms";

@NgModule({
  imports: [BrowserModule, FormsModule],
})
export class AppModule {}
```

---

## Summary Table

| Binding Type             | Syntax                                            | Direction              | Use Case                             |
| ------------------------ | ------------------------------------------------- | ---------------------- | ------------------------------------ |
| **String Interpolation** | `{{ expression }}`                                | Component -> Template  | Display dynamic content in HTML.     |
| **Property Binding**     | `[property]="expression"`                         | Component -> Template  | Bind DOM properties (e.g., `src`).   |
| **Attribute Binding**    | `[attr.attribute-name]="exp"`                     | Component -> Template  | Bind global HTML attributes.         |
| **Event Binding**        | `(event)="expression"`                            | Template -> Component  | Handle user actions like `click`.    |
| **Two-Way Binding**      | `[(ngModel)]="property"`, `bind-value="property"` | Component <-> Template | Synchronize form fields dynamically. |

---

## Resources

- [Angular Binding Syntax Overview](https://angular.io/guide/binding-syntax)
- [Angular Forms and Two-Way Binding](https://angular.io/guide/forms-overview)
- [Event Binding in Angular](https://angular.io/guide/user-input)
