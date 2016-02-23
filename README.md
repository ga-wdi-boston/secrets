[![General Assembly Logo](https://camo.githubusercontent.com/1a91b05b8f4d44b5bbfb83abac2b0996d8e26c92/687474703a2f2f692e696d6775722e636f6d2f6b6538555354712e706e67)](https://generalassemb.ly/education/web-development-immersive)

# Managing Production Secrets

Use this template to structure your READMEs for talks. Remove text from this
section, or use it to frame the talk you are giving. Good framing answers the
question "Why am I learning this?".

Be sure to include a recent [`LICENSE`](LICENSE) and Markdown linter
configuration ([`.remarkrc`](.remarkrc)). Also, include an appropriate
`.gitignore`; these are usually found in specific technology templates, for
example [js-template](https://www.github.com/ga-wdi-boston/js-template).

## Prerequisites

-   Topics with which developers should be familiar with.
-   Prerequisites are "just-in-time", so if I have a prerequisite that mentions
    Sass, I would **not** need to include CSS as a prerequisite.
-   [Links to previous materials](https://www.github.com/ga-wdi-boston/example)
    are often useful.

## Objectives

By the end of this, developers should be able to:

-   Write objectives that focus on demonstrating knowledge.
-   Write learning objectives that begin with an [imperative
    verb](https://en.wikipedia.org/wiki/Imperative_mood).
-   Avoid objectives that start with "Use" or "Understand".
-   Rewrite objecives that begin with "Use" by inverting sentence structure.
-   End each objective with a period.
-   Write objectives on the whiteboard so they can be referenced during a talk.

## Preparation

1.  [Fork and clone](https://github.com/ga-wdi-boston/meta/wiki/ForkAndClone)
    this repository.
1.  Install dependencies with `npm install`.

Better preparation instructions may be found as
[snippets](https://github.com/ga-wdi-boston/instructors/tree/master/snippets).

It's a good idea to have students do these steps while you're writing objectives
on the whiteboard.

## Managing Secrets

Next, if you don't have one already, create a `.gitignore` file. Heroku apps have environmental variables which live outside of the app, and you can set these either through the web interface or through the console (`heroku config`). In order to effectively simulate Heroku on our local machines, we'll also need those environmental variables. However, some of those variables will need to be secret! So, in addition to creating a new file to hold those variables, we'll need to make sure that it **_NEVER_** gets added to our commits.

> ****THIS IS VERY IMPORTANT! COMMITTING SECRETS CAN COST YOU THOUSANDS OF DOLLARS, AND POTENTIALLY YOUR JOB!****

Somewhere inside your `.gitignore`, add the following line: `.env`. Then, and _only then_, create a new file called `.env` in the root of your repo. Add the following content to it:

```bash
# Settings for production environment
SECRET_KEY_BASE= #(some secret key for production - generate it by running `RAILS_ENV=production rake secret`)
RACK_ENV=development
PORT=3000
```

As you can see from the comment above, in order to generate a secret key for our database, you'll need to run the command `RAILS_ENV=production rake secret`. This will spit out a long key into your console - copy the entire key and use it as the value of `SECRET_KEY_BASE`.

Once all of this is done, **check again** that Git is unaware of `.env` by running `git status` - if `.env` shows up on that list, stop what you're doing and get help, because you've done something wrong.

## Additional Resources

-   Any useful links should be included in the talk material where the link is
    first referenced.
-   Additional links for further study or exploration are appropriate in this
    section.
-   Links to important parts of documentation not covered during the talk, or
    tools tangentially used but not part of the focus of the talk, are also
    appropriate.

## [License](LICENSE)

Source code distributed under the MIT license. Text and other assets copyright
General Assembly, Inc., all rights reserved.
