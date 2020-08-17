# How to setup Absolute Imports in a Typescript project

If you hate seeing this:

```ts
// SomeContainer.tsx
import {MyComponent} from '../../components/MyComponent.tsx'
```

and would prefer to see this instead:

```ts
// SomeContainer.tsx
import {MyComponent} from 'components/MyComponent.tsx'
```

Heres the snippet you need:
```jsonc
// tsconfig.json
{
  "compilerOptions": {
    "baseUrl": "./src",
  }
}
```

### BONUS: Wanna get rid of the file name? Make sure to add an index.ts inside your `components/` folder and export everything as named imports.

```ts
// SomeContainer.tsx
import {MyComponent} from 'components'
```

_Much cleaner, ain't it?_
