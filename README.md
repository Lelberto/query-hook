# query-hook

> React hook used to make API calls

[![NPM](https://img.shields.io/npm/v/query-hook.svg)](https://www.npmjs.com/package/query-hook) [![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)

## Install

```bash
npm install --save query-hook
```

## Usage

```tsx
import * as React from 'react'

import { useMyHook } from 'query-hook'

const Example = () => {
  const example = useMyHook()
  return (
    <div>
      {example}
    </div>
  )
}
```

## License

MIT © [Lelberto](https://github.com/Lelberto)

---

This hook is created using [create-react-hook](https://github.com/hermanya/create-react-hook).
