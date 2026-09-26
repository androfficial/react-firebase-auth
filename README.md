# Firebase Auth

Email and password registration and sign-in through Firebase Authentication, with a home page that only signed-in users see. Built in March 2022 as a learning project.

## Features

- Registration at `/register` with an email and a password, followed by a redirect to the home page.
- Sign-in at `/login` with an email and a password. A failed sign-in shows an alert.
- The home page greets the signed-in user and has a log out button that shows their email. Visitors who are not signed in are redirected to `/login`.
- Links between the login and registration pages.

## Tech stack

- **Framework:** React 17, TypeScript 4
- **State:** Redux Toolkit 1, React Redux 7
- **Routing:** React Router 6
- **Styling:** Tailwind CSS 3
- **Backend:** Firebase 9 Authentication (modular SDK)
- **Tooling:** Create React App 5 with react-app-rewired 2, ESLint 8 (Airbnb TypeScript config), Prettier 2

## Getting started

Requires Node.js 16 or 18, Yarn 1 and a Firebase project with a web app and the Email/Password sign-in provider enabled.

```bash
git clone https://github.com/androfficial/react-firebase-auth.git
cd react-firebase-auth
yarn install
yarn start
```

`src/firebase.ts` reads the Firebase web app config from these variables. Before `yarn start`, put them in a `.env` file in the project root:

| Variable | Purpose |
| --- | --- |
| `REACT_APP_FIREBASE_API_KEY` | Firebase config `apiKey` |
| `REACT_APP_FIREBASE_AUTH_DOMAIN` | Firebase config `authDomain` |
| `REACT_APP_FIREBASE_PROJECT_ID` | Firebase config `projectId` |
| `REACT_APP_FIREBASE_STORAGE_BUCKET` | Firebase config `storageBucket` |
| `REACT_APP_FIREBASE_MESSAGING_SENDER_ID` | Firebase config `messagingSenderId` |
| `REACT_APP_FIREBASE_APP_ID` | Firebase config `appId` |

## Scripts

| Command | Description |
| --- | --- |
| `yarn start` | Starts the development server |
| `yarn build` | Builds the production bundle into `build/` |
| `yarn eslint` | Lints the `.ts` and `.tsx` files |
| `yarn eslint:fix` | Lints the `.ts` and `.tsx` files and fixes what it can |
| `yarn format` | Checks formatting with Prettier |
| `yarn format:fix` | Formats the files with Prettier |

## Project structure

```text
src/
  components/  shared email and password Form, SignIn, SignUp
  hooks/       typed Redux hooks and useAuth
  pages/       Home, Login, Registration
  store/       Redux Toolkit store and the user slice
  styles/      Tailwind CSS entry file
  types/       Create React App type references
  firebase.ts  Firebase app setup from the environment variables
```

## Notes

- The signed-in user (id, email and refresh token) is kept in a Redux Toolkit slice, and the `useAuth` hook derives the signed-in state from it for the route guard on the home page.
