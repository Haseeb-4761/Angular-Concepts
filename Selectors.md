# Types of Component Selectors in Angular

In Angular, the selector is a key property in a component's metadata that defines how the component can be used in templates. There are four types of selectors supported by Angular:

---

## 1. **Element Selector**

- The most common type of selector.
- It allows the component to be used as a custom HTML element.
- Syntax: A simple string with a name, e.g., `app-header`.

### Example

In the component's metadata:
```typescript
@Component({
  selector: 'app-header',
  templateUrl: './header.component.html',
  styleUrls: ['./header.component.css']
})
export class HeaderComponent {}
```

In the template:
```html
<app-header></app-header>
```

---

## 2. **Attribute Selector**

- Allows the component to be applied to an existing HTML element via an attribute.
- Syntax: `[attribute-name]`.

### Example

In the component's metadata:
```typescript
@Component({
  selector: '[app-highlight]',
  template: '<p>Highlighted content!</p>',
  styleUrls: ['./highlight.component.css']
})
export class HighlightComponent {}
```

In the template:
```html
<div app-highlight></div>
```

---

## 3. **Class Selector**

- Allows the component to be applied to an element using a CSS class.
- Syntax: `.class-name`.

### Example

In the component's metadata:
```typescript
@Component({
  selector: '.app-card',
  template: '<div>Card content</div>',
  styleUrls: ['./card.component.css']
})
export class CardComponent {}
```

In the template:
```html
<div class="app-card"></div>
```

---

## 4. **ID Selector**

- Allows the component to be applied to an element using an ID.
- Syntax: `#id-name`.

### Example

In the component's metadata:
```typescript
@Component({
  selector: '#app-unique',
  template: '<p>Unique content</p>',
  styleUrls: ['./unique.component.css']
})
export class UniqueComponent {}
```

In the template:
```html
<div id="app-unique"></div>
```

---

## Choosing the Right Selector

| Selector Type     | Use Case                                                                 |
|-------------------|-------------------------------------------------------------------------|
| **Element**       | When creating reusable, standalone components like `<app-header>`.     |
| **Attribute**     | When enhancing or modifying the behavior of an existing HTML element.  |
| **Class**         | When styling or applying behavior to an element with a specific class. |
| **ID**            | When targeting a unique element with a specific ID.                    |

---

## Resources

- [Angular Components Overview](https://angular.io/guide/component-overview)
- [Selectors in Angular](https://angular.io/guide/component-selectors)
