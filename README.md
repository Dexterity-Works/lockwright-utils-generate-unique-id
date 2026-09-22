# lockwright-utils-generate-unique-id

Generate unique IDs.

Site: [lockwright.dexterity.works](https://lockwright.dexterity.works)

Community fork of PearPass (Apache 2.0). Not affiliated with or endorsed by Tether Data or the Pears project.

## Features

- Generates a cryptographically secure random identifier using `crypto.randomUUID()` when available, falling back to a 32-character hex string.
- Accepts an optional `skipUUID` flag to always produce the hex-string format.
- Works in browser, Node.js, and Pear runtimes — any environment that exposes `globalThis.crypto`.

## Security Notice

The package name is `lockwright-utils-generate-unique-id`.

## Installation

Install the package using npm:

```bash
npm install git+https://github.com/Dexterity-Works/lockwright-utils-generate-unique-id.git
```

## Testing

To run the tests, use the following command:

```bash
npm test
```

## Usage Examples

### Default (UUID v4 when available)

```javascript
import { generateUniqueId } from 'lockwright-utils-generate-unique-id';

const id = generateUniqueId();
// => "f47ac10b-58cc-4372-a567-0e02b2c3d479"  (UUID v4)
```

### Force hex-string format

Pass `{ skipUUID: true }` to always get a 32-character hex string, even on runtimes that support `crypto.randomUUID()`.

```javascript
const hexId = generateUniqueId({ skipUUID: true });
// => "a3f1c2d4e5b6a7f8c9d0e1f2a3b4c5d6"  (32-char hex)
```

### API

```
generateUniqueId(options?)
```

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `options.skipUUID` | `boolean` | `false` | When `true`, skips `crypto.randomUUID()` and returns a 32-char hex string instead |

**Returns** `string` — UUID v4 or 32-character hex string.

**Throws** `Error` if `globalThis.crypto` is unavailable (no secure random source).

> **Note:** This function is intended for generating record/session identifiers. It is **NOT** suitable for secrets, authentication tokens, or authorization keys.

## Related Projects

- [lockwright-app-mobile](https://github.com/Dexterity-Works/lockwright-app-mobile) - Lockwright for mobile
- [lockwright-app-browser-extension](https://github.com/Dexterity-Works/lockwright-app-browser-extension) - Lockwright browser extension
- [lockwright-app-desktop](https://github.com/Dexterity-Works/lockwright-app-desktop) - Lockwright for desktop

## License

This project is licensed under the Apache License, Version 2.0. See the [LICENSE](./LICENSE) file for details.
