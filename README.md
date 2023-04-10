
# Curseur

Svelte component for creating customizable cursors.

## Installation
NPM
```bash
npm i curseur
```
Yarn
```bash
yarn add curseur
```
PNPM
```bash
pnpm add curseur
```

## Usage

import the library
```js
import  {  Cursor  }  from  'curseur';
```
And simply use it:
```html
<Cursor  color="green"  mixBlendMode="exlusion"  size={13}  />
```

## Customization

- `size`: Number - The size of the cursor. (Default: `20`)
-  `color`: String - The color of the cursor. (Default: `'black'`)
-  `shape`: String - The shape of the cursor. (Default: `'circle'`)
- `mixBlendMode`: String - The mix-blend-mode of the cursor. (Default: `'none'`)