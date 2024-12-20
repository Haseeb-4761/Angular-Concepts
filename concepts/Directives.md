# Angular Directives

Angular directives are classes that add behavior to elements in Angular applications. They extend HTML by adding custom functionality and are categorized into three types: **Component Directives**, **Attribute Directives**, and **Structural Directives**.

---

## 1. **Component Directives**

### Definition
- Component directives are the most common type of directive in Angular.
- A component is essentially a directive with a template.

### Key Features
- It controls a section of the DOM through the associated template.
- Components encapsulate the view logic (HTML, CSS, and JavaScript/TypeScript).

### Example
#### Component Class (`app.component.ts`):
```typescript
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'Angular Directives Example';
}
```

#### Template (`app.component.html`):
```html
<div>
  <h1>{{ title }}</h1>
</div>
```

### How It Works
- The `selector: 'app-root'` is used in HTML (`<app-root></app-root>`) to load this component.
- The template and styles define the look and feel of this section.

---

## 2. **Attribute Directives**

### Definition
- Attribute directives are used to modify the behavior or appearance of an element.
- They change the element's attributes, styles, or classes dynamically.

### Built-In Examples
1. **`ngClass`**
   - Adds or removes classes dynamically.
   ```html
   <div [ngClass]="{ 'active-class': isActive, 'inactive-class': !isActive }">
     Toggle Class Example
   </div>
   ```
2. **`ngStyle`**
   - Applies styles dynamically.
   ```html
   <p [ngStyle]="{ 'color': isError ? 'red' : 'green' }">
     This is a dynamic style example.
   </p>
   ```

### Custom Attribute Directive
#### Directive Class (`highlight.directive.ts`):
```typescript
import { Directive, ElementRef, HostListener } from '@angular/core';

@Directive({
  selector: '[appHighlight]'
})
export class HighlightDirective {
  constructor(private el: ElementRef) {}

  @HostListener('mouseenter') onMouseEnter() {
    this.highlight('yellow');
  }

  @HostListener('mouseleave') onMouseLeave() {
    this.highlight('');
  }

  private highlight(color: string) {
    this.el.nativeElement.style.backgroundColor = color;
  }
}
```

#### Usage in Template (`app.component.html`):
```html
<p appHighlight>Hover over this text to see the highlight effect.</p>
```

### How It Works
- The directive is applied as an attribute (`appHighlight`) to the element.
- It listens to the `mouseenter` and `mouseleave` events to dynamically change the background color.

---

## 3. **Structural Directives**

### Definition
- Structural directives alter the structure of the DOM by adding or removing elements.
- They use the `*` prefix to indicate they are structural.

### Common Structural Directives
1. **`ngIf`**
   - Conditionally includes or excludes an element.
   ```html
   <div *ngIf="isLoggedIn; else loginTemplate">
     Welcome, user!
   </div>
   <ng-template #loginTemplate>
     <p>Please log in.</p>
   </ng-template>
   ```

2. **`ngFor`**
   - Loops through a collection and renders elements dynamically.
   ```html
   <ul>
     <li *ngFor="let item of items">{{ item }}</li>
   </ul>
   ```

3. **`ngSwitch`**
   - Adds or removes DOM elements based on a switch condition.
   ```html
   <div [ngSwitch]="viewMode">
     <p *ngSwitchCase="'list'">List View</p>
     <p *ngSwitchCase="'grid'">Grid View</p>
     <p *ngSwitchDefault>Default View</p>
   </div>
   ```

### Custom Structural Directive
#### Directive Class (`unless.directive.ts`):
```typescript
import { Directive, Input, TemplateRef, ViewContainerRef } from '@angular/core';

@Directive({
  selector: '[appUnless]'
})
export class UnlessDirective {
  @Input() set appUnless(condition: boolean) {
    if (!condition) {
      this.vcRef.createEmbeddedView(this.templateRef);
    } else {
      this.vcRef.clear();
    }
  }

  constructor(private templateRef: TemplateRef<any>, private vcRef: ViewContainerRef) {}
}
```

#### Usage in Template:
```html
<p *appUnless="isHidden">This text is visible only when isHidden is false.</p>
```

### How It Works
- The directive controls whether to create or remove its host element in the DOM based on the `appUnless` condition.

---

## Summary Table
| Directive Type          | Purpose                          | Example                |
|-------------------------|----------------------------------|------------------------|
| **Component Directive** | Encapsulates UI logic and view.  | `<app-root></app-root>`|
| **Attribute Directive** | Alters behavior or appearance.  | `[ngClass]`, `[ngStyle]`|
| **Structural Directive**| Modifies DOM structure.          | `*ngIf`, `*ngFor`      |

---

Angular directives provide powerful tools to create dynamic and interactive web applications. They enable developers to extend HTML's functionality and create reusable, maintainable components. Understanding the three types of directives is essential for building robust Angular applications.
