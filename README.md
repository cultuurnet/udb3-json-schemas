# cultuurnet/apidocs

This repository contains all the API documentation hosted at https://docs.publiq.be.

The hosting is provided by https://stoplight.io, who provide a beautiful UI for our docs.

## Requirements ✔️

To contribute to our API documentation, some basic knowledge of [git](https://git-scm.com/) is required so you can commit your changes to a temporary branch and get them reviewed before they get published.

The following tools can also be helpful but are not strictly required:

- [Stoplight Studio](https://stoplight.io/studio/), a GUI editor for API documentation built by https://stoplight.io (where our documentation is hosted). However, any file editor is fine technically.
- [Node](https://nodejs.org/en/) and [Yarn](https://yarnpkg.com/getting-started/install) to run the automatic checks on your own machine, and to run the automatic fixer in case of problems. (Any recent version should be fine.) However, the automatic checks will also run in GitHub itself for every push, and you can also run the automatic fixer manually on GitHub.

## Getting started 🚀

Clone this repository to your local machine.
```
git clone git@github.com:cultuurnet/apidocs.git
```

## Contribution guidelines ✨

Anyone can contribute to our API documentation. To make the process as smooth as possible, please take the following guidelines into consideration:

*   Use [atomic commits](https://curiousprogrammer.dev/blog/why-i-create-atomic-commits-in-git/).
*   Use [good commit messages](https://cbea.ms/git-commit/). Avoid generic commit messages like `Updated example.md` or `PR remarks`.
*   Avoid big pull requests with a lot of changes that are not related to each other. If you need to add a lot of documentation, aim for incremental pull requests with small, specific scopes.
*   Create a [draft pull request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests#draft-pull-requests) if your changes are not ready for review yet but you want to open a pull request already.
*   Fill in the description of your pull request with the template that is automatically provided.

When your changes are ready, create a regular pull request or [mark your draft pull request as ready for review](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/changing-the-stage-of-a-pull-request#marking-a-pull-request-as-ready-for-review). One or more reviewers will automatically be assigned who will go over your changes and give feedback or approve them.

After the approval, the changes are usually expected to be merged by the pull request author (if they are in our organization). Pull requests from external forks will be merged by the reviewers.

## Adding a new project 🐣

Adding a new project involves multiple steps both in this git repository, as on https://docs.publiq.be.

Because some of these steps require special permissions, it is not possible to do this yourself. Instead, [create an issue](https://github.com/cultuurnet/apidocs/issues) with the following information:

*   **Human-readable name of your project.** This is the name that will appear in the menu on https://docs.publiq.be. For example `UiTdatabank`.
*   **A short tagline.** This will appear under the name of your project in the menu and must be under 35 characters to avoid an ellipsis. For example `Integrate with the UiTdatabank APIs`.
*   **A URL slug** for your project on https://docs.publiq.be. This will also be the name of your project's directory inside this repository. Avoid abbreviations, use lowercase characters, and `-` for spaces if needed. For example `uitdatabank`.
*   **A [fontawesome icon](https://fontawesome.com/icons) name** which will be displayed next to your project in the menu. For example `calendar-alt`.
*   **A hex color code** that will determine the color of your project's icon in the menu. For example `#EF1810`.

An admin will then add a new project for you.

## Project structure 🌿

Every project has its own space inside the `projects` directory with the same name as their URL slug on https://docs.publiq.be. For example:

```
projects/
├─ authentication/  # https://docs.publiq.be/docs/authentication
├─ errors/          # https://docs.publiq.be/docs/errors
├─ guidelines/      # https://docs.publiq.be/docs/guidelines
├─ uitdatabank/     # https://docs.publiq.be/docs/uitdatabank
├─ uitpas/          # https://docs.publiq.be/docs/uitpas
├─ widgets/         # https://docs.publiq.be/docs/widgets
├─ ...
```

Our documentation is hosted by [Stoplight](https://stoplight.io), which expects a specific directory structure:

```
projects/
├─ authentication/
│  ├─ assets/         # Contains all your static files
│  │  ├─ images/      # Contains all your images
│  ├─ docs/           # Contains all your .md files for guides
│  ├─ reference/      # Contains all your OpenAPI files (preferably .json)
│  ├─ toc.json        # Contains the config of your project's sidebar
├─ ...
```

It is important to adhere to this structure to avoid problems on the hosted version of our docs at https://docs.publiq.be or inside the Stoplight Studio editor.

## Opening your project in Stoplight Studio 🗂

If you are just starting out with API documentation in this repository, it is advised to work with the [Stoplight Studio](https://stoplight.io/studio/) editor.

When opening your project in Stoplight Studio, it is important to **open just your project**! If you instead open the whole repository, or the whole `projects` folder at once, Stoplight Studio will not correctly find your OpenAPI files, docs, images, and sidebar configuration file.

To open your project in Stoplight Studio, start the app and on the start screen click "Open Existing Folder". Then pick the directory of your project in your local copy of this repository.

Then, to get an overview of all the files in your project, click on the "Files" tab in the left sidebar.

## OpenAPI file(s) ⚙️

**Directory: `reference`**

The complete technical overview of your API's endpoints must be documented in an [OpenAPI](https://www.openapis.org/) file (previously called "Swagger"). If you have multiple APIs inside your project, your project may have multiple OpenAPI files.

Every OpenAPI file must follow version 3.x of the OpenAPI spec, preferably [3.1.0](https://spec.openapis.org/oas/latest.html) or later when possible.

Preferably the OpenAPI files are formatted as JSON, but YAML is also allowed if necessary.

You can add/edit OpenAPI files using your preferred JSON/YAML editor. [Stoplight Studio](https://stoplight.io/studio/) offers a nice GUI to work with OpenAPI files and also includes embedded reporting of the automatic checks that we run for OpenAPI files.

## Docs 👩‍🏫

**Directory: `docs`**

How-to guides and other pages all live inside the `docs` directory of your project.

Every page is a Markdown (`.md`) file, which you can edit with a Markdown editor. However, Stoplight supports some special syntax that is not always supported in every Markdown editor. Therefore it is advised to use [Stoplight Studio](https://stoplight.io/studio/) if possible.

The reference for the Stoplight Flavored Markdown can be found [here](https://meta.stoplight.io/docs/studio/ZG9jOjg0-stoplight-flavored-markdown-smd). It allows you to, for example, easily embed videos from YouTube and Vimeo and to add info/warning/danger/success messages.

Note that Markdown files should not be used to document all of your API's endpoints. They should only be used for how-to guides and other extra documentation, while your API's endpoints should be documented in an OpenAPI file.

## Sidebar 🔎

**File: `toc.json`**

When you add or remove docs, your project's sidebar will not automatically be updated. Instead, you have to manage your project's sidebar manually inside its `toc.json` file. The exact syntax and options are described in [Stoplight's documentation](https://meta.stoplight.io/docs/platform/ZG9jOjIxOTkxNTkz-project-sidebar#project-sidebar).

## Images 🎨

**Directory: `assets/images`**

To ensure that all of your images display correctly on https://docs.publiq.be, they must be stored inside the `assets/images` directory of your project. You may use subdirectories if you want.

Additionally, you should always use relative URLs to reference them inside your Markdown files. For example, if your file is `docs/introduction.md`:
```
![Your example alt text](../assets/images/example.png)
```

If you do not follow these guidelines, images may not appear on https://docs.publiq.be even if they do in Stoplight Studio.

## Automatic checks 🚩

To avoid common mistakes like dead links in how-to guides or violations of our [API design guidelines](https://docs.publiq.be/docs/guidelines) in OpenAPI files, automatic checks will run for every push or pull request.

You can also run these checks yourself on your local machine to spot issues early on, and even fix some of them automatically.

First, make sure you have node and yarn installed as per the requirements mentioned above.

Second, run `yarn install` to install all required packages for the checks to work.

Then, run any of the following commands:

*   `yarn api:lint` to check for syntax errors or design guidelines violations inside the OpenAPI files
*   `yarn docs:lint` to check the `.md` files (guides) for mistakes or syntax errors

## Automatically fixing (some) errors ✅

Warnings or errors reported by `yarn api:lint` (a.k.a. the `CI / openapi` check on GitHub) always need to be fixed manually in the OpenAPI file(s) of your project.

Warnings or errors reported by `yarn docs:lint` (a.k.a. the `CI / docs` check on GitHub) can sometimes be fixed automatically, depending on the exact issue. For example formatting issues can be fixed automatically, but dead links not.

If you have `node` and `yarn` installed locally, you can run `yarn docs:lint:fix` to try to fix the linting issues. Any issues that can be fixed will be fixed, and you can then commit them.

You can also run the same script on GitHub itself via https://github.com/cultuurnet/apidocs/actions/workflows/docs-linting-fix.yml. 

Click "Run workflow", select the branch you are working on (make sure it's up-to-date!), and hit the green "Run workflow" button. If any errors were fixed, they will be automatically committed back to your branch. Make sure to pull these changes in your local copy of the docs before making more changes to avoid merge conflicts!

![](readme-images/run-workflow.png)
