# React-Reducer Example

[:point_right: Click here to see on browser](https://react-use-reducer-rho.vercel.app/)

![React useReducer](https://github.com/kaplanh/react-useReducer/assets/101884444/b5f70174-ae54-4c05-8f9d-37d0abeb8c96)



---

| **What's used in this app ?**                                                      | **How use third party libraries** | **Author**                                                    |
| ---------------------------------------------------------------------------------- | --------------------------------- | ------------------------------------------------------------- |
| [useState Hook](https://react.dev/learn#using-hooks)                               |                                   | [Take a look at my portfolio](https://kaplanh.github.io/Portfolio_with_CssFlex/)                                                                                 |
| [fetch API](https://www.npmjs.com/package/react-fetch)         | npm i/yarn add axios              |     [Visit me on Linkedin](https://www.linkedin.com/in/kaplan-h/)                                                                              |
| [react-events](https://react.dev/learn#responding-to-events)                            |                                   |                                                                                  |
| [Semantic-Commits](https://gist.github.com/joshbuchea/6f47e86d2510bce28f8e7f42ae84c716) |                                   |                                                                                  |
| Deploy with [Vercel](https://vercel.com/kaplanh)                                        |                                   |                                                                                  |
| API [thecatapi](https://api.thecatapi.com/v1/images/search)      |                                   |                                                                                  |

---

## How To Run This Project 🚀

<br/>

### 💻 Install React 👇

```bash
yarn create react-app .  or npx create-react-app .
```

### 💻 Install Sass 👇

```bash
yarn add sass  or npm i sass
```

## 🔴 Delete these files and delete the imports👇

    - App.test.js
    - reportWebVitals.js
    - setupTests.js
    - favicon.ico
    - logo192.png
    - logo512.png
    - manifest.json
    - robots.txt

### 💻 Start the project 👇

```bash
yarn start or npm start
```

OR

-   <strong>Clone the Repo</strong>

    ```sh
    git clone
    ```

-   <strong>Install NPM packages</strong>

    ```sh
    npm install or yarn
    ```

-   <strong>Run the project</strong>

    ```sh
    npm start or yarn start
    ```

-   <strong>Open the project on your browser</strong>

    ```sh
    http://localhost:3000/
    ```

-   ### <strong>Enjoy! 🎉</strong>

---

## Project Skeleton

```
 reaact reducer-example(folder)
|
|----public (folder)
│     └── index.html
|----src (folder)
│    │
|    |
|    |
|    |
│    ├--- App.js
│    ├--- UseReducerExample.js
│    ├--- UseStateExample.js
│    |--- index.js
│    |--- reducer.js
│
│
|── .gitignore
|── package-lock.json
├── package.json
|── README.md
|── yarn.lock


```

---

### At the end of the project, the following topics are to be covered;

- React Reducer

```jsx
//reducer.js
export const initialState = {
  loading: false,
  catImage: "",
  error: "",
}

//? Pure Js fonksiyonu
export const reducer = (initialState, action) => {
  switch (action.type) {
    case "START":
      return { ...initialState, loading: true }
    case "SUCCESS":
      return {
        ...initialState,
        catImage: action.payload,
        error: "",
        loading: false,
      }
    case "FAIL":
      return {
        ...initialState,
        catImage: "",
        error: action.payload,
        loading: false,
      }
    default:
      break
  }
}

//? action
//!  {type: "SUCCESS", payload: catImage }
//! {type: "START" }

//UseReducerExample.js
import { useReducer } from "react"
import { initialState, reducer } from "./reducer"

const UseReducerExample = () => {
  const [state, dispatch] = useReducer(reducer, initialState)

  //? destr.
  const { loading, error, catImage } = state

  const getCatImage = async () => {
    const url = "https://api.thecatapi.com/v1/images/search"

    dispatch({ type: "START" })
    try {
      const res = await fetch(url)
      const data = await res.json()

      //? Consuming
      dispatch({ type: "SUCCESS", payload: data[0].url })
    } catch (error) {
      dispatch({ type: "FAIL", payload: "DATA CAN NOT BE FETCHED" })

      console.log(error)
    }
  }

  return (
    <div>
      <button
        onClick={getCatImage}
        disabled={loading}
        style={{ display: "block", margin: "1rem" }}
      >
        Get Cat Image
      </button>
      {error && <h2>{error}</h2>}
      {catImage && <img width="50%" src={catImage} alt="img" />}
    </div>
  )
}

export default UseReducerExample


```


-   Semantic Commit Messages
    See how a minor change to your commit message style can make you a better programmer.

    Format: <type>(<scope>): <subject>

    <scope> is optional

    -   Example

    ```
                feat: add hat wobble
        ^--^  ^------------^
        |     |
        |     +-> Summary in present tense.
        |
        +-------> Type: chore, docs, feat, fix, refactor, style, or test.
    ```

-   More Examples:
    -   `feat`: (new feature for the user, not a new feature for build script)
    -   `fix`: (bug fix for the user, not a fix to a build script)
    -   `docs`: (changes to the documentation)
    -   `style`: (formatting, missing semi colons, etc; no production code change)
    -   `refactor`: (refactoring production code, eg. renaming a variable)
    -   `test`: (adding missing tests, refactoring tests; no production code change)
    -   `chore`: (updating grunt tasks etc; no production code change)

---

## Feedback and Collaboration

I value your feedback and suggestions. If you have any comments, questions, or ideas for improvement regarding this project or any of my other projects, please don't hesitate to reach out.
I'm always open to collaboration and welcome the opportunity to work on exciting projects together.
Thank you for visiting my project. I hope you have a wonderful experience exploring it, and I look forward to connecting with you soon!

<p align="center"> ⌛<strong> Happy Coding </strong> ✍ </p>
