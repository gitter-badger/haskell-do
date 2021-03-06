# HaskellDO
*(pronounced "Haskell do")*

HaskellDO is a Haskell code editor, centered around interactive development.

This is a **pre-release** version, **not expected to be used in production**. As a
prototype, major changes may be applied in the future that could break backwards
compatibility. Pull Requests will be greatly appreciated, check out [our contributing guidelines](CONTRIBUTING.md).

The current version is written in [Haskell](https://www.haskell.org/) and
[PureScript](http://www.purescript.org/), but on next releases we're aiming for
a pure Haskell implementation.

## Downloads
---
The only *3rd-party* requirement to run HaskellDO is [Stack](http://haskellstack.org/)

You can find a binary release according to your operating system in the
[releases page](https://github.com/theam/haskelldo/releases).

## Usage
---

### Initializing a project
Begin by creating a **new** Stack project.

`stack new your_project_name`

After opening HaskellDO, it will ask you to open a Stack project.
Navigate to the root of the project you just created and open that
folder.

After opening the project, it will notify you of the following fact:

> The current version of HaskellDO **does not** support opening projects,
  therefore, after opening the project, it will override the `Main.hs`
  file in the root of the project. (Not any file in `app` or `src`, just
  the root.)

![Confirmation Dialog](http://imgur.com/DgspZip.jpg)

Therefore, if you re-open a project, the `<project-root>/Main.hs` file will
be deleted and re-created from scratch.

### Main interface
Let's begin by adding a text cell for documenting our analysis:

![Imgur](http://i.imgur.com/QAVI2WC.gif)

HaskellDO's text editor is based on [SimpleMDE](https://simplemde.com/) for
handling the editing and rendering of the "documentation" part of our code.

It supports all the features that you would expect from a normal markdown
editor, including image embedding.

- Do a single click out of the editor to render the current text
- Do a double click inside of the editor to come back to the text editing
  view.

![Imgur](http://i.imgur.com/ElGTVLK.gif)

Now, **it's time to work with some code, let's insert a code cell**.
In it, we write regular Haskell code, like we would do in a normal Haskell
module.

In fact, our whole page is just a Haskell file that can be used in any
Haskell, project. No need to export/import!

![Imgur](http://i.imgur.com/8jVxh6A.gif)

Now we have to try our new algorithm we spent hours researching on.
No, we do not have to spawn a `stack ghci` or a `stack repl`. HaskellDO
manages that for us and reloads the code each time we ask it to evaluate
some expression.

Just click on the **toggle console** button and press return on it to
enable it.

After writing your expression, press return [twice](linkToGithubIssue)
to get the result written on screen.

![Imgur](http://i.imgur.com/jgZQAvu.gif)

But, what does our *real* module file look like? Let's see the contents
of our `Main.hs` file:

```haskell
-- # Analyzing dog cuteness with genetic algorithms
--
-- After going **through thorough and tough thoughts**, we decided to use a simple example.

a = [1..20]
b = f <$> a

f :: Int -> Int
f x = x * 3 + 4
```

Just regular Haskell! Ready for deployment!

When you've finished testing HaskellDO, due to a bug, the `haskelldo-core`
process is left running. Be sure to kill it!

## Building from source
---

One could also want to build HaskellDO from source:
### Requirements

- NodeJS v6.8.1 or superior
- Stack v1.2.0 or superior

Begin by cloning this repository.

The project is composed of two sub-projects:

- A PureScript front end, residing in `gui`
- A Haskell back end, residing in `core`

### Compilation
For compiling the **backend**, execute in the `core/` directory:

- `stack build` - This will download the necessary dependencies and build the project.

For compiling the **frontend**, execute in the `gui/` directory:

- `npm install -g bower pulp purescript` - This will install:
    - **Bower** - A dependency tool used for purescript libraries
    - **Pulp** - A build tool for purescript
    - **Purescript** itself

- `npm install` - Installs necessary dependencies for the desktop app
- `bower install` - Installs purescript libraries used for the project
- `npm run build` - Build the project

Alternatively, for the last step, one can use `npm run watch` to make `pulp`
watch for source code changes, building the frontend each time the code changes.

## Running in dev-mode
---
After building the project, run, in the following order:

1. In the backend folder, `stack exec haskelldo-core`
2. In the frontend folder, `npm run start dev`, to make the GUI connect to the running
   dev server.

## Contributing
---
Wanna contribute? Make sure that you've read our [contributor guidelines](linkToContributing.md).
We'd like to hear from you and your ideas, get in touch with other contributors through:

- [Gitter](gitterChannelLink)
- [The issues page](githubIssues)
