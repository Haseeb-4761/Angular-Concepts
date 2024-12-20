# How to Create an Angular App

Angular is a powerful framework for building dynamic web applications. Follow the steps below to create your first Angular app.

---

## Prerequisites

Before starting, ensure you have the following installed on your system:

1. **Node.js and npm**  
   Download and install Node.js from [https://nodejs.org/](https://nodejs.org/). npm is included with Node.js.

   Verify installation:

   ```bash
   node -v
   npm -v
   ```

2. **Angular CLI**  
   Install the Angular Command Line Interface (CLI) globally:
   ```bash
   npm install -g @angular/cli
   ```
   Verify installation:
   ```bash
   ng version
   ```

---

## Step 1: Create a New Angular App

1. Open a terminal or command prompt.
2. Navigate to the directory where you want to create your project.
   ```bash
   cd path/to/your/directory
   ```
3. Use the Angular CLI to create a new app:

   ```bash
   ng new my-angular-app
   ```

   - Replace `my-angular-app` with your desired app name.
   - You will be prompted to choose routing and styles (CSS, SCSS, etc.). Make your selections as needed.

4. Navigate to the newly created project directory:
   ```bash
   cd my-angular-app
   ```

---

## Step 2: Serve the Application

1. Run the following command to serve your application:
   ```bash
   ng serve
   ```
2. Open your browser and navigate to [http://localhost:4200/](http://localhost:4200/) to view your app.

---

## Step 3: Modify the App

1. Open the project in your preferred code editor (e.g., Visual Studio Code):

   ```bash
   code .
   ```

2. Modify the `src/app/app.component.html` file to change the content displayed on the homepage.

---

## Step 4: Build the Application for Production

1. Use the Angular CLI to build your app for production:
   ```bash
   ng build --prod
   ```
2. The built files will be in the `dist/my-angular-app` directory.

---

## Step 5: Deploy the Application

You can deploy your Angular app to various platforms, such as:

- **GitHub Pages**: Use the Angular CLI's `ng deploy` command.
- **Firebase Hosting**: Follow Firebase's hosting setup.
- **Other Hosting Services**: Upload the contents of the `dist/my-angular-app` directory to your preferred hosting platform.

---

## Additional Resources

- [Angular Documentation](https://angular.io/docs)
- [Angular CLI Reference](https://angular.io/cli)
- [Deploy Angular Apps](https://angular.io/guide/deployment)
