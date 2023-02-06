# React coding 


## Table of contents

* [React coding style guide](#react-coding-style-guide)
  * [Naming](#naming)
  * [Common Rules](#common-rules)

## React coding style guide

### Naming

The name of files and folders for React Components.

**React UI component’s names should be PascalCase**

```
LoginScreen.[js/ts]x
```

**All other helper files should be camelCase. (non-component files)**

```
commonUtils.js
```

**All the folder names should be camelCase.**

```
components
```

**CSS files should be named the same as the component PascalCase. Global CSS which applies to all components should be placed in global.css and should be named in camelCase.**

```
LoginScreen.css(for components)
global.css(for global styles)
```

**Test files should be named the same as the component or non-component file.**

```
LoginScreen.[test/spec/cy].js
commonUtils.[test/spec/cy].js
```

## Common Rules

* Use the DRY principle (Don't repeat yourself).

* Create multiple files instead of writing a big file. (Componentization of code: fix to small functionality for each file).

* Place all your CSS files in one common folder.

* Avoid Inline CSS as and when possible (a CSS class should be created when there are more than 2 CSS attributes).

* Use a linter to make your code easier to review. Follow strict linting rules. This in turn helps you write clean, consistent code.

* Review your code before creating a pull request.

* Split your code into multiple smaller functions. Each with a single responsibility.

* Create many utility files that can help you remove duplicate code from multiple files.

* Separate all your service calls into a separate file. If it’s a big project try to split the services into multiple files.

* Name your files logically according to the job that they perform.

* Clean code is self-commenting(using the right variable names and function names). Use comments only to explain complex functions.

* Always write test cases for your code. Keep tests files in sync with the files they are testing.

* Destructuring your props is a good way to help make your coder cleaner and more maintainable.

```js
function authenticate({ user_id, token }) {}
```

* Putting imports in an order
  1. React import
  2. Library imports (Alphabetical order)
  3. Absolute imports from the project (Alphabetical order)
  4. Relative imports (Alphabetical order)
  5. Import * as
  6. Import ‘./<some file>.<some extension>

Each kind should be separated by an empty line. This makes your imports clean and easy to understand for all the components, 3rd-party libraries, and etc.

* Use index file for each folder to export (Avoid repeating names on the imports)