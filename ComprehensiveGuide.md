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

# Set Up Your Workspace

1. Install [Node.js](https://nodejs.org/en) (v20 or later) and npm.
2. Install the Vercel CLI (`npm install --global vercel`).
3. Copy this repo as a template and clone it onto your local machine.
4. Install all required packages by running `npm install`.
5. Start the dev server with `vercel dev` (log in with your Vercel account and create a linked project as required).

# Project and File Management

## Assigned Tasks

We use GitHub Projects as our task management system. To see what you're assigned, visit the repo, click `Projects`, click our project, and take a look at the `Assigned` column. Cards with your picture on them are yours to do this week.

When you start working on a task, drag the card to `In Progress`. 

When you finish a task and have a PR up, drag the card to `In Review`.

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
