
# Curseur

Svelte component for creating customizable cursors.

![npm](https://img.shields.io/npm/dw/curseur?style=for-the-badge) ![GitHub repo size](https://img.shields.io/github/repo-size/n3-rd/curseur?style=for-the-badge) ![GitHub top language](https://img.shields.io/github/languages/top/n3-rd/curseur?style=for-the-badge) ![npm](https://img.shields.io/npm/v/curseur?style=for-the-badge)

![enter image description here](https://i.ibb.co/SQGMwnw/CURSEUR-1.png)

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
<Cursor  color="green"  mixBlendMode="exclusion"  size={13}  />
```
To use hover effects, you can simply add a ```.hoverable``` class to the element you want to apply the effect to.
```html
<div  class="hoverable">
    <h1>Hover me!</h1>
</div>
```


## Customization

- `size`: Number - The size of the cursor. (Default: `20`)
-  `color`: String - The color of the cursor. (Default: `'black'`)
-  `shape`: String - The shape of the cursor. (Default: `'circle'`)
- `mixBlendMode`: String - The mix-blend-mode of the cursor. (Default: `'none'`)
