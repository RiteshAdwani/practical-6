# Practical-6(User-list-app)

- This repo consists the user-list-app with some code optimization and shows how to generate different builds for different environments.

---

## Why we use different environment variables?

- Different environment variables are used in generating different builds, such as production, staging, and development, to customize the behavior and configuration of the application for each environment.
- Here are some reasons why different environment variables are used:

**1. API endpoints:** In different environments, you may need to connect to different backend services or APIs. By using environment variables, you can specify the appropriate API endpoints for each environment without modifying the code.

**2. Credentials and sensitive information:** Different environments may require different credentials or sensitive information, such as database connection strings, API keys, or authentication tokens. Using environment variables allows you to securely manage and provide these sensitive values specific to each environment.

**3 Feature flags:** Environment variables can be used to enable or disable specific features of the application based on the environment. For example, you may want to enable additional debugging features in the development environment that are not necessary in the production environment.

**4 Logging and error reporting:** Environment variables can be used to configure different logging settings or error reporting mechanisms for each environment. This helps in distinguishing and handling errors differently in different environments.

**5 Optimizations and performance:** Environment-specific configurations, such as caching strategies, CDN (Content Delivery Network) URLs, or asset optimizations, can be defined using environment variables. This allows you to optimize performance based on the specific requirements of each environment.

- By using different environment variables, you can ensure that your application is configured correctly for each environment without making code changes. This promotes consistency, flexibility, and easier deployment across different environments.

---

## To set up environment variables in a Vite React project, you can follow these steps:

- Create a .env file in the root of your project. You can name this file `.env.development` for development-specific variables or `.env.production` for production-specific variables or `.env.staging` for testing-specific variable.

- Add your environment variables to the .env file in the following format: VARIABLE_NAME=variable_value.
- To prevent accidentally leaking env variables to the client, only variables prefixed with VITE\* are exposed to your Vite-processed code.
  For example: VITE_SOME_KEY=123

- In your code, you can access the environment variables using the import.meta.env object.
  For example: console.log(import.meta.env.VITE_SOME_KEY)

## How to run and generate different builds:

- Clone this repo and run `npm install` to install all packages.

**1. Development Build**

- To run this project in development mode, go to project directory in terminal and run this command:
  `npm run dev`

**2. Staging Mode**

- To run and see this project in Staging mode follow the below steps:

**step 1 :**

- Create .env.staging file in root folder write below code

```
VITE_APP_BUILD_NAME = "staging build"
```

**step 2:**

- In the package.json file, go to scripts and add this line:

```
"build:staging": "vite build --mode staging"
```

**step 3 :**

- Go to terminal and write this command
  `npm run build:staging`

- This will generate staging build of your code.

**step 4 :**

- To serve this build first install serve package and serve build.
- `npm install serve` : It is a command used to install the serve package from the npm registry. The serve package is a simple, zero-configuration command-line http server that can be used to serve static files from a directory.
- Then go to dist folder and serve build.

```
cd dist
serve -s
```

**3. Production Mode**

- To run and see this project in production mode follow bellow steps:

**step 1 :**

- Create .env.production file in root folder write below code:

```
VITE_APP_BUILD_NAME = "production build"
```

**step 2 :**

- Go to terminal and write this command
  `npm run build`

- This will generate Production build of your code.

**step 3 :**

- To serve this build first install serve package and serve build.

- Then go to dist folder and serve build.

```
cd dist
serve -s
```
