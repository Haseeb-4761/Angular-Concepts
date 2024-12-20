# How to Create a Component Using Angular CLI

Angular CLI provides a convenient way to generate components for your Angular application. Follow the steps below to create a new component:

---

## Step 1: Open Terminal

1. Open a terminal or command prompt.
2. Navigate to your Angular project directory:
   ```bash
   cd path/to/your/angular/project
   ```

---

## Step 2: Run the Generate Command

1. Use the Angular CLI `generate` command to create a new component:
   ```bash
   ng generate component component-name
   ```

   - Replace `component-name` with your desired component name.
   - The Angular CLI will create the necessary files and update the module automatically.

2. Alternatively, you can use the shorthand command:
   ```bash
   ng g c component-name
   ```

---

## Step 3: Specify a Path (Optional)

If you want to create the component in a specific folder, include the path in the command:

```bash
ng g c folder-name/component-name
```

For example, to create a component named `header` inside a `shared` folder:
```bash
ng g c shared/header
```

---

## Step 4: Verify Generated Files

The CLI generates the following files in the specified directory:

1. `component-name.component.ts` - Component logic file.
2. `component-name.component.html` - Component template.
3. `component-name.component.css` (or `.scss`) - Component styles.
4. `component-name.component.spec.ts` - Unit test file.

Additionally, the CLI updates the `AppModule` (or relevant module) to declare the new component.

---

## Step 5: Use the Component

1. Add the component's selector to your desired template file:

   - Open `component-name.component.ts` to find the selector:
     ```typescript
     selector: 'app-component-name',
     ```

   - Use the selector in another component's template (e.g., `app.component.html`):
     ```html
     <app-component-name></app-component-name>
     ```

2. Save your changes and view the component in the browser.

---

## Additional Options

You can use flags with the `ng generate component` command for more control:

- **--inline-template**: Generate the component with an inline template.
  ```bash
  ng g c component-name --inline-template
  ```

- **--inline-style**: Generate the component with inline styles.
  ```bash
  ng g c component-name --inline-style
  ```

- **--skip-tests**: Skip generating the spec file.
  ```bash
  ng g c component-name --skip-tests
  ```

---

## Example

To create a `footer` component with SCSS styles and no test file:

```bash
ng g c footer --style scss --skip-tests
```

This command generates a `footer` component with:
- SCSS styling.
- No unit test file.

---

## Resources

- [Angular CLI Documentation](https://angular.io/cli)
- [Angular Components Overview](https://angular.io/guide/component-overview)
