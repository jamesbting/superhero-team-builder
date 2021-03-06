## Set up

This set up guide is written assuming you already have a working version of nodeJS installed. If you don't install it here: https://nodejs.org/en/download/
To set up this project, first clone the repository

```bash
$ git clone https://github.com/jamesbting/fundmore-challenge.git
```

Change your working directory into the project directory

```bash
$ cd superhero-app
```

## Run

Install npm modules

```bash
$ npm install
```

Start the application

```bash
$ npm start
```

## Dependencies

Before starting the application, you must install the following dependencies.
Dependencies: material-ui/core, material-ui/icons, lodash, react-helmet

To install material-ui, type the following into the command line:

```bash
npm install @material-ui/core
```

```bash
npm install @material-ui/icons
```

```bash
npm i --save lodash
```

```bash
npm install --save react-helmet
```

Note: If you receive the error:

"Warning: Using UNSAFE_componentWillMount in strict mode is not recommended and may indicate bugs in your code. See https://fb.me/react-unsafe-component-lifecycles for details.

Move code with side effects to componentDidMount, and set initial state in the constructor.

Please update the following components: SideEffect(NullComponent)"

it is the result of an external dependence using componentWillMount(), and running the following command should resolve the issue (https://stackoverflow.com/questions/58891130/how-to-find-out-which-package-is-using-the-unsafe-componentwillmount-method). However, this error should have no impact on the performance of my application.

```bash
npm install --save react-helmet@^6.0.0-beta.2
```

## IMPORTANT NOTES BEFORE FIRST START:

To prevent my API key from being released in the wild, you **must** create a file name ".env" in the root folder of this repository in the with the following contents:

REACT_APP_API_KEY=123456

where instead of 123456, you would put your own personal API key. Since this app is not meant for production, this solution should suffice. See my notes below about why this is a bad idea. Without this file, your app will say no superheroes are found, even for valid superhero names.

## Notes about the design

1. Single-view vs. Multi-view

   While the requirements imply that the superhero details and the team should be on different pages, when I used my own application and after thinking about it, since it is a team builder, I felt it would be better to show them on the same page, so the user will be able to compare the superheroes that were searched to the ones that are currently on the team. While this is probably against the requirements, in my opinion it would be better since the user will be able to see the differences between their team members and the search results, an important consideration for a team builder app.

   Since I modified the code to be a multi-view application, here is an example of the single view version in action: https://gfycat.com/unconsciousincompleteicefish

2. API Keys

   Since this is a front-end only app, there is no backend to store API keys completely hidden from view. Obviously having the API key hardcoded into the app is a terrible idea, since anyone with access to the source code will be able to use it freely. Therefore, I choose to store my API key as an environment variable of the development server. In production, you should not do this either, since anyone who inspects the production files will be able to determine your API key. However, since this is only for a coding challenge and not an actually deployed application, this solution should suffice.

   In a production environment, I would have my application's back end handle all the API requests and the management of the API key, thus keeping the API key a secret. (https://stackoverflow.com/questions/48699820/how-do-i-hide-api-key-in-create-react-app)

3. PropTypes
   I use PropTypes to enforce Design by Contract

## Known issues:

1. Unique key prop
   index.js:1 Warning: Each child in a list should have a unique "key" prop.

Check the render method of `ResultItem`. See https://fb.me/react-warning-keys for more information.
in WithStyles(ForwardRef(Typography)) (at ResultItem.jsx:175)
in ResultItem (at Result.jsx:100)
in div (created by ForwardRef(Paper))
in ForwardRef(Paper) (created by WithStyles(ForwardRef(Paper)))
in WithStyles(ForwardRef(Paper)) (at Result.jsx:98)
in div (at Result.jsx:96)
in Result (at SuperHeroApp.jsx:140)
in div (at SuperHeroApp.jsx:139)
in div (at SuperHeroApp.jsx:138)
in SuperHeroApp (at App.js:14)
in div (at App.js:8)
in App (at src/index.js:9)
in StrictMode (at src/index.js:8)

Cause:
Using `<Typography></Typography>` inside of .map() in order to list the stats on separate lines
Fixes:
Removing the `<Typography></Typography>` suppresses the warning, but then the stats are listed as a paragraph.
Listing each element also suppresses the warning, but then the code becomes less maintainable/extensible

## Things I would've liked to add:

1. A suggestion system for search queries
2. Instead of using the alert() function, displaying a message on screen that says the same message
3. Different messages for the API errors (i.e. timeout message, too many requests message,superhero not found message etc.)
4. Back to top button that would bring the user to the top of the page

----------------------------The text below this line was generated by npx--------------------------

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.<br />
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.<br />
You will also see any lint errors in the console.

### `npm test`

Launches the test runner in the interactive watch mode.<br />
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `npm run build`

Builds the app for production to the `build` folder.<br />
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.<br />
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `npm run eject`

**Note: this is a one-way operation. Once you `eject`, you can’t go back!**

If you aren’t satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you’re on your own.

You don’t have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn’t feel obligated to use this feature. However we understand that this tool wouldn’t be useful if you couldn’t customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

### Code Splitting

This section has moved here: https://facebook.github.io/create-react-app/docs/code-splitting

### Analyzing the Bundle Size

This section has moved here: https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size

### Making a Progressive Web App

This section has moved here: https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app

### Advanced Configuration

This section has moved here: https://facebook.github.io/create-react-app/docs/advanced-configuration

### Deployment

This section has moved here: https://facebook.github.io/create-react-app/docs/deployment

### `npm run build` fails to minify

This section has moved here: https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify
