# Deploying a React Project Created with Vite on GitHub Pages

Follow these steps to deploy your React project created using Vite to GitHub Pages.

## 1. Set Up Your Project

Ensure your React project is ready for deployment. If you haven't already, initialize your project with Vite:

```js
npm create vite@latest my-react-app --template react
cd my-react-app
npm install
```

### 2. Update vite.config.js

In your vite.config.js file, add the base option. This is necessary because GitHub Pages serves your project from a subdirectory **(/your-repo-name/)**, not from the root (/).

```js
// vite.config.js
import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";

export default defineConfig({
  plugins: [react()],
  base: "/your-repo-name/", // Replace 'your-repo-name' with your GitHub repository name
});
```

### 3. Build the Project

Run the build command to generate the static files:

```js
npm run build
```

This will create a dist folder containing your compiled project.

### 4. Install gh-pages

You need to install the gh-pages package to deploy the dist folder to GitHub Pages:

```js
npm install gh-pages --save-dev
```

### 5. Update package.json

In your package.json file, add the following **homepage** and **deploy** script:

```json
{
  "name": "my-react-app",
  "version": "0.0.0",
  "private": true,
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview",
    "deploy": "gh-pages -d dist"
  },
  "homepage": "https://your-username.github.io/your-repo-name/", // Replace with your GitHub username and repo name
  "dependencies": {
    // other dependencies
  },
  "devDependencies": {
    // other dev dependencies
    "gh-pages": "^3.2.3"
  }
}
```

### 6. Deploy to GitHub Pages

Deploy your project to GitHub Pages by running:

```js
npm run deploy
```

This command will create a gh-pages branch in your repository and push the contents of the dist folder to it.

### 7. Verify Deployment

Go to https://your-username.github.io/your-repo-name/ to see your deployed React app.

### 8. Set Up GitHub Pages

If it's your first time deploying to GitHub Pages, make sure to enable GitHub Pages in your repository settings:

    1. Go to your repository on GitHub.
    2. Click on the "Settings" tab.
    3. Scroll down to the "Pages" section.
    4. Under "Branch," select gh-pages and /root as the source.
    5. Save your changes.
    6. Your site should be live after a few minutes.
