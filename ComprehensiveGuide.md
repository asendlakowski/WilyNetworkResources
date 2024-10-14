# Comprehensive Wily Network Development Guide

<style>
  /* Rule element for team rules */
  Rule {
    display: block;
    font-weight: bold;
    color: #CB3048;

    border: 0.15rem solid #CB3048;
    border-top-left-radius: 0.3rem; border-top-right-radius: 0.3rem;

    padding-top: 0.2rem;
    padding-bottom: 0.2rem;
    padding-left: 0.5rem;
    padding-right: 0.5rem;
  }
  Rule::before {
    content: '\2605  Rule: ';
    font-weight: normal;
  }
  
  /* <Rule tall> for rules that don't have a following pre with explanation */
  Rule[tall] {
    margin-bottom: 0.7rem;
    border-bottom-left-radius: 0.3rem;
    border-bottom-right-radius: 0.3rem;
  }

  /* Extend rule border around following pre with explanation */
  Rule + .highlighter-rouge pre {
    border-bottom: 0.15rem solid #CB3048;
    border-left: 0.15rem solid #CB3048;
    border-right: 0.15rem solid #CB3048;

    border-top-left-radius: 0 !important;
    border-top-right-radius: 0 !important;
    border-bottom-left-radius: 0.3rem;
    border-bottom-right-radius: 0.3rem;
  }

  /* Exercise block with an assignment */
  Exercise {
    display: block;
    font-weight: bold;
    color: #54d2e2;

    background-color: white;
    position: relative;
    z-index: 10;

    border: 0.15rem solid #54d2e2;
    border-top-left-radius: 0.3rem; border-top-right-radius: 0.3rem;

    padding-top: 0.2rem;
    padding-bottom: 0.2rem;
    padding-left: 0.5rem;
    padding-right: 0.5rem;
  }
  Exercise::before {
    content: '\270F  Exercise: ';
    font-weight: normal;
  }

  /* <Exercise tall> for exercises that aren't followed by a pre with explanation */
  Exercise[tall] {
    margin-bottom: 0.7rem;
    border-bottom-left-radius: 0.3rem;
    border-bottom-right-radius: 0.3rem;
  }

  /* Extend exercise border around following pre with explanation */
  Exercise + .highlighter-rouge pre {
    border-bottom: 0.15rem solid #54d2e2;
    border-left: 0.15rem solid #54d2e2;
    border-right: 0.15rem solid #54d2e2;

    border-top-left-radius: 0 !important;
    border-top-right-radius: 0 !important;
    border-bottom-left-radius: 0.3rem;
    border-bottom-right-radius: 0.3rem;
  }

  /* Example response extend below exercise as a visual add-on */
  details {
    margin-left: 1em;
    margin-right: 1em;

    position: relative;

    transform: translate(0, -1rem);

    padding-left: 0.5rem;
    padding-right: 0.5rem;
    padding-top: 0.3rem;
    padding-bottom: 0.3rem;
    
    background-color: #54d2e2;

    border-bottom: 0.15rem solid #54d2e2;
    border-left: 0.15rem solid #54d2e2;
    border-right: 0.15rem solid #54d2e2;

    border-bottom-left-radius: 0.3rem;
    border-bottom-right-radius: 0.3rem;
  }

  /* Fix spacing below pre inside of example */
  details pre {
    margin-bottom: 0.3rem !important;
  }

  /* Bold, white text for example title */
  summary {
    text-align: center !important;
    font-weight: bold;
    color: white;
  }

  /* Highlight color for code inside of example that's important <b>code</b> */
  details b {
    font-weight: bold;
    color: #d14;
  }

  /* Boxes around main titles */
  h1 {
    border-radius: 0.5rem;
    background-color: #333;
    color: white;
    padding-bottom: 0.5rem;
    padding-left: 0.7rem;
    padding-right: 0.7rem;
    padding-top: 0.5rem;
  }

  /* Hide footer */
  .footer {
    display: none;
  }

  /* Wrap text in text-based pre tags */
  pre[text] {
    white-space: pre-wrap;
  }
</style>

# Table of Contents

Getting Set Up:

- [Set Up Your Workspace](#set-up-your-workspace)

Programming and Testing:

- [Project and File Management](#project-and-file-management)
- [Typescript Basics](#typescript-basics)
- [Typescript Advanced Stuff](#typescript-advanced-stuff)
- [React](#react)

# Set Up Your Workspace

1. Install [Node.js](https://nodejs.org/en) (v20 or later) and npm.
2. Install the Vercel CLI (`npm install --global vercel`).
3. Copy this repo as a template and clone it onto your local machine.
4. Install all required packages by running `npm install`.
5. Start the dev server with `vercel dev` (log in with your Vercel account and create a linked project as required).

# Project and File Management

## Assigned Tasks

We use GitHub Issues as our task management system. To see what you're assigned, visit the repo, click `Issues`, and filter by your name.

When you start working on a task, remove the 'assigned' tag and add the 'in progress' tag. 

When you finish a task and have a PR up, update the tag to `ready for review`.

Alana and Avery will review your work before moving your card to `Done`.

## GitHub

The main branch of the project is managed by Alana and Avery, so please do not merge directly into `main`. Instead, you should be merging to a branch you make for your ticket.

<Rule tall>
  Never commit, merge, or push to main
</Rule>

Before starting to work on new tickets, create a new branch labeled `<initials>-<partner-initials>/<lowercase-dashed-ticket-description>`.

<Rule>
  One branch per ticket
</Rule>


```bash
git checkout main
git pull
git checkout -b as-ah/adding-student-page
```

Please rebase before pushing your code, and make sure to go through any merge conflicts that come up

<Rule>
  Rebase before pushing your code
</Rule>

```bash
# Always commit before you rebase
git add .
git commit -m "Adding Alana's student page"
git checkout main
git pull
git checkout <branch-name>
git rebase main
```

Fix any merge conflicts fron the rebase and then 
```bash
# Always push after you commit
git add .
git commit -m "description of what you did"
git push
```

When done with your ticket, submit a pull request to `main` and describe anything you think we need to know for the code. Finally, request a review from Alana and Avery.

## File Management

We use a strict file structure for all our projects. This helps us get around each other's code and greatly improves modularity and encourages code reuse.

Modules can take one of two structures: one/two files or folder. A module must be a folder if it has any helpers, sub-components, or more than two files for any other reason. There is one exception to this: test files are not included in this count, so you may end up with three files instead of a folder if one of them is a test.

<Rule>
  Modules must be folders if they have helpers, sub-components, or more than 2 files
</Rule>

```ts
// Allowed: 
MyComponent.tsx
MyComponent.scss

// BUT MUST BE A FOLDER...

// If there are 3+ files:
MyComponent/
  index.tsx
  style.scss
  logo.png

// OR

// If there are helpers:
MyComponent/
  index.tsx
  helpers/
    myHelper.tsx

// Or if there are sub-components:
MyComponent/
  index.tsx
  MySubComponent.tsx
  MySubComponent.scss
```

## Modules

Our npm projects are divided into modules. We use es6 import/export syntax.

### Creating a Module

To create a module, create a `.tsx` file and at the end of the file, on one line, export the item of interest as the default export.

<Rule>
  Default export must be at the end of the file
</Rule>

```ts
...

export default MyComponent;
```

The file name must match the name of the default export. This helps with consistency and helps with automatic documentation.

<Rule>
  Default export name must match file name
</Rule>

```ts
// Chart/index.tsx
export default MyComponent;

// MyButton.tsx
export default MyButton;
```

If an item takes up more than one line, define it above and then export it on one line.

<Rule>
  Export must be on a single line
</Rule>

```ts
const MyCar = {
    ...
};

export default MyCar;
```

### Importing a Module

When importing a module, leave out the extension if it's a `.ts` or `.tsx` file.

<Rule>
  When importing, leave off extension if ".tsx"
</Rule>

```ts
import MyComponent from '../shared/MyComponent';
```

If a module is a folder, leave off `index.tsx` when importing.

<Rule>
  Leave off "index.tsx" when importing file modules
</Rule>

```ts
// File structure
MyComponent/
  index.tsx
  style.scss
  MyButton.tsx

// Bad:
import MyComponent from './MyComponent/index';

// Good:
import MyComponent from './MyComponent';
```

# Typescript Basics

## Types

### Primitives

- `number` - all number types (int, float, etc.)
- `string` - text of any length
- `boolean` - either true or false
- `undefined` - unset
- `null` - no value
- `void` - either `undefined` or `null` - but we refrain from using it except for with function return types

### Important Data Structures

- `Array` - array of elements
- `Map` - dictionary with keys and values
- `Set` - set where items can only exist once in the list
- `Object` - unordered map where keys must be strings

### Types and Enums

- `Type/Interface` - a data type/interface
- `Enum` - an enum (does not support dynamic keys or values that are objects)

<Exercise>
  Match each of the following values to their type
</Exercise>

```ts
const a = 5 < 10;
const b = 'Hanalei';
const c = [1, 7, 5];
const d = 27;
const e = { name: 'Gabe' };
const f = e.age;
```

<!-- Start Example -->
<details>
<summary>Example Result</summary>
<pre>
const a = 5 < 10; <b>// boolean</b>
const b = 'Hanalei'; <b>// string</b>
const c = [1, 7, 5]; <b>// number[]</b>
const d = 27; <b>// number</b>
const e = { name: 'Gabe' }; <b>// object, { [k: string]: string }</b>
const f = e.age; <b>// undefined</b>
</pre>
</details>
<!-- End Example -->

## Creating Variables

Use `const` when defining variables. Only use `let` if absolutely necessary (a variable's value changes). It is unforgivable to use `var`.

<Rule>
  Use const to define variables. Only use let if necessary
</Rule>

```ts
// Good
const name = 'Divardo';

// Good
const getName = () => { ... };

// Good only because age is modified later
let age = 10;
...
age += 1;
```

Object property modifications do **not** count as re-assigning:

```ts
// Still use const
const user = {
  name: 'Divardo',
  age: 10,
};

// These do not modify user
user.name = 'Jane';
user.age += 1;
```

An easy way to choose between `const` and `let` is simply to always start with `const` and only change it to `let` if the editor complains.

<Exercise>
  Fill in the let/const blank
</Exercise>

```ts
/**
 * Format a last name to indicate ownership (e.g. Calicci becomes Calicci's and Abrams becomes Abrams')
 * @author Gabe Abrams
 * @param lastName the last name of the person
 * @returns last name in ownership form
 */
____ genOwnershipForm = (lastName: any) => {
  // Last name that ends with "s" gets an apostrophe only
  if (lastName.endsWith('s')) {
    return `${lastName}'`;
  }

  // Other last names get "'s" suffix
  return `${lastName}'s`;
};

// Print account status
____ lastName = 'Calicci';
console.log(`This is ${genOwnershipForm(lastName)} laptop.`);

// Bonus points for finding other errors in the code
```

<!-- Start Example -->
<details>
<summary>Example Result</summary>
<pre>
/**
  * Format a last name to indicate ownership (e.g. Calicci becomes Calicci's and Abrams becomes Abrams')
  * @author Gabe Abrams
  * @param lastName the last name of the person
  * @returns last name in ownership form
  */
<b>const</b> genOwnershipForm = (lastName: <b>string</b>) => {
  // Last name that ends with "s" gets an apostrophe only
  if (lastName.endsWith('s')) {
    return `${lastName}'`;
  }

  // Other last names get "'s" suffix
  return `${lastName}'s`;
};

// Print account status
<b>const</b> lastName = 'Calicci';
console.log(`This is ${genOwnershipForm(lastName)} laptop.`);
</pre>
</details>
<!-- End Example -->

<Exercise>
  Fill in the let/const blank
</Exercise>

```ts
// Create a bank account
____ checking: BankAccount = {
  firstName: 'Gabe',
  lastName: 'Abrams',
  balance: 29,
};

// Deduct money from the account balance
checking.balance -= 10;
```

<!-- Start Example -->
<details>
<summary>Example Result</summary>
<pre>
// Create a bank account
<b>const</b> checking: BankAccount = {
  firstName: 'Gabe',
  lastName: 'Abrams',
  balance: 29,
};

// Deduct money from the account balance
checking.balance -= 10;
</pre>
</details>
<!-- End Example -->

We favor longer variable names that are descriptive: `mouseX` is better than `x`. When apps are bundled and built, variable names are minified anyway. Don't minimize number of chars, minimize confusion and ambiguity.

<Rule>
  Use appropriate naming conventions, be descriptive
</Rule>

```ts
// Variable:
favoriteFruits

// Constant:
FAVORITE_FRUITS // (all caps with underscores)

// Enum:
FavoriteFruit // (notice this is not pluralized)

// Typescript Class (not a css class):
FavoriteFruits

// Component:
FavoriteFruits

// CSS class:
.FavoriteFruits-container
```

If a variable is an optional boolean, always name it such that `false` is the default value. For example, if users are usually online while using the tool, an optional status boolean should be named `isOffline` so that `false` can be the default value (instead of `isOnline` where `true` is the default value). You'll really appreciate this consistency farther down the line and when reading other people's code. This is especially useful in React with optional boolean component props which are only added if the boolean is true (if the default is false, it saves a lot of useless extra code).

<Rule>
  Name optional booleans such that false is the default value
</Rule>

```ts
// If users are usually teachers...

// Bad:
const isNotStudent?: boolean = ...

// Good
const isStudent?: boolean = ...
```

<Exercise>
  Create better names for the following variables
</Exercise>

```ts
// NOTE: This class represents a user in the database
class customUser {
  ...
}

// NOTE: This css class is used in the component called "MyButton"
.button-label {
  ...
}

// NOTE: Comments are usually not included
let noComments = true;

// NOTE: User age is usually included
let userAgeKnown = false;
```

<!-- Start Example -->
<details>
<summary>Example Result</summary>
<pre>
// NOTE: This class represents a user in the database
class <b>CustomUser</b> {
  ...
}

// NOTE: This css class is used in the component called "MyButton"
.<b>MyButton-label</b> {
  ...
}

// NOTE: Comments are usually not included
let <b>commentsIncluded</b> = true;

// NOTE: User age is usually included
let <b>userAgeUnknown</b> = false;
</pre>
</details>
<!-- End Example -->

All variables must have types. If typescript cannot infer a type, one must be explicitly defined.

<Rule>
  All variables must have specific types (if not defined or inferred)
</Rule>

```ts
const name: string = getName();
// Note: always include a space before the type
```

All numbers must include units, either in the variable name itself or in a comment at the variable's declaration:

<Rule>
  All numbers must include units
</Rule>

```ts
// Good:
const heightFt = 5;
// or
const height = 5; // ft

// Bad:
const height = 5;
```

If you have the option to choose units, here are our preferred set of units:

- timestamp/time = ms
- age = years
- date = ms since epoch (number)
- video timestamp = seconds since start of video

<Exercise>
  Create acceptable names for the following variables
</Exercise>

```ts
// NOTE: This is the time since the user was last active
const lastActive = ...;

// NOTE: This is the time to wait before playing the next video
const videoDelay = 10;

// NOTE: This is the current "feels like" temperature outside
const feelsLike = 74;
```

<!-- Start Example -->
<details>
<summary>Example Result</summary>
<pre>
// NOTE: This is the time since the user was last active
const <b>lastActiveTimestamp</b> = ...;

// NOTE: This is the time to wait before playing the next video
const <b>videoDelaySec</b> = 10;

// NOTE: This is the current "feels like" temperature outside
const <b>feelsLikeDeg</b> = 74; <b>// Fahrenheit</b>
</pre>
</details>
<!-- End Example -->

We reserve single quotes for typescript and double quotes for JSX. This makes our code differentiable and nestable.

<Rule>
  Only use single quotes in typescript, reserve double quotes for jsx props
</Rule>

```ts
// Import other components
import toggleButton from 'toggle-button';

const name = 'Divardo';
```

Arrays that start off empty must have a declared type.

<Rule>
  Arrays must have declared types
</Rule>

```ts
const names: string[] = [];
```

Objects must be defined with proper spacing to preserve clarity.

<Rule>
  Space out object properties
</Rule>

```ts
// Good:
const user = { name: 'Divardo' };

// Bad:
const user = {name: 'Divardo'};
```

If adding a variable to an object with the same name, use shorthand.

<Rule>
  Used object property shorthand
</Rule>

```ts
const name = 'Divardo';
const age = 10;

// Good:
const user = { name, age };

// Bad:
const user = { name: name, age: age };
```

### Simple Operations

Always use `===` for equality. If you're using `==` there had better be a really good reason.

<Rule>
  Always use === or !== for equality comparisons ("==" is banned)
</Rule>

```ts
if (name === 'Divardo') {
    ...
}
```

Triple equals (`===`) compares type and value. Thus, `'5' === 5` is false.

If you want to compare just value and not type, convert the variables first: `Number.parseInt('5', 10) === 5`, which will now return true.

If you want to do a deep comparison of two objects, use a library.

Math must be readable and grouped. Only one operation can happen in each parentheses group.

<Rule>
  Wrap each mathematical operation in parentheses
</Rule>

```ts
const x = (((a + b) * (c + d)) / e);
```

It turns out few people understand the subtleties of `num++` or `num--`, so we do not use those operators except in for loops, where its use is well-understood.

<Rule>
  Only use ++ or -- in for loop declarations
</Rule>

```ts
// Bad:
age++;

// Good:
age += 1;
```

This works nicely with other mathematical operations:

- Add: `age += 2`
- Multiply: `age *= 3`
- Divide: `age /= 5`
- Subtract: `age -= 1`

<Exercise>
  Update this code to match our rules
</Exercise>

```ts
// Get the restaurant hours
const hours = await getHoursFromDB();

// Create restaurant info object
const restaurantInfo = {
  name: 'Dosa House',
  hours: hours,
};

// Create the order
const foodOrder = { timestampMs: 12093840982,
  cost: 12.78,
  restaurantInfo: restaurantInfo,
};

// Ask the user for a tip
const tip = await askUserForTip();

// Update the cost to include the tip
foodOrder.cost = (foodOrder.cost * (tip + 1));

// Add a dollar to the cost as a kitchen surcharge
foodOrder.cost++;
```

<!-- Start Example -->
<details>
<summary>Example Result</summary>
<pre>
// Get the restaurant hours
const hours = await getHoursFromDB();

// Create restaurant info object
const restaurantInfo = {
  name: 'Dosa House',
  <b>hours,</b>
};

// Create the order
const foodOrder = {
  <b>timestampMs: 12093840982,</b>
  cost: 12.78,<b> // USD</b>
  <b>restaurantInfo,</b>
};

// Ask the user for a tip
const tip = await askUserForTip();<b> // percent</b>

// Update the cost to include the tip
foodOrder.cost <b>*= (tip + 1)</b>;

// Add a dollar to the cost as a kitchen surcharge
foodOrder.cost <b>+= 1</b>;
</pre>
</details>
<!-- End Example -->

String addition must always be done using template strings.

<Rule>
  Only use template strings for string addition
</Rule>

```ts
const weather = `The temperature is ${temp} today`;
```

Never nest ternaries and always wrap them in parentheses, even if they're short.

<Rule>
  Never nest ternaries
</Rule>

```ts
// Bad:
const beingType = (age > 150 ? (allergy === 'sun' ? 'vampire' : 'zombie') : 'human');

// Good:
const monsterType = (allergy === 'sun' ? 'vampire' : 'zombie');
const beingType = (age > 150 ? monsterType : 'human');
```

<Rule>
  Put complex ternaries on multiple lines
</Rule>

```ts
// Bad
const carStatus = (miles > getCarMiles() ? `${make} is older than ${standard}` : 'new');

// Good
const carStatus = (
  miles > getCarMiles()
    ? `${make} is older than ${standard}`
    : 'new'
);
```

<Rule>
  Wrap multiline ternaries with parentheses, place condition on its own line
</Rule>

```ts
// Bad
const carStatus = miles > getCarMiles()
  ? `${make} is older than ${standard}`
  : 'new'
;

// Bad
const carStatus = (miles > getCarMiles()
  ? `${make} is older than ${standard}`
  : 'new'
);

// Good
const carStatus = (
  miles > getCarMiles()
    ? `${make} is older than ${standard}`
    : 'new'
);
```

<Rule>
  Operators always start lines
</Rule>

```ts
// Bad:
const carStatus = (
  miles > getCarMiles() ?
    `${make} is older than ${standard}` :
    'new'
);

// Good
const carStatus = (
  miles > getCarMiles()
    ? `${make} is older than ${standard}`
    : 'new'
);

// Bad:
const isInClass = (
  joinedZoom ||
  sittingInPerson ||
  watchedVideo
);

// Good:
const isInClass = (
  joinedZoom
  || sittingInPerson
  || watchedVideo
);

// Bad:
const age = (
  currentAge +
  elapsedTime
);

// Good:
const age = (
  currentAge
  + elapsedTime
);
```

<Exercise>
  Fix the formatting of the following boolean logic
</Exercise>

```ts
const isStudent = (
  inRoster && (!isTTM ||
    (studentEnrollments +
    observerEnrollments) >
    0
  )
);
```

<!-- Start Example -->
<details>
<summary>Example Result</summary>
<pre>
// Required formatting:
const isStudent = (
  inRoster
  && (
    !isTTM
    || (
      (studentEnrollments + observerEnrollments)
      > 0
    )
  )
);

// It's also okay to put enrollments on their own lines
const isStudent = (
  inRoster
  && (
    !isTTM
    || (
      (
        studentEnrollments
        + observerEnrollments
      )
      > 0
    )
  )
);

// Much better with comments:
const isStudent = (
  // The user must be in the roster
  inRoster
  // ...and cannot be a TTM
  && (
    // The user is not a TTM
    !isTTM
    // ...or the user is a student/auditor
    || (
      (studentEnrollments + observerEnrollments)
      > 0
    )
  )
);
</pre>
</details>
<!-- End Example -->

When retrieving values from objects or tuples (arrays of length 2), you can destructure. We prefer that you do not alias (do not rename destructured values). This helps other programmers follow data around your code and also helps when people use `find` or other searching mechanisms.

<Rule>
  Destructure where possible. Do not alias unless necessary
</Rule>

```ts
const {
  name,
  age,
} = person;
```

## Errors

We always use `try/catch` to handle errors (we don't use `.then` or `.catch` unless absolutely necessary).

Errors must always contain two important ingredients:

1. A human-readable message that explains the issue in plain and simple english without revealing any technical details or inner workings of the app.
1. An error code in the form `ABC123`, where the letters are a code that's specific to the project or section of the project, and the number is a unique number assigned to the error.

<Rule tall>
  All errors must have a human-readable message and a unique error code
</Rule>

To make this possible, we use a custom error called `ErrorWithCode` which can be found in `dce-reactkit`.

## Functions

We never use the `function` keyword. It's been outdated for years.

<Rule>
  Never use the function keyword
</Rule>

```ts
// Banned:
function honk(horn) {
    ...
}
```

Use arrow functions as much as possible: this ensures appropriate context binding and reduces complexity.

<Rule>
  Use arrow functions as much as possible
</Rule>

```ts
// Helper
const honk = (horn: HondaHorn) => {
    ...
};

// Inline
cars.forEach((car) => {
    ...
});
```

To keep our arrow functions uniform, we try not to use shorthand unless it's very helpful. Thus, parentheses around arguments are usually required and curly brackets are usually required surrounding the body, even if the function is very simple. Similarly, most arrow functions should be multiline.

<Rule>
  Arrow functions usually have ( ) and { } and are usually multiline
</Rule>

```ts
// Banned:
(x) => x + 1

// Banned:
name => { print(name); }

// Good:
(x) => {
  return x + 1;
}

// Good:
(name) => {
  print(name);
}
```

<Exercise>
  Fix the function below to make it adhere to our standards
</Exercise>

```ts
// NOTE: created by Chat GPT using this prompt:
// Create a typescript function that takes a string and counts the number of sentences

function countSentences(text: string): number {
  // Define an array of characters that may end a sentence.
  const sentenceEnders = [".", "!", "?"];
  
  // Initialize the sentence count to zero.
  let sentenceCount = 0;
  
  // Loop through each character in the text.
  for (let i = 0; i < text.length; i++) {
    const char = text[i];
    
    // If the character is a sentence ender, increment the sentence count.
    if (sentenceEnders.includes(char)) {
      sentenceCount++;
    }
  }
  
  // Return the sentence count.
  return sentenceCount;
}

// Bonus points for optimizing the code too!
```

<!-- Start Example -->
<details>
<summary>Example Result</summary>
<pre>
<b>// NOTE: moved this outside of function so it isn't initialized over and over</b>
// Define an array of characters that may end a sentence.
const sentenceEnders = [<b>'.', '!', '?'</b>];

const countSentences = (text: string): number => {
  // Initialize the sentence count to zero.
  let sentenceCount = 0;
  
  // Loop through each character in the text.
  for (let i = 0; i < text.length; i++) {
    const char = text[i];
    
    // If the character is a sentence ender, increment the sentence count.
    if (sentenceEnders.includes(char)) {
      sentenceCount <b>+=</b> 1;
    }
  }
  
  // Return the sentence count.
  return sentenceCount;
}
</pre>
</details>
<!-- End Example -->

### Documentation

All named functions absolutely must have JSDoc definitions. Include a description of the purpose of the function, add one or more author tags for people who worked on that function, and describe arguments and return.

<Rule>
  Add JSDoc to all named functions
</Rule>

```ts
/**
 * Prepares a car to race: fills up the tank and tests the engine
 * @author Your Name
 * @param car the car to prepare
 * @param raceType the type of race to prepare for
 * @returns cost of the preparation process in USD
 */
const prepareCar = async (car: Car, raceType: RaceType): number => {
    ...
};
```

Notice that data types are included inline in the typescript function declaration. To minimize documentation update issues, keep data types and sync/async status inline in the typescript. Do not include them in JSDoc. Thus, `{type}` tags and the `@async` keyword are not allowed

<Rule>
  Don't duplicate descriptions with JSDoc
</Rule>

```ts
// Bad:
/**
 * Prepares a car to race: fills up the tank and tests the engine
 * @author Your Name
 * @async
 * @param {Car} car the car to prepare
 * @param {RaceType} raceType the type of race to prepare for
 * @returns cost of the preparation process in USD
 */
const prepareCar = async (car: Car, raceType: RaceType): number => {
  ...
};

// Good:
/**
 * Prepares a car to race: fills up the tank and tests the engine
 * @author Your Name
 * @param car the car to prepare
 * @param raceType the type of race to prepare for
 * @returns cost of the preparation process in USD
 */
const prepareCar = async (car: Car, raceType: RaceType): number => {
  ...
};
```

<Exercise>
  Create JSDoc for the following function
</Exercise>

```ts
const countSentences = (
  opts: {
    text: string,
    sentenceEnders?: string[],
    countEmptyLines?: boolean,
  },
): number {
  ...
};
```

<!-- Start Example -->
<details>
<summary>Example Result</summary>
<pre>
<b>
/**
  * Count the number of sentences in a string
  * @author Gabe Abrams
  * @param opts object containing all arguments
  * @param opts.text the text to analyze
  * @param [opts.sentenceEnders] custom sentence ender punctuation marks
  *   to use when counting sentences
  * @param [opts.countEmptyLines] if true, count empty lines as sentences too
  * @returns the number of sentences in the text
  */
</b>
const countSentences = (
  opts: {
    text: string,
    sentenceEnders?: string[],
    countEmptyLines?: boolean,
  },
): number {
  ...
};
</pre>
</details>
<!-- End Example -->

### Default Argument Values

To include a default value for an argument, do this:

```ts
const helper = (a: string, b: string = 'default value') => {
  // ...
};
```

<Rule>
  All required params must come before default params
</Rule>

```ts
// Bad:
const helper = (text: string, greeting: string = 'hi', id: number) => {
  ...
};

// Good:
const helper = (text: string, id: number, greeting: string = 'hi') => {
  ...
};
```

With types and defaults, arguments can take up a lot of space. As usual, if one item is on another line, all items must be on their own lines. Here's how to do this with arguments:

```ts
const helper = (
  opts: {
    requiredParam1: string,
    requiredParam2: number,
    optionalParam: string = 'default value',
  },
) => {
  // ...
};
```

## Classes

Ask yourself: should this code be a helper function or a class? One rule of thumb is that if code will only be instantiated once, it's probably best as a helper function. Also, if it doesn't have to maintain its own context (it's mostly data, maybe a couple helper functions that do not refer to "this") it could probably just be a type.

All variables in the class must be defined at the top of the class (all `this.xyz` variable).

<Rule>
  Define all instance properties at top of class
</Rule>

```ts
class User {
  private name: string;
  private age: number;
  private pronouns?: string;
  private gender?: string;

  ...
}
```

Every property and methods must be labeled as either `private` or `public`. We require that you make an active decision on privacy. Note: `#` is an acceptable substitute for `private` if you prefer.

<Rule>
  All class properties and methods must either be private or public
</Rule>

```ts
class User {
  // Bad:
  name: string;

  // Good:
  private name: string;

  // Bad:
  getName(): string {
    ...
  }

  // Good:
  public getName(): string {
    ...
  }
}
```

If a method doesn't refer to `this`, then there's no reason it can't be a `static` method. Thus, if a method doesn't refer to `this`, we require that it be `static`. This helps because it's easy for others to figure out if a function depends on class variables.

<Rule>
  Methods that don't reference "this" must be static
</Rule>

```ts
class User {
  // Bad:
  public sayHello() {
    console.log('Hello!');
  }

  // Good:
  public static sayHello() {
    console.log('Hello!');
  }

  // Good:
  public getName(): string {
    return this.name;
  }
}
```

<Exercise>
  Think of your favorite mode of transport as a kid (bike, tricycle, rip stick, scooter) and create a class that represents it (don't implement functions)
</Exercise>

```ts
// Example:
class Kayak {
  // Number of seats in the kayak
  private numSeats: number;
  // Current location
  private location: { x: number, y: number };
  // Current direction
  private direction: number; // degrees

  /**
   * Performs paddle operation, moving the kayak either forward or backward
   * @author Gabe Abrams
   * @param [backward] if true, paddle backward
   */
  public paddle(backward?: boolean) {
    // TODO: implement
  }

  /**
   * Either turns the kayak left (ccw) or right (cw)
   * @author Gabe Abrams
   * @param [opts] object containing all arguments
   * @param [opts.direction=left] the direction to turn
   * @param [opts.angle=45] number of degrees to turn the kayak
   */
  public turn(
    opts: {
      direction?: 'left' | 'right',
      angle?: number,
    } = {},
  ) {
    // TODO: implement
  }
}
```

## Types

We use `Type` to define types (instead of `Interface`) because of some important advanced features that we leverage in React. Note that many people disagree with Gabe on this, so be flexible in interviews, be ready to use `Interface` as well.

<Rule>
  Wherever possible, use Type instead of Interface
</Rule>

```ts
type Car = {
  ...
};
```

We treat types as objects, ending lines with `,` instead of `;`. This isn't because of very important functionality, this is just for consistency. The commas show that each item is part of the whole.

<Rule>
  Delimit types with commas
</Rule>

```ts
type Car = {
  // Company that the car was made by
  make: string,
  // Age
  age: number, // years
};
```

Every property in a type must be accompanied by a full description and units (as usual). Comment above each item.

<Rule>
  Describe all type properties
</Rule>

```ts
// Good:
type Car = {
  // Company that the car was made by
  make: string,
  // Age of the car
  age: number, // years
};

// Bad:
type Car = {
  make: string,
  age: number,
};
```

<Exercise>
  Create a type for your favorite savory entree as if it were a customizable item on an online menu
</Exercise>

```ts
// Example: Samosa Chaat
type SamosaChaat = {
  // Filling inside of the samosa
  filling: string,
  // If true, the chaat will be prepared with more spice
  spicy: boolean,
  // Number of samosas in the chaat
  samosaQuantity: number,
};
```

If a type can have multiple different structures, use `|`:

<Rule>
  If a type has multiple forms, separate by |
</Rule>

```ts
type Vehicle = (
  | {
    // Type of vehicle
    type: 'car',
    // Number of wheels
    numWheels: number,
    // True if car fits in a compact parking spot
    isCompact: boolean,
  }
  | {
    // Type of vehicle
    type: 'truck',
    // Number of wheels
    numWheels: number,
    // True if truck has a trailer hitch
    hasTrailerHitch: boolean,
  }
);
```

In the case where all forms of a type have shared parts, separate that out into a general section of the type:

```ts
type Vehicle = (
  // Common parameters
  {
    // Number of wheels
    numWheels: number,
  }
  // Type-dependent parameters
  & (
    // Car
    | {
      // Type of vehicle
      type: 'car',
      // True if car fits in a compact parking spot
      isCompact: boolean,
    }
    // Truck
    | {
      // Type of vehicle
      type: 'truck',
      // True if truck has a trailer hitch
      hasTrailerHitch: boolean,
    }
  )
);
```

<Exercise>
  Add an optional "side" for your entree. Add a "hasSide" boolean and if it's true, also define your "side" type
</Exercise>

```ts
// Example: Samosa Chaat with Optional Drink
type SamosaChaat = (
  {
    // Filling inside of the samosa
    filling: string,
    // If true, the chaat will be prepared with more spice
    spicy: boolean,
    // Number of samosas in the chaat
    samosaQuantity: number,
  } & (
    // No side drink
    | {
      // If true, a side is included
      hasSide: false,
    }
    // Includes side
    | {
      // If true, a side is included
      hasSide: true,
      // Description of side
      side: {
        // Name of the side
        name: (
          | 'Lassi'
          | 'Water'
          | 'Chai'
        ),
        // Additional cost of the side
        costDollars: number,
      },
    }
  )
);
```

### Types Cheatsheet

For your reference, here's a types cheatsheet with props that I use frequently:

```ts
// Primitives
string // text or character (e.g. 'Hello' or 'h')
number // integer or float (e.g. 4 or 4.73)
boolean // true or false
undefined // Unset value
null // Absence of value

// Operations
(string | number) // Any type in this list
('blue' | 'red' | 'green') // Any value in a list

// Arrays
string[] // Array of strings
number[] // Array of numbers
Car[] // Array containing objects of type Car
(string | Car)[] // Array of strings or objects of type Car

// Enums
EnumName // Enums also function as types

// Common Data Structures
{ [k: string]: number } // Object where keys are strings, values are numbers
Map<string, Car> // Map where keys are strings, values are objects of type Car
Set<Car> // Set of objects of type Car

// Functions
() => undefined // Function with no arguments, no return
(car: Car) => undefined // Function with an argument and no return value
(car: Car, year?: number) => number // Function with optional arg and return type

// Object with specific structure
{
  name: string,
  age?: number,
}

// React types
React.ReactNode // Renderable React content
React.FC<Props> // Functional Component

// Types to avoid
any
unknown
```

Avoid casting at all costs, but if it must be done, use the `as` keyword:

```ts
const user = (await fetchUserFromAPI()) as User;
```

Casting is different from value conversion:

```ts
// Convert to a string:
const str = String(value);

// Convert to a number:
const int = Number.parseInt(value, 10);
const fl = Number.parseFloat(value);

// Convert to a boolean:
const b = !!value;
```

## Enums

If a value can take on many pre-determined values, we use enums. However, we understand that enums are limited: keys are not dynamic and values cannot be complex objects. Use enums where possible.

<Rule>
  Prefer enums, but substitute with objects if not possible
</Rule>

```ts
enum Instrument {
  // An upright piano
  Piano = 'Piano',
  // A violin string instrument
  Violin = 'Violin',
}
```

There are shorthands for numerical enums. To ensure readable database entries and debugging, we prefer string-valued enums where the value is identical to the name.

<Rule>
  Keys and values of enums should be identical strings
</Rule>

```ts
// Bad:
enum Instrument {
  Piano = 'piano',
  Violin = 'violin',
}

// Bad:
enum Instrument {
  Piano,
  Violin,
}

// Bad:
enum Instrument {
  Piano = 1,
  Violin = 2,
}

// Good:
enum Instrument {
  // An upright piano
  Piano = 'Piano',
  // A violin string instrument
  Violin = 'Violin',
}
```

<Exercise>
  Update your entree type to use enums
</Exercise>

```ts
// Type of fillings
enum Filling {
  // Potato and pea filling
  PotatoPea = 'PotatoPea',
  // Cauliflower mash filling
  Cauliflower = 'Cauliflower',
}

// Name of side
enum SideName {
  // Mango or salty lassi
  Lassi = 'Lassi',
  // Iced water
  Water = 'Water',
  // Masala tea
  Chai = 'Chai',
}

// Example: Samosa Chaat with Optional Drink
type SamosaChaat = (
  {
    // Filling inside of the samosa
    filling: Filling,
    // If true, the chaat will be prepared with more spice
    spicy: boolean,
    // Number of samosas in the chaat
    samosaQuantity: number,
  } & (
    // No side drink
    | {
      // If true, a side is included
      hasSide: false,
    }
    // Includes side
    | {
      // If true, a side is included
      hasSide: true,
      // Description of side
      side: {
        // Name of the side
        name: SideName,
        // Additional cost of the side
        costDollars: number,
      },
    }
  )
);
```

It's important to know the type of item, not just the item itself, especially when reading other people's code. Also, some enums may have duplicate keys. This is why we don't destructure enums.

<Rule tall>
  Never destructure enums
</Rule>

## Code Style

To keep code readable and simple, if there are ever more than three of anything (arguments, values, anything), each must be on its own line. Honestly, it's okay to put items on their own lines if there are two or more items.

<Rule>
  If more than three elements, put each element on its own line
</Rule>

```ts
Additionally, whenever there is one item on its own line, all other items must be on their own lines as well.
```

<Rule tall>
  When an item is on its own line, only that item can be on the line (no parentheses, etc.)
</Rule>

Arrays:

```ts
// Bad: first item is not on its own line
const fruits = ['Apple',
  'Orange',
  'Pineapple',
  'Mango',
];

// Bad: last item is not on its own line
const fruits = [
  'Apple',
  'Orange',
  'Pineapple',
  'Mango'];

// Good
const fruits = [
  'Apple',
  'Orange',
  'Pineapple',
  'Mango',
];
```

Function calls:

```ts
// Bad: first item is not on its own line
const firstName = database.initialize()
    .getUser()
    .firstName;

// Bad
const firstName = (
    database.initialize()
        .getUser()
        .firstName
);

// Good
const firstName = (
    database
        .initialize()
        .getUser()
        .firstName
);
```

Arguments:

```ts
// Bad: first item is not on its own line
startCar(Engine.getFourCylinder(),
    WheelKit.manufacture(4),
    Horn.prepare(),
);

// Bad: last item is not on its own line
startCar(Engine.getFourCylinder(),
    WheelKit.manufacture(4),
    Horn.prepare());

// Good
startCar(
    Engine.getFourCylinder(),
    WheelKit.manufacture(4),
    Horn.prepare(),
);
```

<Exercise>
  Fix the following bits of code
</Exercise>

```ts
// Bit 1:
const output = getOutput(text, {
  parse: true,
  delimiter: ',',
});

// Bit 2:
const ageNextYear = (
  ageAtLogin
  + elapsedYears
  + 1);

// Bit 3:
const studentLists = [getDCEStudents(),
  getFASUsers().roster
    .filter((user) => {
      return user.isStudent;
    }).map((user) => {
      return user.userInfo;
    }),
];
```

<!-- Start Example -->
<details>
<summary>Example Result</summary>
<pre>
// Bit 1:
const output = getOutput(
  <b>text, {</b>
    <b>parse: true,</b>
    <b>delimiter: ',',</b>
  <b>},</b>
);

// Bit 2:
const ageNextYear = (
  <b>ageAtLogin</b>
  <b>+ elapsedYears</b>
  <b>+ 1</b>
);

// Bit 3:
const studentLists = [
  <b>getDCEStudents(),</b>
  <b>getFASUsers()</b>
    <b>.roster</b>
    <b>.filter((user) => {</b>
      <b>return user.isStudent;</b>
    <b>})</b>
    <b>.map((user) => {</b>
      <b>return user.userInfo;</b>
    <b>}),</b>
];
</pre>
</details>
<!-- End Example -->

For all arrays, function arguments, object definitions, and other comma-delineated objects, use trailing commas. This helps create clean git diffs and reduces typos.

<Rule>
  Use trailing commas
</Rule>

```
See the examples above. Look for trailing commas.

Note: this is not supported in `.json` files. Thus, when possible, we prefer `.tsx` for data if possible.
```

<Rule>
  Use "guard clauses" if possible
</Rule>

```ts
// Bad:
const showTeacherInfo = () => {
  // Make sure there's at least one enrolled user
  if (enrollments.length > 0) {
    // Print
    console.log('This course has at least one enrolled user');

    // Check if the course has a teacher
    const hasTeacher = enrollments.some((enrollment) => {
      return (enrollment.type === 'TTM');
    });
    if (hasTeacher) {
      // Print
      console.log('This course already has an assigned teacher');

      // Update the UI
      dispatch({
        type: ActionType.ShowTeacherInfo,
      });
    }
  }
};

// Good:
const showTeacherInfo = () => {
  // Make sure there's at least one enrolled user
  if (enrollments.length === 0) {
    return;
  }

  // Print
  console.log('This course has at least one enrolled user');

  // Check if the course has a teacher
  const hasTeacher = enrollments.some((enrollment) => {
    return (enrollment.type === 'TTM');
  });
  if (!hasTeacher) {
    return;
  }
  
  // Print
  console.log('This course already has an assigned teacher');

  // Update the UI
  dispatch({
    type: ActionType.ShowTeacherInfo,
  });
};
```

Guard clauses are `if` statements that terminate execution. Using guard clauses removes the need for nesting.


# Typescript Advanced Stuff

## Array Functions

Array functions are awesome. Replace loops with array functions wherever possible. Unfortunately, array functions do not fully support async/await yet. That's the only time we must use a `for` loop.

<Rule>
  Use array functions whenever possible unless await is used inside
</Rule>

```ts
// Good:
fruits.forEach((fruit: Fruit) => {
  console.log(`I love ${fruit}s`);
});

// Bad:
fruits.forEach(async (fruit: Fruit) => {
  await fruit.waitToRipen();
});

// Good
for (let i = 0; i < fruits.length; i++) {
  await fruits[i].waitToRipen();
}
```

Each array function takes an anonymous "operation function" that is called once for each element in the array. Each time the operation function is called, it receives one of the array elements as an argument. This occurs sequentially such that the operation function is called with the first element, then the second element, then the third, and so on.

### array.forEach – Executes a provided function once for each array element

The operation function holds the code that you want to run for each element.

```ts
const fruits = ['apple', 'orange', 'pineapple'];

fruits.forEach((fruit: string) => {
  console.log(`I love ${fruit}s`);
});

// Output:
// > I love apples
// > I love oranges
// > I love pineapples
```

You can also get the element's index:

```ts
fruits.forEach((fruit, i) => {
  // ...
});
```

<Exercise>
  Create code that greets every other student
</Exercise>

```ts
const studentNames = ['Divardo', 'Calicci', 'Kai', 'Manu', 'Anini', 'Alli'];

// TODO: implement

// Output:
// > Hello, Calicci
// > Hello, Manu
// > Hello, Alli
```

<!-- Start Example -->
<details>
<summary>Example Result</summary>
<pre>
const studentNames = ['Divardo', 'Calicci', 'Kai', 'Manu', 'Anini', 'Alli'];

// Greet every other student
studentNames.forEach((studentName, i) => {
  // Skip even indexed students
  if (i % 2 === 0) {
    return;
  }

  // Greet the student
  console.log(`Hello, ${studentName}`);
});
</pre>
</details>
<!-- End Example -->

### array.map – Creates a new array by applying a function to each element

The operation function takes an element of the original array, does some computation, and then returns the corresponding element for the new array.

```ts
type Car = {
  // The color of the car
  color: string,
  // The year the car was made
  year: number,
};

const cars: Car[] = [
  {
    color: 'red',
    year: 2015,
  },
  {
    color: 'blue',
    year: 2018,
  },
];

const years: number[] = cars.map((car: Car) => {
  return car.year;
});

const olderCars: Car[] = cars.map((car: Car) => {
  return {
    ...car,
    year: car.year - 1,
  };
});
```

<Exercise>
  Create code that prepends each student's name with "Legal Name: "
</Exercise>

```ts
const studentNames = ['Divardo', 'Calicci', 'Kai'];

// TODO: implement

// Output: ['Legal Name: Divardo', 'Legal Name: Calicci', 'Legal Name: Kai']
```

<!-- Start Example -->
<details>
<summary>Example Result</summary>
<pre>
const studentNames = ['Divardo', 'Calicci', 'Kai'];

// Prepend each student's name
const prependedStudentNames = studentNames.map((studentName) => {
  // Add prefix
  return `Legal Name: ${studentName}`;
});
</pre>
</details>
<!-- End Example -->

<Rule tall>
  Prefer .forEach or .map over .reduce
</Rule>

<Rule>
  Never modify function arguments
</Rule>

```ts
// Bad:
const olderCars: Car[] = cars.map((car: Car) => {
  car.year -= 1;

  return car;
});

// Good:
const olderCars: Car[] = cars.map((car: Car) => {
  return {
    ...car,
    year: car.year - 1,
  };
});
```

### array.some – Test whether an element in the array passes the test function

The operation function takes an element in the array and returns true/truthy if this element passes the test. If any element results in the operation function returning true/truthy, `some` immediately returns true. If no elements result in the operation function returning true/truthy, `some` returns false after going through the entire array.

```ts
type Car = {
  // The color of the car
  color: string,
  // The year the car was made
  year: number,
};

const cars: Car[] = [
  {
    color: 'red',
    year: 2015,
  },
  {
    color: 'blue',
    year: 2018,
  },
];

const atLeastOneRed = cars.some((car: Car) => {
  return (car.color === 'red');
});
```

<Exercise>
  Create code that checks if any of the students have a name that ends with a vowel
</Exercise>

```ts
const listA = ['Divardo', 'Calicci', 'Kai'];
const listB = ['Max', 'Clark', 'Ash'];

// TODO: implement

// Output:
// > true
// > false
```

<!-- Start Example -->
<details>
<summary>Example Result</summary>
<pre>
const listA = ['Divardo', 'Calicci', 'Kai'];
const listB = ['Max', 'Clark', 'Ash'];

// Create a list of vowels
const vowels = 'aeiou'.split('');

// Go through each list and check if a student's name ends with a vowel
[listA,listB].forEach((studentNames) => {
  const atLeastOneNameEndsWithVowel = studentNames.some((studentName) => {
    // Get last letter
    const lastLetter = (
      studentName
        .toLowerCase()
        .substring(studentName.length - 1)
    );

    // Check if last letter is a vowel
    return vowels.includes(lastLetter);
  });
});
</pre>
</details>
<!-- End Example -->

### array.every – Test whether all elements in the array pass the test function

The operation function takes an element in the array and returns true/truthy if this element passes the test. If all elements results in the operation function returning true/truthy, `every` returns true after going through the entire array. If at any point, one of the elements result in the operation function returning false/falsy, `every` immediately returns false.

```ts
type Car = {
  // The color of the car
  color: string,
  // The year the car was made
  year: number,
};

const cars: Car[] = [
  {
    color: 'red',
    year: 2015,
  },
  {
    color: 'blue',
    year: 2018,
  },
];

const allCarsAreRed = cars.every((car: Car) => {
  return (car.color === 'red');
});
```

<Exercise>
  Create code that checks if every student is at least 18 years old
</Exercise>

```ts
type Student = {
  // First name
  name: string,
  // Age
  age: number, // years
};

const listA: Student[] = [
  { name: 'Divardo', age: 17 },
  { name: 'Calicci', age: 18 },
  { name: 'Kai', age: 19 },
];
const listB: Student[] = [
  { name: 'Max', age: 20 },
  { name: 'Clark', age: 18 },
  { name: 'Ash', age: 22 },
];

// TODO: implement

// Output:
// > false
// > true
```

<!-- Start Example -->
<details>
<summary>Example Result</summary>
<pre>
const listA = [
  { name: 'Divardo', age: 17 },
  { name: 'Calicci', age: 18 },
  { name: 'Kai', age: 19 },
];
const listB = [
  { name: 'Max', age: 20 },
  { name: 'Clark', age: 18 },
  { name: 'Ash', age: 22 },
];

// Go through each list and check if all students are 18+
[listA,listB].forEach((students) => {
  const allStudentsAtLeast18 = students.every((student) => {
    return (student.age >= 18);
  });
});
</pre>
</details>
<!-- End Example -->

### array.filter – Create an array with elements that pass the test function

The operation function takes an element in the array and returns true/truthy if this element passes the test. At the end, `filter` returns a new array that contains only the elements that pass the test.

```ts
type Car = {
  // The color of the car
  color: string,
  // The year the car was made
  year: number,
};

const cars: Car[] = [
  {
    color: 'red',
    year: 2015,
  },
  {
    color: 'blue',
    year: 2018,
  },
];

const redCars = cars.filter((car: Car) => {
  return (car.color === 'red');
});
```

<Exercise>
  Create code that creates a list of students who are teens
</Exercise>

```ts
type Student = {
  // First name
  name: string,
  // Age
  age: number, // years
};

const students: Student[] = [
  { name: 'Divardo', age: 17 },
  { name: 'Calicci', age: 18 },
  { name: 'Kai', age: 19 },
  { name: 'Max', age: 20 },
  { name: 'Clark', age: 18 },
  { name: 'Ash', age: 22 },
  { name: 'Anna', age: 12 },
];

// TODO: implement

// Output:
// [
//   { name: 'Divardo', age: 17 },
//   { name: 'Calicci', age: 18 },
//   { name: 'Kai', age: 19 },
//   { name: 'Clark', age: 18 },
// ]
```

<!-- Start Example -->
<details>
<summary>Example Result</summary>
<pre>
const students = [
  { name: 'Divardo', age: 17 },
  { name: 'Calicci', age: 18 },
  { name: 'Kai', age: 19 },
  { name: 'Max', age: 20 },
  { name: 'Clark', age: 18 },
  { name: 'Ash', age: 22 },
  { name: 'Anna', age: 12 },
];

// Filter to just teen students
const teens = students.filter((student) => {
  return (
    // Old enough
    student.age >= 13
    // ...and not too old
    && student.age < 20
  );
});
</pre>
</details>
<!-- End Example -->

### array.find - Return the first element that satisfies the test function

The operation function takes an element in the array and returns true/truthy if this element passes the test. At the end, `find` return the first element that passes the test. If no elements pass the test, `find` returns `undefined`.

```ts
type Car = {
  // Color of the body of the car
  color: string,
  // Year that the car was manufactured
  year: number, // e.g. 1995
  // The first name of the owner of the car
  owner: string,
};


const cars: Car[] = [
  {
    color: 'red',
    year: 2015,
    owner: 'Gabe',
  },
  {
    color: 'blue',
    year: 2018,
    owner: 'Ben',
  },
];

const bensCar = cars.find((car: Car) => {
  return (car.owner === 'Ben');
});
```

<Exercise>
  Create code that finds a student who's name starts with 'A'
</Exercise>

```ts
type Student = {
  // First name
  name: string,
  // Age
  age: number, // years
};

const students: Student[] = [
  { name: 'Divardo', age: 17 },
  { name: 'Calicci', age: 18 },
  { name: 'Kai', age: 19 },
  { name: 'Max', age: 20 },
  { name: 'Clark', age: 18 },
  { name: 'Ash', age: 22 },
  { name: 'Anna', age: 12 },
];

// TODO: implement

// Output:
// { name: 'Ash', age: 22 }
```

<!-- Start Example -->
<details>
<summary>Example Result</summary>
<pre>
const students = [
  { name: 'Divardo', age: 17 },
  { name: 'Calicci', age: 18 },
  { name: 'Kai', age: 19 },
  { name: 'Max', age: 20 },
  { name: 'Clark', age: 18 },
  { name: 'Ash', age: 22 },
  { name: 'Anna', age: 12 },
];

// Find a student who's name starts with 'A'
<b>const studentWithNameStartingInA = students.find((student) => {</b>
  <b>return student.name.startsWith('A');</b>
<b>});</b>
</pre>
</details>
<!-- End Example -->

## Object Functions

Object functions are great for iterating through objects. Use them whenever possible. But just like array functions, if using async/await inside the loop, you'll need a for loop.

<Rule tall>
  Use object functions whenever possible unless await is used inside
</Rule>

### Object.keys(...) – get an array that contains each key in the object

```ts
const idToName = {
  12459: 'Divardo',
  50829: 'Calicci',
  50628: 'Keala',
};

const ids = Object.keys(idToName);
```

Note: no matter what type of keys you use, `Object.keys` returns an array of strings. In the example above, `ids` is a string array with values `['12459', '50829', '50628']`.

### Object.values(...) – get an array of values

```ts
const idToName = {
  12459: 'Divardo',
  50829: 'Calicci',
  51628: 'Keala',
};

const names = Object.values(idToName);
```

### Combine with array functions

It's often important to loop through an enum or object's keys or values.

```ts
Object.values(idToName).forEach((name: string) => {
  console.log(`Hello, ${name}!`);
});
```

<Exercise>
  Create an array containing just the first two digits of each student's id number
</Exercise>

```ts
const idToName = {
  12459: 'Divardo',
  50829: 'Calicci',
  51628: 'Keala',
};

// TODO: implement

// Output:
// [12, 50, 50]
```

<!-- Start Example -->
<details>
<summary>Example Result</summary>
<pre>
const idToName = {
  12459: 'Divardo',
  50829: 'Calicci',
  51628: 'Keala',
};

// Extract the first two letters of each id number
const idPrefixes = Object.keys(idToName).map((id) => {
  return id.substring(0, 2);
});
</pre>
</details>
<!-- End Example -->

## Asynchronous Code

Typescript is a single-threaded interpreted language and is _much_ slower than C/C++ and other compiled languages. _But_, asynchronous code runs really fast and is great for servers and good for simple clients like browsers. Thus, Express and React are great choices as long as we use asynchronous code when necessary.

### Asynchronous Functions

This function is non-blocking and executes its function body in the background.

```ts
const funcName = async () => {
  ...
};
```

For asynchronous functions that have return values, simply wrap the return type in `Promise<...>`:

```ts
// For example, here's an async function that returns a number
const funcName = async (): Promise<number> => {
  ...
};
```

Always use the `async` keyword instead of returning `Promise` objects. In fact, refrain from referencing `Promise` except in types and when using `Promise.all`.

<Rule>
  Only reference Promise when using Promise.all or when defining types
</Rule>

```ts
// Bad:
const ready = new Promise((resolve, reject) => {
  ...
});

// Bad:
loadFile.then((contents) => {
  // ...
});
// (where loadFile returns a promise)

// Bad:
const funcName = () => {
  ...
  const p = new Promise((resolve, reject) => {
    ...
  });
  ...
  return p;
};

// Okay:
const funcName = async (): Promise<number> => {
  ...
  await doSomething();
  ...
  return 5;
};

// Okay:
await Promise.all(tasks);
```

<Exercise>
  Create an async function that creates a unique test assignment in a sandbox course
</Exercise>

```ts
// Import caccl-api
import initAPI from 'caccl-api';

// Initialize the API
const api = initAPI({
  // TODO: fill this in
});

// TODO: create a function "createTestAssignment" that creates a unique assignment in the course and returns it
// NOTE: check out the caccl-api docs at bit.ly/caccl-api
```

<!-- Start Example -->
<details>
<summary>Example Result</summary>
<pre>
// Import caccl-api
import initAPI from 'caccl-api';

// Initialize the API
const api = initAPI({
  <b>canvasHost: 'canvas.harvard.edu',</b>
  <b>accessToken: '1895~sdjfoa9me098fjoiasnudo8f7am9sod8ufnoaisdunfkuasdf',</b>
  <b>defaultCourseId: 53450,</b>
});

<b>/**</b>
 <b>* Create a unique test assignment within the sandbox course</b>
 <b>* @author Gabe Abrams</b>
 <b>* @returns assignment object that was created</b>
 <b>*/</b>
<b>const createTestAssignment = async () => {</b>
  <b>// Generate a unique assignment name</b>
  <b>const uniqueAssignmentName = `Test Assignment[${Date.now()}-${Math.random()}]`;</b>

  <b>// Create an assignment</b>
  <b>const assignment = await api.course.assignment.create({</b>
    <b>name: uniqueAssignmentName,</b>
    <b>submissionTypes: ['none'],</b>
    <b>published: true,</b>
  <b>});</b>

  <b>// Return the new assignment</b>
  <b>return assignment;</b>
<b>};</b>
</pre>
</details>
<!-- End Example -->

### Waiting for async tasks

To wait for an async task, always use `await` instead of `.then`.

<Rule>
  Use await instead of .then
</Rule>

```ts
// Bad:
fruit.ripe().then(() => {
  console.log('The fruit is ripe!');
});

// Good:
await fruit.ripe();
```

To catch an error from an awaited task, just surround with `try/catch` instead of `.catch`. This is because if you forget to use `.catch`, errors disappear into the ether.

<Rule>
  Use try/catch instead of .catch
</Rule>

```ts
// Bad:
fruit.ripe().catch((err) => {
  ...
});

// Good:
try {
  await fruit.ripe();
} catch (err) {
  ...
}
```

### Series execution

Use the `await` flag to wait for each function to finish.

```ts
const data1 = await doTask1();
const data2 = await doTask2();
```

<Exercise>
  Create an assignment and then get the full list of assignments
</Exercise>

```ts
// Import caccl-api
import initAPI from 'caccl-api';

// Initialize the API
const api = initAPI({
  // TODO: fill this in
});

// TODO: implement the solution
// NOTE: check out the caccl-api docs at bit.ly/caccl-api
```

<!-- Start Example -->
<details>
<summary>Example Result</summary>
<pre>
// Import caccl-api
import initAPI from 'caccl-api';

// Initialize the API
const api = initAPI({
  <b>canvasHost: 'canvas.harvard.edu',</b>
  <b>accessToken: '1895~sdjfoa9me098fjoiasnudo8f7am9sod8ufnoaisdunfkuasdf',</b>
  <b>defaultCourseId: 53450,</b>
});

<b>/**</b>
 <b>* Create a unique test assignment within the sandbox course</b>
 <b>* @author Gabe Abrams</b>
 <b>* @returns assignment object that was created</b>
 <b>*/</b>
<b>const createTestAssignment = async () => {</b>
  <b>// Generate a unique assignment name</b>
  <b>const uniqueAssignmentName = `Test Assignment [${Date.now()}-${Math.random()}]`;</b>

  <b>// Create an assignment</b>
  <b>const assignment = await api.course.assignment.create({</b>
    <b>name: uniqueAssignmentName,</b>
    <b>submissionTypes: ['none'],</b>
    <b>published: true,</b>
  <b>});</b>

  <b>// Return the new assignment</b>
  <b>return assignment;</b>
<b>};</b>

<b>// First, create an assignment</b>
<b>await createTestAssignment();</b>

<b>// Then, get the full list of assignments</b>
<b>const assignments = await api.course.assignment.list();</b>
</pre>
</details>
<!-- End Example -->

### Parallel execution

Combine `await` with `Promise.all` for parallel execution.

```ts
const [
  data1,
  data2,
] = await Promise.all([
  doTask1(),
  doTask2(),
]);
```

<Exercise>
  In parallel, get the list of pages, assignments, and discussion topics
</Exercise>

```ts
// Import caccl-api
import initAPI from 'caccl-api';

// Initialize the API
const api = initAPI({
  // TODO: fill this in
});

// TODO: implement the solution
// NOTE: check out the caccl-api docs at bit.ly/caccl-api
```

<!-- Start Example -->
<details>
<summary>Example Result</summary>
<pre>
// Import caccl-api
import initAPI from 'caccl-api';

// Initialize the API
const api = initAPI({
  <b>canvasHost: 'canvas.harvard.edu',</b>
  <b>accessToken: '1895~sdjfoa9me098fjoiasnudo8f7am9sod8ufnoaisdunfkuasdf',</b>
  <b>defaultCourseId: 53450,</b>
});

<b>// In parallel, get course content</b>
<b>const [</b>
  <b>pages,</b>
  <b>assignments,</b>
  <b>discussionTopics,</b>
<b>] = await Promise.all([</b>
  <b>// List pages</b>
  <b>api.course.page.list(),</b>
  <b>// List assignments</b>
  <b>api.course.assignment.list(),</b>
  <b>// List discussion topics</b>
  <b>api.course.discussionTopic.list(),</b>
<b>]);</b>
</pre>
</details>
<!-- End Example -->

<Exercise>
  Run two tasks in parallel: 1. create a unique assignment and then get the list of assignments, 2. create a unique page and then get the list of pages
</Exercise>

```ts
// Import caccl-api
import initAPI from 'caccl-api';

// Initialize the API
const api = initAPI({
  // TODO: fill this in
});

// TODO: implement the solution
// NOTE: check out the caccl-api docs at bit.ly/caccl-api
```

<!-- Start Example -->
<details>
<summary>Example Result</summary>
<pre>
// Import caccl-api
import initAPI from 'caccl-api';

// Initialize the API
const api = initAPI({
  <b>canvasHost: 'canvas.harvard.edu',</b>
  <b>accessToken: '1895~sdjfoa9me098fjoiasnudo8f7am9sod8ufnoaisdunfkuasdf',</b>
  <b>defaultCourseId: 53450,</b>
});

<b>/**</b>
 <b>* Create a unique test assignment within the sandbox course</b>
 <b>* @author Gabe Abrams</b>
 <b>* @returns assignment object that was created</b>
 <b>*/</b>
<b>const createTestAssignment = async () => {</b>
  <b>// Generate a unique assignment name</b>
  <b>const uniqueAssignmentName = `Test Assignment [${Date.now()}-${Math.random()}]`;</b>

  <b>// Create an assignment</b>
  <b>const assignment = await api.course.assignment.create({</b>
    <b>name: uniqueAssignmentName,</b>
    <b>submissionTypes: ['none'],</b>
    <b>published: true,</b>
  <b>});</b>

  <b>// Return the new assignment</b>
  <b>return assignment;</b>
<b>};</b>

<b>/**</b>
 <b>* Create a unique test page within the sandbox course</b>
 <b>* @author Gabe Abrams</b>
 <b>* @returns page object that was created</b>
 <b>*/</b>
<b>const createTestPage = async () => {</b>
  <b>// Generate a unique page title</b>
  <b>const uniquePageTitle = `Test Page [${Date.now()}-${Math.random()}]`;</b>

  <b>// Create a page</b>
  <b>const page = await api.course.pages.create({</b>
    <b>title: uniquePageTitle,</b>
    <b>body: 'This is a test page.',</b>
    <b>published: true,</b>
  <b>});</b>

  <b>// Return the new assignment</b>
  <b>return assignment;</b>
<b>};</b>

<b>// Run create + list tasks in parallel</b>
<b>const [</b>
  <b>assignments,</b>
  <b>pages,</b>
<b>] = await Promise.all([</b>
  <b>// Create an assignment and then get the list of assignments</b>
  <b>(async () => {</b>
    <b>// Create an assignment</b>
    <b>await createTestAssignment();</b>

    <b>// Get the list of assignments</b>
    <b>const assignments = await api.course.assignment.list();</b>

    <b>// Return the list of assignments</b>
    <b>return assignments;</b>
  <b>})(),</b>
  <b>// Create a page and then get the list of pages</b>
  <b>(async () => {</b>
    <b>// Create a page</b>
    <b>await createTestPage();</b>

    <b>// Get the list of pages</b>
    <b>const pages = await api.course.page.list();</b>

    <b>// Return the list of pages</b>
    <b>return pages;</b>
  <b>})(),</b>
<b>]);</b>
</pre>
</details>
<!-- End Example -->

### Error Handling

With asynchronous code, error handling is nearly the same: simply wrap your code in a `try/catch` block:

```ts
// Async task that doesn't return anything
try {
  await doAsyncTask();
} catch (err) {
  // Handle error
}

// Async task that returns something
let userEmail: string;
try {
  userEmail = await getUserEmail();
} catch (err) {
  // Handle error
}
```

The most important thing to remember is that asynchronous tasks must be _awaited from inside the try/catch_ otherwise, code execution will continue and leave the `try/catch` block before the error occurs.

When handling errors that occur in `Promise.all` parallel execution, it's important to note that `Promise.all` throws an error immediately as soon as any of the promises passed into it throw an error. If an error occurs, only the first error will be thrown by `Promise.all`. Other tasks will continue to execute, but their results will be ignored.

If you don't want all of the tasks in the `Promise.all` to be ignored if one of the tasks encounters an error, simply group them together and wrap the internal tasks with `try/catch` blocks. The best way to explain this is by example:

Here's what it would look like if we wanted the code to quit if any of the tasks fail:

```ts
try {
  const [
    pages,
    assignments,
    serverList,
  ] = await Promise.all([
    api.course.page.list(),
    api.course.assignment.list(),
    getListOfServers(),
  ]);
} catch (err) {
  // Handle error
}
```

However, let's say that we want it to work such that if one of two first Canvas-based tasks fails, we don't want the `getListOfServers` task to be ignored. We could separate the Canvas-based tasks into a separate asynchronous function and handle the error within that function:

```ts
/**
 * Load pages and assignments. If a failure occurs, instead of failing, we
 *   will return an empty array
 * @author Gabe Abrams
 * @returns pages and assignments
 */
const loadCanvasData = async () => {
  try {
    const [
      pages,
      assignments,
    ] = await Promise.all([
      api.course.page.list(),
      api.course.assignment.list(),
    ]);

    return {
      pages,
      assignments,
    };
  } catch (err) {
    return {
      pages: [],
      assignments: [],
    };
  }
};

try {
  const [
    canvasData,
    serverList,
  ] = await Promise.all([
    loadCanvasData(),
    getListOfServers(),
  ]);

  const {
    pages,
    assignments,
  } = canvasData;
} catch (err) {
  // Handle error
}
```

If the tasks are simple and it's convenient to put the asynchronous task inline, you can skip the step of creating a named function by instead creating an anonymous function and immediately calling it:

```ts
try {
  const [
    canvasData,
    serverList,
  ] = await Promise.all([
    (async () => {
      try {
        const [
          pages,
          assignments,
        ] = await Promise.all([
          api.course.page.list(),
          api.course.assignment.list(),
        ]);

        return {
          pages,
          assignments,
        };
      } catch (err) {
        return {
          pages: [],
          assignments: [],
        };
      }
    })(),
    getListOfServers(),
  ]);

  const {
    pages,
    assignments,
  } = canvasData;
} catch (err) {
  // Handle error
}
```

### Callbacks

Refrain from using callbacks unless absolutely necessary. If it's a lib function that requires a callback, wrap it in a helper and then use the helper.

<Rule>
  Refrain from using callbacks. If a lib requires one, wrap and forget it
</Rule>

```ts
// Bad:
setTimeout(task, 1000);

// Good:
/**
 * Wait for a specific amount of time
 * @author Gabe Abrams
 * @param msToWait the number of ms to wait before continuing
 */
const waitFor = async (msToWait: number) => {
  return new Promise((resolve) => {
    setTimeout(resolve, msToWait);
  });
};

await waitFor(1000);
task();
```

# React

All our front-end development are done within the React framework. We pair React with Tailwind for styling:

- [Tailwind](https://tailwindcss.com/)

## Organize the Project

We organize our React projects with the following file structure:

```ts
the-wily-network/src/
  main.tsx // Entry point
  App.tsx // Main component
  components/
    AdminHomePage/
      InnerComplicatedComponent/
        index.tsx
      innerSimpleComponent.tsx
      index.tsx // Main page that imports components
    StudentHomePage/
      index.tsx
    ...
  styles/
    index.css // Main shared stylesheet
  types/
    Student.ts
    Admin.ts
    WishList.ts
    ...
```

## Create a Component

Here is an example component template - this is definetly overkill but generally a good structure to follow.

```ts
/**
 * Add component description
 * @author Add Your Name
 */

// Import React
import React, { useReducer, useEffect, useRef } from 'react';

// Import FontAwesome
import { FontAwesomeIcon } from '@fortawesome/react-fontawesome';
import { faCheck } from '@fortawesome/free-solid-svg-icons';

// Import shared helpers
import addHelperName from './addHelperFilename';

// Import shared constants
import ADD_CONSTANT_NAME from './addConstantFilename';

// Import shared types
import AddSharedTypeName from './AddSharedTypeFilename';

// Import shared components
import AddSharedComponentName from './AddSharedComponentFilename';

// Import helpers
import addHelperName from './addHelperFilename';

// Import constants
import ADD_CONSTANT_NAME from './addConstantFilename';

// Import types
import AddTypeName from './AddSharedTypeFilename';

// Import components
import AddComponentName from './AddComponentFilename';

// Import style
import './AddNameOfStylesheet.scss';

/*------------------------------------------------------------------------*/
/* -------------------------------- Types ------------------------------- */
/*------------------------------------------------------------------------*/

// Props definition
type Props = {
  // Add description of required prop
  addPropName: addPropType,
  // Add description of optional prop
  addPropName?: addPropType,
};

// Add description of custom type
type AddCustomTypeName = {
  // Add description of property
  addCustomPropName: addCustomPropType,
};

/*------------------------------------------------------------------------*/
/* ------------------------------ Constants ----------------------------- */
/*------------------------------------------------------------------------*/

// Add description of constant
const ADD_CONSTANT_NAME = 'add constant value';

/*------------------------------------------------------------------------*/
/* -------------------------------- State ------------------------------- */
/*------------------------------------------------------------------------*/

/* -------------- Views ------------- */

enum View {
  // Add description of view
  AddViewName = 'AddViewName',
}

/* -------- State Definition -------- */

type State = (
  | {
    // Current view
    view: View.AddViewName,
    // Add description of require state variable
    addStateVariableName: addStateVariableValue,
    // Add description of optional state variable
    addStateVariableName?: addStateVariableValue,
  }
  | {
    // Current view
    view: View.AddViewName,
    // Add description of require state variable
    addStateVariableName: addStateVariableValue,
    // Add description of optional state variable
    addStateVariableName?: addStateVariableValue,
  }
);

/* ------------- Actions ------------ */

// Types of actions
enum ActionType {
  // Add description of action type
  AddActionTypeName = 'AddActionTypeName',
}

// Action definitions
type Action = (
  | {
    // Action type
    type: ActionType.AddActionTypeName,
    // Add description of required payload property
    addPayloadPropertyName: addPayloadPropertyType,
    // Add description of optional payload property
    addPayloadPropertyName?: addPayloadPropertyType,
  }
  | {
    // Action type
    type: (
      | ActionType.AddActionTypeWithNoPayload
      | ActionType.AddActionTypeWithNoPayload
    ),
  }
);

/**
 * Reducer that executes actions
 * @author Add Your Name
 * @param state current state
 * @param action action to execute
 * @returns updated state
 */
const reducer = (state: State, action: Action): State => {
  switch (action.type) {
    case ActionType.AddActionType: {
      return {
        ...state,
        addStateVariableName: addStateVariableNewValue,
      };
    }
    default: {
      return state;
    }
  }
};

/*------------------------------------------------------------------------*/
/* --------------------------- Static Helpers --------------------------- */
/*------------------------------------------------------------------------*/

/**
 * Add description of helper
 * @author Add Your Name
 * @param addArgName add arg description
 * @param addArgName add arg description
 * @returns add return description
 */
const addHelperName = (
  addRequiredArgName: addRequiredArgType,
  addOptionalArgName?: addOptionalArgType,
  addOptionalArgWithDefaultName?: addOptionalArgType = addArgDefault,
): addReturnType => {
  // TODO: implement
};

/*------------------------------------------------------------------------*/
/* ------------------------------ Component ----------------------------- */
/*------------------------------------------------------------------------*/

const AddComponentName: React.FC<Props> = (props) => {
  /*------------------------------------------------------------------------*/
  /* -------------------------------- Setup ------------------------------- */
  /*------------------------------------------------------------------------*/

  /* -------------- Props ------------- */

  // Destructure all props
  const {
    addRequiredPropName,
    addOptionalPropName = 'add default value of prop',
  } = props;

  /* -------------- State ------------- */

  // Initial state
  const initialState: State = {
    addStateVariableName: 'add state variable initial value',
  };

  // Initialize state
  const [state, dispatch] = useReducer(reducer, initialState);

  // Destructure common state
  const {
    addStateVariableName,
    addStateVariableName,
  } = state;

  /* -------------- Refs -------------- */

  // Initialize refs
  const addRefName = useRef<AddRefType>(null);

  /*------------------------------------------------------------------------*/
  /* ------------------------- Component Functions ------------------------ */
  /*------------------------------------------------------------------------*/

  /**
   * Add component helper function description
   * @author Add Your Name
   * @param addArgName add description of argument
   * @param [addOptionalArgName] add description of optional argument
   * @returns add description of return
   */
  const addComponentHelperFunctionName = (
    addArgName: addArgType,
    addOptionalArgName?: addOptionalArgType,
  ): addReturnType => {
    // TODO: implement
  };

  /*------------------------------------------------------------------------*/
  /* ------------------------- Lifecycle Functions ------------------------ */
  /*------------------------------------------------------------------------*/

  /**
   * Mount
   * @author Add Your Name
   */
  useEffect(
    () => {
      (async () => {
        // TODO: implement
      })();
    },
    [],
  );

  /**
   * Update (also called on mount)
   * @author Add Your Name
   */
  useEffect(
    () => {
      // TODO: implement
    },
    [addTriggerVariable],
  );

  /**
   * Unmount
   * @author Add Your Name
   */
  useEffect(
    () => {
      return () => {
        // TODO: implement
      };
    },
    [],
  );

  /*------------------------------------------------------------------------*/
  /* ------------------------------- Render ------------------------------- */
  /*------------------------------------------------------------------------*/

  /*----------------------------------------*/
  /* ---------------- Modal --------------- */
  /*----------------------------------------*/

  // Modal that may be defined
  let modal: React.ReactNode;

  /* ------- AddFirstTypeOfModal ------ */

  if (addLogicToDetermineIfModalIsVisible) {
    // TODO: implement

    // Create modal
    modal = (
      <Modal
        key="unique-modal-key"
        ...
      />
    );
  }

  /*----------------------------------------*/
  /* ---------------- Views --------------- */
  /*----------------------------------------*/

  // Body that will be filled with the current view
  let body: React.ReactNode;

  /* -------- AddFirstViewName -------- */

  if (view === View.AddViewName) {
    // TODO: implement

    // Create body
    body = (
      <addJSXOfBody />
    );
  }

  /* -------- AddSecondViewName -------- */

  if (view === View.AddViewName) {
    // TODO: implement

    // Create body
    body = (
      <addJSXOfBody />
    );
  }

  /*----------------------------------------*/
  /* --------------- Main UI -------------- */
  /*----------------------------------------*/

  return (
    <addContainersForBody>
      {/* Add Modal */}
      {modal}

      {/* Add Body */}
      {body}
    </addContainersForBody>
  );
};

/*------------------------------------------------------------------------*/
/* ------------------------------- Wrap Up ------------------------------ */
/*------------------------------------------------------------------------*/

// Export component
export default AddComponentName;

```

## Component Development Practices

The template above is highly involved, so let's break it down into pieces. Remember that you can leave any sections out if they are irrelevant. For example, if your component does not have any state, leave out the entire section.

Let's go from top to bottom.

### Documentation

We use JSDoc to document each file and every single function. Add one or more author tags to every single JSDoc entry.

Here's an example for a forgot password button:

<Rule>
  Add JSDoc to the top of every component file, describing the component
</Rule>

```ts
/**
 * Button that shows the "forgot password" panel
 * @author Divardo Calicci
 */
```

<Rule tall>
  Add JSDoc to the top of every named function
</Rule>

### Git Norms

**Commit frequently**. We will squash later, but it's nice to have a detailed history. Plus, this is great for your careers.

### CSS Names

<Rule>
  When naming css classes, always prefix every class with the name of the component
</Rule>

```css
/* For component Favorite Fruits: */

/* Good: */
.FavoriteFruits-container

/* Bad: */
.container
```

### CSS Units

We prefer **rem** for elements that have the same sizing, independent of their context (independent of their parent styling and size).

We prefer **em** for elements that have variable sizing where their sizing depends on their parent or context.

Why? When people customize their browser settings (fonts, font size, viewport settings, etc.) it will mess up your layout and create unexpected layouts. Plus, this makes your tool more accessible (it adapts better to user settings).

<Rule tall>
  Use rem or em units instead of px units
</Rule>

### Imports

We aggressively divide imports by type because components often end up with many imports.

First, we import libraries such as `react`. Then, we import any local files

<Rule>
  Import libraries before importing any local modules
</Rule>

```ts
// Import Lib
import Lib from 'lib';

// Import AnotherLib
import AnotherLib from 'another-lib';

// Import LocalModule
import LocalModule from 'local-module';
```

Additionally, we divide all local modules into categories. Up first are shared imports (items that are also imported by other modules), then we have non-shared imports (items that are not imported by any other module). We divide each of these into sub-categories: helpers, constants, types, and components.

<Rule>
  Group local imports
</Rule>

```ts
// Import shared helpers
import addHelperName from './addHelperFilename';

// Import shared constants
import ADD_CONSTANT_NAME from './addConstantFilename';

// Import shared types
import AddSharedTypeName from './AddSharedTypeFilename';

// Import shared components
import AddSharedComponentName from './AddSharedComponentFilename';

// Import helpers
import addHelperName from './addHelperFilename';

// Import constants
import ADD_CONSTANT_NAME from './addConstantFilename';

// Import types
import AddTypeName from './AddSharedTypeFilename';

// Import components
import AddComponentName from './AddComponentFilename';
```

Finally, always import resources (images, etc.) and stylesheets last. These are the only imports that can include file extensions.

<Rule>
  Import the stylesheet last
</Rule>

```ts
// Import style
import './AddNameOfStylesheet.scss';
```

<Rule tall>
  Only stylesheet and resource imports can include file extensions
</Rule>

### Types

The first type in your types section must always be your `Props` (if your component has any).

<Rule tall>
  Props must be at the top of the "Types" section
</Rule>

Remember that optional props must be marked with the `?` symbol. We put default props in the "Set Up" section inside of the component itself, so leave out the defaults here.

Example:

```ts
// Props definition
type Props = {
  // User's first name
  userFirstName: string,
  // User's last name
  userLastName: string,
  // True if the user is a teacher
  isTeacher?: boolean,
  // Handler for when the user wants to log in
  onLogInClicked?: () => void,
};
```

### Constants

All constants are named with all caps, words separated by underscores. We do this because the `const` keyword is ubiquitous throughout our code, so `const` does not always indicate that something is a module constant.

<Rule>
  Constants use ALL_CAPS_NAMING
</Rule>

```ts
// Duration of fade out animation
const FADE_OUT_DURATION = 1500; // ms
```

Remember that all numbers must include their units.

<Exercise tall>
  Create a simple button component that takes a label, onClick function, variant, and ariaLabel as props
</Exercise>

### State

You may be familiar with the React `useState` hook. We take a more rigorous approach to component state, always requiring that state be managed by reducers. This forces us to keep our views and controllers separate. Thus, we achieve a fully separate MVC design.

<Rule tall>
  Use reducers to manage state
</Rule>

For components that have different views, define a `View` enum and base state definitions on the view. In our example, the component is a checkout panel.

<Rule>
  Create a View enum for components that have more than one view
</Rule>

```ts
enum View {
  // View the cart
  Cart = 'Cart',
  // Add shipping and billing information
  ShippingAndBillingForm = 'ShippingAndBillingForm',
  // Review order details and confirm
  Review = 'Review',
}
```

Then, base the sate off of views. Each view should have a separate state definition.

```ts
type State = (
  | {
    // Current view
    view: View.Cart,
    // List of items that are in the cart
    cart: Items[],
  }
  | {
    // Current view
    view: View.ShippingAndBillingForm,
    // List of items that are being purchased
    cart: Items[],
    // Shipping information
    shippingInformation: {
      // Shipping address
      address: Address,
      // Delivery instructions
      deliveryInstructions: string,
      // Phone number
      phone: PhoneNumber,
    },
    // Billing information
    billingInformation: (
      | {
        // True if same as shipping information
        sameAsShippingInformation: true,
      }
      | {
        // True if same as shipping information
        sameAsShippingInformation: false,
        // Billing address
        address: Address,
        // Phone number
        phone: PhoneNumber,
      }
    ),
  }
  | {
    // Current view
    view: View.Review
    // Identifier of the pending transaction
    transactionId: string,
    // True if the user has accepted the terms
    termsAccepted: boolean,
  }
);
```

If the component only has one view, leave out the `View` enum and create a state that has only one form:

```ts
type State = {
  // List of email recipients
  recipients: EmailAddress[],
  // List of CC recipients
  ccRecipients?: EmailAddress[],
  // Text typed into the email subject line
  subject: string,
  // Text typed into the body of the email
  body: string,
  // True if the "sending" indicator is visible
  sending: boolean,
};
```

We use reducers to manage state. That means that all state updates are handled through actions. This helps us to abstract away state updates, and helps state updates to be more reusable.

First, we create an `ActionType` enum that defines all of the types of actions that can be dispatched.

<Rule>
  All actions must have a separate ActionType
</Rule>

```ts
// Types of actions
enum ActionType {
  // Add a recipient to the email
  AddRecipient = 'AddRecipient',
  // Update the subject of the email
  UpdateSubject = 'UpdateSubject',
  // Reset the entire email form
  ResetForm = 'ResetForm',
  // Show the "email is being sent" indicator
  ShowSendingIndicator = 'ShowSendingIndicator',
}
```

Then, define the type of each action object. If the action has any payload properties, give it a separate Action type definition. Then, group all actions that have no payload at the bottom into one shared type definition.

<Rule>
  Define every action type with payload separately, group payload-less actions
</Rule>

```ts
// Action definitions
type Action = (
  | {
    // Action type
    type: ActionType.AddRecipient,
    // Email address of the recipient
    recipient: EmailAddress,
  }
  | {
    // Action type
    type: ActionType.UpdateSubject,
    // New text in the subject line
    subject: string,
  }
  | {
    // Action type
    type: (
      | ActionType.ResetForm
      | ActionType.ShowSendingIndicator
    ),
  }
);
```

Finally, create a reducer that executes the state updates. This function can get quite involved, so remember to keep it very organized. If using the spread operator (`...`) to merge state, always put `...state` as the first element in the list so properties are overwritten.

```ts
/**
 * Reducer that executes actions
 * @author Divardo Calicci
 * @param state current state
 * @param action action to execute
 * @returns updated state
 */
const reducer = (state: State, action: Action): State => {
  switch (action.type) {
    case ActionType.AddRecipient: {
      return {
        ...state,
        recipients: [...state.recipients, action.recipient],
      };
    }
    case ActionType.UpdateSubject: {
      return {
        ...state,
        subject: action.subject,
      };
    }
    case ActionType.ResetForm: {
      return {
        recipients: [],
        ccRecipients: [],
        subject: '',
        body: '',
        sending: false,
      };
    }
    case ActionType.ShowSendingIndicator: {
      return {
        ...state,
        sending: true,
      };
    }
    default: {
      return state;
    }
  }
};
```

Switch statements in Typescript (and Javascript) share a block scope, so it can get very confusing to reason about logic. Thus, we wrap each case in a closure.

<Rule>
  Switch cases must be wrapped in curly brace closures
</Rule>

```ts
// Bad:
switch (expression) {
  case value1:
    ...
  case value2:
    ...
  default:
    ...
}

// Good:
switch (expression) {
  case value1: {
    ...
  }
  case value2: {
    ...
  }
  default: {
    ...
  }
}
```

If some of your actions can only be dispatched from within specific views, break your reducer into multiple sections surrounded with `if` statements:

```ts
/**
 * Reducer that executes actions
 * @author Divardo Calicci
 * @param state current state
 * @param action action to execute
 * @returns updated state
 */
const reducer = (state: State, action: Action): State => {
  /* --------- Assignment List -------- */
  
  if (state.view === View.AssignmentList) {
    switch (action.type) {
      case ActionType.FilterAssignments: {
        ...
      }
      default: {
        return state;
      }
    }
  }

  /* ------------ Page List ----------- */

  if (state.view === View.PageList) {
    switch (action.type) {
      case ActionType.FilterPages: {
        ...
      }
      default: {
        return state;
      }
    }
  }

  /* ------------- Default ------------ */

  return state;
};
```

<Exercise tall>
  Create a closeable alert that becomes invisible after being closed
</Exercise>

### Static Helpers

If logic can be removed from the component because it does not depend on state or props, either create a small static helper or move the logic to another file and import it under "Import Helpers".

<Rule tall>
  Static helpers and imported helpers should not heavily rely on state or props
</Rule>

Otherwise, static helpers follow usual rules: add JSDoc, types, etc.

```ts
/**
 * Get time of day
 * @author Divardo Calicci
 * @param timezone timezone of the current user
 * @returns text describing the time of day
 */
const getTimeOfDay = (timezone: Timezone): string => {
  ...
};
```

### Component Setup

The first thing that happens inside the component function is labeled "Setup" and it contains initialization for the props and state.

First, destructure props and include default props directly inline.

```ts
// Destructure all props
const {
  name,
  email,
  age,
  isTeacher = false,
  profileColor = Color.Blue,
} = props;
```

Then, define the initial state. In this way, default props and state are right next to each other and easy to find.

```ts
// Initial state
const initialState: State = {
  isOnline: false,
};
```

Then, initialize the state and destructure all state variables that are shared amongst all forms of the state.

```ts
// Initialize state
const [state, dispatch] = useReducer(reducer, initialState);

// Destructure common state
const {
  isOnline,
} = state;
```

Finally, initialize refs (if you have any).

```ts
// Initialize refs
const inputElem = useRef<HTMLInputElement>(null);

...

<input ref={inputElem} ...
```

To get the element attached to a ref, use `inputElem.current`.

### Lifecycle Functions

React programmers often speak about the "lifecycle" of a component. When a component first is included in the UI, we say that the component is "Mounted". Then, when the props or state change, we say that the component "Updated". Note that when the component first receives its props and state (during the mount step), we also consider this as an update. Finally, when the component leaves the UI, we say that the component is "Unmounted". We use three different types of lifecycle functions if we want to trigger code when one of these lifecycle states occurs.

#### Mount

To trigger code when the component mounts, we add a `useEffect(handler, [])` hook.

```ts
/**
 * Mount
 * @author Divardo Calicci
 */
useEffect(
  () => {
    // TODO: implement
  },
  [],
);
```

The "Mount" lifecycle function is great for running any asynchronous loading code (example: API request). If your code is asynchronous, wrap it in an anonymous async function. This trick works for any other lifecycle function, but we will only show it used here.

```ts
/**
 * Mount
 * @author Divardo Calicci
 */
useEffect(
  () => {
    (async () => {
      // Check if the user is online
      const { isOnline } = await getUserState();

      // Update the sate
      dispatch({
        type: ActionType.CHANGE_USER_STATUS,
        isOnline,
      });
    })();
  },
  [],
);
```

#### Update

To trigger code when a prop or state variable changes, we use a `useEffect(handler, [trigger])` hook. The trigger array can be one or more props and/or state variables that will cause the handler to be called. We recommend keeping your trigger array as concise as possible.

```ts
/**
 * Update (also called on mount)
 * @author Divardo Calicci
 */
useEffect(
  () => {
    // Play a "message received" sound
    audioPlayer.play(Sound.MessageReceived);
  },
  [messages],
);
```

If you need multiple different "Update" lifecycle functions with different triggers, add multiple "Update" functions, each with a different trigger array.

You may hear about another usage for the `useEffect` hook where the trigger array is left out completely: `useEffect(handler)`, which corresponds to a trigger that happens whenever _anything_ changes. Refrain from using this hook unless it's absolutely necessary. Usually, if you want to use this hook, that means that either you are doing logic that will need to happen every render (so it might as well be part of the render function), or your logic doesn't need to be run that frequently (so you should be more careful with when your logic runs, which you do by adding a trigger array).

<Rule tall>
  Always include a trigger array with the useEffect hook
</Rule>

#### Unmount

To trigger code when a component leaves the UI, we return a handler function within a `useEffect(handler, [])` hook. This is a great lifecycle function for cleanup.

```ts
/**
 * Unmount
 * @author Divardo Calicci
 */
useEffect(
  () => {
    return () => {
      // Save the user's changes
      saveChanges();
    };
  },
  [],
);
```

<Exercise tall>
  Create an app that lists the assignments in the course and allows the user to delete an assignment
</Exercise>

#### useEffect Hook

In each of the lifecycle functions we learned above, you'll see effective usage of the `useEffect` hook, which is one of the more complex hooks. It's not necessary that you fully understand this hook in order to do software development at DCE, but it's a good hook to understand. Thus, we'll go over it in some detail just for fun. This is a slightly simplified and modified description, see the docs for full detail.

The `useEffect` hook is used to watch for changes to prop variables (so we can make updates when prop variables change) and also to watch for destruction of such variables (we we can do cleanup). Here's how it works:

`useEffect` takes two arguments. The first argument is the effect function that is called when the changes are detected. The second argument is the list of prop variables to watch.

When any of the prop variables in the list change, the effect function is called. Also, on mount, those prop variables go from not existing to having values (that counts as a change), so the effect function is called on mount. The effect function contains the code that React should run when the changes are detected, and that is quite straightforward. But, the effect function also does something a little tricky: it's allowed to return another function (a cleanup function) that will be called when the component unmounts (this is a simplification).

Let's go through a few examples to make sense of this:

```ts
useEffect(
  () => {
    console.log('Hello!');
  },
  [],
);
```

In the example above, the array of prop variables to watch is empty. Thus, the effect function will be called on mount (because it's always called on mount) but will not be triggered at any point afterward. The effect function contains just a console.log and does not return a cleanup function, so there is no code here that will be called upon unmount. That's why we consider this `useEffect` usage to be a "Mount" function.

```ts
useEffect(
  () => {
    console.log('Hello!');
  },
  [users],
);
```

In the example above, the array of prop variables contains the "users" prop. Thus, the effect function will be called on mount and will also be called whenever the "users" prop changes value. The effect function contains just a console.log and does not return a cleanup function, so there is no code here that will be called upon unmount. That's why we consider this `useEffect` usage to be an "Update" function.

```ts
useEffect(
  () => {
    return () => {
      console.log('Hello!');
    };
  },
  [],
);
```

In the example above, the array of prop variables to watch is empty. Thus, the effect function will be called on mount (because it's always called on mount) but will not be triggered at any point afterward. The effect function only contains a return statement and does not run any other code, so in effect, there is no code to run on mount but there is code to run on unmount (the returned function will be called on unmount). That's why we consider this `useEffect` usage to be an "Unmount" function.

At DCE, these are the only three usages that we'll allow for `useEffect`, but at other organizations they may allow much more complex `useEffect` implementations. We keep things simple and clear for understandability and readability.

<Rule tall>
  Only use the "useEffect" hook statements that are listed in the template
</Rule>

### Render

You may have noticed that we separate sections of our code with comment blocks. Aside from the usual very large and wide comment block delimiting sections of the code, we use two smaller types of comment blocks to organize our render functions.

Medium blocks to separate parts of the UI:

```ts
/*----------------------------------------*/
/* ---------------- Modal --------------- */
/*----------------------------------------*/
```

And line comments to organize different types of that part of the UI:

```ts
/* ----------- Error Modal ---------- */
```

```ts
/* ------- Confirmation Modal ------- */
```

<Rule tall>
  Use comment blocks and lines to organize render code
</Rule>

When rendering views, it is okay to use `if` statements along with the `view` state variable (instead of `if` `else if` logic) because this keeps our code separate and readable.

At the end of the component's render code, there should be just one return statement that returns the main UI.

<Rule>
  Components can have only one return statement
</Rule>

```tsx
/*----------------------------------------*/
/* --------------- Main UI -------------- */
/*----------------------------------------*/

return (
  <div className="EmailForm-outer-container">
    {/* Add Modal */}
    {modal}

    {/* Add Body */}
    {body}
  </div>
);
```

### Wrap Up

This final section is usually very short. Put any final export logic here.

```ts
// Export component
export default EmailForm;
```

<Rule tall>
  Default export must happen at the end of the file on one line
</Rule>

<Rule>
  Default export cannot directly export a value
</Rule>

```ts
// Bad:
export default 50;

// Bad:
export default {
  ...
};

// Good:
export default myVariableName;

// Good:
export default MyClass;
```

## Writing JSX

Writing JSX code takes some getting used to. In many cases, it looks and feels just like HTML, but on certain cases, it differs in very small ways. Let's go through JSX by reviewing some of my favorite tips.

### Injecting Typescript

JSX is a combination of HTML and Typescript. The most important thing you'll learn about JSX is how to inject typescript into html. Typescript is always surrounded by `{...}` within our JSX blocks. Let's learn through examples:

Add a dynamically generated template string for the button aria-label:

```jsx
<button
  type="button"
  className="btn btn-warning"
  aria-label={`log out ${currentUserName}`}
>
  Log Out
</button>
```

Add a variable as the value for an onClick function:

```jsx
<button
  type="button"
  className="btn btn-warning"
  onClick={logOut}
>
  Log Out
</button>
```

Add an inline function that's called when the user clicks a button:

```jsx
<button
  type="button"
  className="btn btn-warning"
  onClick={() => {
    console.log('Logging out now!');
  }}
>
  Log Out
</button>
```

This works for props and also normal html contents:

```jsx
<button
  type="button"
  className="btn btn-warning"
>
  Log Out
  {' '}
  {numActiveUsers}
  {' '}
  Users
</button>
```

Any typescript can be placed inside the `{...}`, for example, math:

```jsx
<button
  type="button"
  className="btn btn-warning"
>
  Log Out
  {' '}
  {numActiveUsers + 1}
  {' '}
  Users
</button>
```

We can also use conditional logic, just like usual in typescript:

```jsx
<button
  type="button"
  className="btn btn-warning"
>
  {
    numActiveUsers === 1
      ? 'Log Out Current User'
      : `Log Out ${numActiveUsers} Users`
  }
</button>
```

### Classes

Instead of using `class="..."`, we use `className="..."` in JSX.

### Events

In HTML, event handlers are named in all lowercase like `onmousedown` but in JSX, we use camel case like `onMouseDown`.

### Spaces in JSX

To add a normal breaking space, use `{' '}` on its own line.

To add a non-breaking space, use `&nbsp;`.

### Quotes and Other Symbols

To keep our JSX clean and to help with rendering, we always encode symbols.

<Rule tall>
  Always encode symbols in JSX
</Rule>

Here are a few for reference:

- `&` becomes `&amp;`
- `<` becomes `&lt;`
- `>` becomes `&gt;`
- `"` becomes `&quot;`
- `'` becomes `&apos;`
- `¢` becomes `&cent;`
- `©` becomes `&copy;`
- `®` becomes `&reg;`

### Modals

All modals should be `dce-reactkit` modals with unique keys.

<Rule>
  All modals must have unique keys
</Rule>

```ts
<Modal
  key="unique-modal-key"
  ...
/>
```

### FontAwesome Icons

To add a FontAwesome icon, make sure the icon is imported. For example, if we want a checkmark, we will import the `faCheck` icon:

```ts
// Import FontAwesome
import { FontAwesomeIcon } from '@fortawesome/react-fontawesome';
import { faCheck } from '@fortawesome/free-solid-svg-icons';
```

Usually, icon names are just the camelCase versions of the icon name, but autocomplete should help you here.

Then, when you want to use the icon, include it like this:

```html
<FontAwesomeIcon icon={faCheck} />
```

You can also add a `className` prop to `FontAwesomeIcon` for bootstrap styles:

```html
<FontAwesomeIcon
  icon={faCheck}
  className="m-2"
/>
```

### Self-closing Tags

In HTML, you may see a tag that has no contents:

```html
<div id="LoginButton-container"></div>
```

...but in JSX, we use self-closing tags:

```tsx
<div id="LoginButton-container" />
```

<Rule tall>
  Use self-closing tags for elements with no children
</Rule>

## Dispatching Actions

We spent a lot of time defining the state and reducer, but how do you dispatch an action to the reducer?

Simple: call the `dispatch` function and pass an object with a `type` property and any other payload properties that are defined for that action type.

```ts
dispatch({
  type: ActionType.UpdateSubject,
  subject: inputField.value,
});
```

## Design Principles

### Prefer Multiline Representations

Unless something in JSX has just one item, put it on multiple lines. This keeps our UI code very clean and readable.

<Rule>
  Prefer multiline JSX
</Rule>

```tsx
{/* Good */}
<div id="LoginButton-container" />

{/* Equally Good */}
<div
  id="LoginButton-container"
/>

{/* Bad */}
<div id="LoginButton-container" className="row" />

{/* Good */}
<div
  id="LoginButton-container"
  className="row"
/>
```

### One Language Per Line

In JSX file, we mix and match typescript and html code.

Unless you're embedding a single variable:

```tsx
<button
  onClick={handleClick}
  ...
```

...or you're embedding a single value:

```tsx
<button
  type="button"
  ...
```

...don't mix and match typescript and html code on the same line.

<Rule>
  Don't mix typescript and JSX
</Rule>

```tsx
{/* Bad: */}
<button
  onClick={() => { handleClick(); }}
  ...
/>

{/* Good: */}
<button
  onClick={() => {
    handleClick();
  }}
  ...
/>

{/* Bad: */}
<div className="Role-description">
  You are a {user.role} in the course.
</div>

{/* Good: */}
<div className="Role-description">
  You are a
  {' '}
  {user.role}
  {' '}
  in the course
</div>
```

### Shared State

If state must be shared between multiple components, put those state variables in the lowest common ancestor and pass state down to children via props.

This can cause what is called "prop drilling", where state is passed through multiple layers of children via their props. If this becomes particularly cumbersome, it might be one of the cases where we use a React Context Provider to create a shared state, but this needs to be a full team decision.

<Rule tall>
  Never create a React Context Provider without discussing with the rest of the team
</Rule>

### No Images

Unless absolutely necessary, never use images. Great alternatives are glyphs via `FontAwesome` or svg vector graphics. If you think that an image is required, discuss the situation with the team. We do this to aggressively keep our apps small in size. We have students all over the world, many with very slow internet connections, so load time is very important.

<Rule tall>
  Never use an image without discussing with the rest of the team
</Rule>

### "Fat" Reducers

You'll often hear the term "fat" vs "thin" reducers, which refers to whether logic is concentrated inside the reducer or outside the reducer, respectively. We love "fat" reducers. As much as possible, move logic into the reducer. In my opinion, "thin" reducers defeat the entire purpose of reducers. When writing "thin" reducers, you often create an entire action that just passes through state updates. In this case, you lose all of the benefits of abstraction that `useReducer` offers and you might as well just replace it with `useState`.

## Constant Modules

If you have shared constants, put them in a `constants/` folder either in `client/src/shared/` if they're shared across the whole app or put them directly in the folder for the current component if they're shared across a component and its children.

Constant modules are simple:

```tsx
// MAX_STUDENTS_PER_TABLE.tsx

/**
 * Maximum number of students allowed at a table
 * @author Divardo Calicci
 */
const MAX_STUDENTS_PER_TABLE = 500; // people

export default MAX_STUDENTS_PER_TABLE;
```

## Enum or Types Modules

If you have shared enums or types, put them in a `types/` folder either in `client/src/shared/` if they're shared across the whole app or put them directly in the folder for the current component if they're shared across a component and its children.

Type modules are simple:

```tsx
// Car.tsx

/**
 * Car type
 * @author Divardo Calicci
 */
type Car {
  // Company that made the car
  make: string,
  // Year that the car was manufactured
  year: number,
  // Color of the car
  color: AllowedColors,
}

export default Car;
```

Enum modules are simple:

```tsx
// AllowedColors.tsx

/**
 * Allowed paint colors for new cars
 * @author Divardo Calicci
 */
enum AllowedColors {
  Red = 'Red',
  Green = 'Green',
  Blue = 'Blue',
}

export default AllowedColors;
```

It seems like a lot of word to re-type the name of enum values in lowercase, but we do that for a good reason: it helps with readable serialization and database entries that are more debuggable and readable. Because this is so valuable, we require it.

<Rule>
  Enums must have string value unless the value's natural type is a number
</Rule>

```ts
// Bad:
enum AllowedColors {
  Red,
  Green,
  Blue,
}

// Good:
enum AllowedColors {
  Red = 'Red',
  Green = 'Green',
  Blue = 'Blue',
}

// Bad (allowed colors are not numbers)
enum AllowedColors {
  Red = 1,
  Green = 2,
  Blue = 3,
}

// Good (number of wheels is a number naturally)
enum VehicleWheelConfig {
  Bike = 2,
  Tricycle = 3,
  Car = 4,
  FlatbedTruck = 16,
}
```

## Helper Modules

If you have shared helpers, put them in a `helpers/` folder either in `client/src/shared/` if they're shared across the whole app or put them directly in the folder for the current component if they're shared across a component and its children.

Simply define the function and then export it.

```ts
// roundToTwoDecimals.tsx

/**
 * Round a number to two decimals
 * @author Divardo Calicci
 * @param num the number to round
 * @returns the rounded number
 */
const roundToTwoDecimals = (num: number) => {
  return (
    Math.round(
      num * 100
    )
    / 100
  );
};

export default roundToTwoDecimals;
```

### Use Bootstrap As Much As Possible

If Bootstrap has a class for the style or layout that you want to use, take advantage of Bootstrap. Check out the [Bootstrap docs](https://getbootstrap.com/docs/). They're great.

But if you must create a new style, put it in an associated `.scss` file. If that style is shared, see the next section on "Shared Styles"

## Shared Styles

If you have shared styles, put them in a `styles/` folder either in `client/src/shared/` if they're shared across the whole app or put them directly in the folder for the current component if they're shared across a component and its children.

Great candidates for these styles are:

- Shared classes like `btn-nostyle`
- Shared custom color variables
- Shared custom number variables

Generally, we try to limit the number of shared style because we use Bootstrap so much. But, as a team, we may put some shared styles into a `client/src/shared/styles/style.scss` file.

To import a stylesheet that includes variables that you'd like to use, do it with the `@use` command:

```scss
@use '../shared/styles/style.scss';
```

When defining variables, do so at the top of your scss file:

```scss
$border-width: 0.5rem;
```
