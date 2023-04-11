# Open Link

If you want your CLI to trigger the opening of a webpage you can do so with Termivore's `openLink` method. This is useful for linking to documentation, external resources or even opening up a local url for your application.

=== "TypeScript/ES6"

    ``` typescript
    import { openLink } from 'termivore';

	openLink('https://www.termivore.com');
    ```

=== "JavaScript/CommonJS"

    ``` javascript
    const termivore = require('termivore');

	termivore.openLink('https://www.termivore.com');
    ```