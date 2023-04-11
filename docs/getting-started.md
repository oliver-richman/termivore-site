# Getting Started with Termivore

Creating a CLI with Termivore is pretty simple, however there a two approaches based on your project's needs.

You can either use the Termivore CLI (recommended) or manually import the Termivore features you need.
If you haven't started building your CLI yet, or want to start over then we would *highly recommend* using the Termivore CLI

## Termivore CLI
Using the Termivore CLI will allow you to quickly spin up a new project with everything you need to get started.

Firstly, you'll want to install Termivore globally:
```bash
npm i -g termivore
```

!!! info "You probably already will, but you might want to"

    Ensure you have both node and npm installed on your machine.
	We would recommend using a tool such as NVM to handle your node/npm versions

Once you have Termivore installed globally, you can now have access to the `termivore` command within your console.
To create a new Termivore CLI project for the first time you can just run:
```bash
termivore create
```

This will run you through a series of questions to setup your new CLI to your preferences.

If you'd rather not answer a bunch of questions there are arguments and options you can pass to `termivore create` which will allow you to define your preferences ahead of time:

### Arguments

| Argument | Description |
| --- | --- |
| `<project-name>` | The name of the project and directory to create |
| `<root-command>` | The root command of your cli, e.g. Termivore's root command is 'termivore' |

### Options

| Option | Description | Alternatives |
| --- | --- | --- |
| `--language` | The language of your project, must be either 'TypeScript' or 'JavaScript' | `-l`, `--lang` |
| `--no-help` | Use this flag if you don't want a help command to be created | `-nh` |
| `--no-version` | Use this flag if you don't want a -v flag to show your CLIs version | `-nv` | 
| `--linting-preference` | Specify your linting preference, 'both', 'eslint', 'prettier', 'none' | `-lp`, `--lint` |
| `--no-git` | Use this flag if you don't want to init this project as a git repository |`-ng` | 

### Examples

#### TypeScript, ESLint, Prettier CLI

Create a new Termivore CLI called `my-project` with a root command of `mp`. Use TypeScript, ESlint and Prettier.
By default this will initialise the new project as a git repository and create a help command and add the functionality for `-v`.
```bash
termivore create my-project mp --lang=TypeScript --lint=both
```

#### JavaScript, No Linting, No Git, No Extras

Create a new Termivore CLI called `very-cool-project` with a root command of `vcp`. Uses JavaScript with no linting or formatting. It also disables the help command and the version option. Also, because we have passed `-ng` it won't initialise a git repository.
```bash
termivore create very-cool-project vcp --lang=JavaScript --lint=none -ng -nv -nh
```


## Manual Use

If you're just wanting to use some of Termivores features in an existing project or you prefer to approach CLI creation in a different way, you can manually add elements of Termivore to your package.

First of all, install Termivore as a dependency in your project:
```bash
npm i termivore
```

Next you'll want to import the feature(s) you want to use:

=== "TypeScript/ES6"

    ``` typescript
    import { log } from 'termivore';

	log('This log is green!').green().print();
    ```

=== "JavaScript/CommonJS"

    ``` javascript
    const termivore = require('termivore');

	termivore.log('This log is green!').green().print();
    ```
