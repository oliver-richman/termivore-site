# Logger

Termivore's `log()` function is a useful and versatile method that will be able to tackle most of your logging needs. It can log out in a variety of preset colors, as well as specific hex and rgb colors. You also have the ability to pass in your own ANSI codes if you need to do something a little more complex.

## Basic Use

The most basic use of the Termivore logger is like this:

=== "TypeScript/ES6"

    ``` typescript
    import { log } from 'termivore';

	log('I log to the console').print();
    ```

=== "JavaScript/CommonJS"

    ``` javascript
    const termivore = require('termivore');

	termivore.log('I log to the console').print();
    ```

The most important thing to remember is to always end a log function with a chained `.print()` as this is what triggers the log to be printed to the console. There a few reasons for this, but it's mainly to allow the use of chaining styles, appending logs, etc.

## Adding Color

There's a variety of preset methods you can chain to `log()` to change the color of your log, both text color and background color. However, if there's a specific hex code or RGB color you wish to use, then don't worry, this is also possible with the log function!

### Text Color

You can change the color of your log text very simply, by doing:

=== "TypeScript/ES6"

    ``` typescript
    import { log } from 'termivore';

	log('I\'m blue!').blue().print();
    ```

=== "JavaScript/CommonJS"

    ``` javascript
    const termivore = require('termivore');

	termivore.log('I\'m blue!').blue().print();
    ```

!!! info "Available preset colors"

    To see a full list of the preset colors you can set, by chaining methods like above, please see the Chainable Methods section of this page

### Background Color

Changing the background color of your log is just as easy as changing the text color, every available method you can chain to change the color also has a `Bg` counterpart:

=== "TypeScript/ES6"

    ``` typescript
    import { log } from 'termivore';

	log('My background is blue!').blueBg().print();
    ```

=== "JavaScript/CommonJS"

    ``` javascript
    const termivore = require('termivore');

	termivore.log('My background is blue!').blueBg().print();
    ```

If you wish to change both the text and background color of a log you can simply chain up the commands:

=== "TypeScript/ES6"

    ``` typescript
    import { log } from 'termivore';

	log('My text is black, my background is white!').black().whiteBg().print();
    ```

=== "JavaScript/CommonJS"

    ``` javascript
    const termivore = require('termivore');

	termivore.log('My text is black, my background is white!').black().whiteBg().print();
    ```

## Adding Styles

As well as colors, there is also a variety of styles you can add to your logs too

=== "TypeScript/ES6"

    ``` typescript
    import { log } from 'termivore';

	log('This text is bold').bold().print();
	log('This text is in italics').italic().print();
	log('This text is underlined').underline().print();
    ```

=== "JavaScript/CommonJS"

    ``` javascript
    const termivore = require('termivore');

	termivore.log('This text is bold').bold().print();
	termivore.log('This text is in italics').italic().print();
	termivore.log('This text is underlined').underline().print();
    ```

## Log Replacement & Deletion

The log function isn't just colors and styles, you can also manipulate the logs that have already been printed to the console.

### Replace an already printed log

If you've printed a log to the console and then wish to change it, you can do:

=== "TypeScript/ES6"

    ``` typescript
    import { log } from 'termivore';

	const logId = log('Previous text').print();
    log('Changed text', logId).print();
    ```

=== "JavaScript/CommonJS"

    ``` javascript
    const termivore = require('termivore');

	const logId = termivore.log('Previous text').print();
    termivore.log('Changed text', logId).print();
    ```

### Remove an already printed log

Removing a log from the console after it's printed works the same way as replacing a printed log, however you just pass a blank string

=== "TypeScript/ES6"

    ``` typescript
    import { log } from 'termivore';

	const logId = log('I am going to be removed').print();
    log('', logId).print();
    ```

=== "JavaScript/CommonJS"

    ``` javascript
    const termivore = require('termivore');

	const logId = termivore.log('I am going to be removed').print();
    termivore.log('', logId).print();
    ```

## Appending

Creating complex logs with appended text is made simple with Termivore, wether you just want to add another string to your log, or specifically style elements of your log text.

### Appending text

If you're doing more complex logic with your logs and wish to append text to a log before you print it then this is possible with the chainable `append` method. As with all the log's chainable methods you don't have to do it all in one, you can assign the log to a variable and update it with appends (or any chainable method) until you're ready to print it.

=== "TypeScript/ES6"

    ``` typescript
    import { log } from 'termivore';

	log('All').append('one').append('log!').print();

    const greetingLog = log('Hello,');
    greetingLog.append(name).print();
    ```

=== "JavaScript/CommonJS"

    ``` javascript
    const termivore = require('termivore');

	termivore.log('All').append('one').append('log!').print();

    const greetingLog = termivore.log('Hello,');
    greetingLog.append(name).print();
    ```

### Appending a `log()`

When you append to a log, it doesn't always have to be a string, it can also be another `log`. For example if you wanted to print a message to the console where one part of the message is styled differently, appending a log might be the best solution:

=== "TypeScript/ES6"

    ``` typescript
    import { log } from 'termivore';

    const boldGreenName = log(`${name}!`).green().bold();
	log('Hello,').append(boldGreenName).append('Nice to meet you!').print();
    ```

=== "JavaScript/CommonJS"

    ``` javascript
    const termivore = require('termivore');

	const boldGreenName = termivore.log(`${name}!`).green().bold();
	termivore.log('Hello,').append(boldGreenName).append('Nice to meet you!').print();
    ```

## Chainable Methods

There are many available methods you can chain to the `log` method before finally chaining `print`, some of which you may have seen in the examples above, here is the full list of methods you can chain to a `log()`.

| Method | Arguments | Description | Example |
| --- | --- | --- | --- |
| `append` | appendedMessage: string or Logger | Used to join a string or new log to an existing log | 'original log message <span style="color: red;">appended red message</span>' |
| `bold` | n/a | Used to change the text to be bold | **bold text** |
| `dim` | n/a | Used to change the text to be dim | <span style="opacity: 0.5">dimmed text</span> |
| `italic` | n/a | Used to change the text to be italic | *italic text* |
| `underline` | n/a | Used to change the text to be underlined | <span style="text-decoration: underline">underlined text</span>  |
| `black` | n/a | Changes the text color to black | black text |
| `blackBg` | n/a | Changes the log's background color to black | <span style="color:#fff; background-color:#000">black background</span> |
| `red` | n/a | Changes the text color to red | <span style="color:red"> red text</span> |
| `redBg` | n/a | Changes the log's background color to red | <span style="color:#fff; background-color:red">red background</span> |
| `green` | n/a | Changes the text color to green | <span style="color:green"> green text</span> |
| `greenBg` | n/a | Changes the log's background color to green | <span style="color:#fff; background-color:green">green background</span> |
| `yellow` | n/a | Changes the text color to yellow | <span style="color:yellow; background-color:black"> yellow text</span> |
| `yellowBg` | n/a | Changes the log's background color to yellow | <span style="color:black; background-color:yellow">yellow background</span> |
| `blue` | n/a | Changes the text color to blue | <span style="color:blue"> blue text</span> |
| `blueBg` | n/a | Changes the log's background color to blue | <span style="color:#fff; background-color:blue">blue background</span> |
| `magenta` | n/a |Changes the text color to magenta | <span style="color:magenta"> magenta text</span> |
| `magentaBg` | n/a | Changes the log's background color to magenta | <span style="color:#fff; background-color:magenta">magenta background</span> |
| `cyan` | n/a | Changes the text color to cyan | <span style="color:cyan; background-color:black"> cyan text</span> |
| `cyanBg` | n/a | Changes the log's background color to cyan | <span style="background-color:cyan">cyan background</span> |
| `white` | n/a | Changes the text color to white | <span style="color:white; background-color:black"> white text</span> |
| `whiteBg` | n/a | Changes the log's background color to white | <span style="background-color:white">white background</span> |
| `rgb` | rgb: string[] or r: string, g: string, b: string | Changes the text color to the RGB color provided | <span style="color:rgb(246, 118, 74)"> rgb(246, 118, 74) text</span> |
| `rgbBg` | rgb: string[] or r: string, g: string, b: string | Changes the log's background color to the RGB color provided | <span style="color:#fff; background-color:rgb(246, 118, 74)">rgb(246, 118, 74) background</span> |
| `hex` | hexCode: string | Changes the text color to the hex code color provided | <span style="color:#937490"> #937490 text</span> |
| `hexBg` | hexCode: string | Changes the log's background color to the hex code color provided | <span style="color:#fff; background-color:#937490">#937490 background</span> |
| `ansi` | ansiCode: string | Adds the provided ANSI code to the beginning of the log so that the ANSI code action is performed for the log |  |