# query-hook

> React hook used to make API calls

[![NPM](https://img.shields.io/npm/v/query-hook.svg)](https://www.npmjs.com/package/query-hook) [![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)

## Install

```bash
npm install --save query-hook
```

## Usage

### JavaScript
```jsx
import { useQuery, Status } from 'query-hook';

const Component = () => {
  const usersQuery = useQuery();

  useEffect(() => {
    switch (usersQuery.status) {
      case Status.INIT:
        usersQuery.get('https://api.example.com/users');
        break;
      case Status.SUCCESS:
        console.log('Fetched users :', usersQuery.response.users);
        break;
      case Status.ERROR:
        console.error('Unable to fetch users :', usersQuery.errorResponse.errors);
        break;
    }
  }, [usersQuery.status]);

  return (
    <div>
      {usersQuery?.response.users.map(user => user.name)}
    </div>
  )
}
```

### TypeScript
```tsx
import { FC } from 'react';

import { useQuery, Status, ErrorData, Response, ErrorResponse } from 'query-hook';

// Custom error data (optional)
interface CustomErrorData extends ErrorData {
  error: 'access_denied' | 'unauthorized' | 'not_found';
}

// Custom response (optional)
interface UsersResponse extends Response {
  users: [{
    email: string;
    name: string;
  }];
}

// Custom error response with custom error data (optional)
interface CustomErrorResponse extends ErrorResponse {
  errors: CustomErrorData[];
}

const Component: FC = () => {
  const usersQuery = useQuery<UsersResponse, CustomErrorResponse>();

  useEffect(() => {
    switch (usersQuery.status) {
      case Status.INIT:
        usersQuery.get('https://api.example.com/users');
        break;
      case Status.SUCCESS:
        console.log('Fetched users :', usersQuery.response.users);
        break;
      case Status.ERROR:
        console.error('Unable to fetch users :', usersQuery.errorResponse.errors);
        break;
    }
  }, [usersQuery.status]);

  return (
    <div>
      {usersQuery?.response.users.map(user => user.name)}
    </div>
  )
}
```

## License

MIT © [Lelberto](https://github.com/Lelberto)

---

This hook is created using [create-react-hook](https://github.com/hermanya/create-react-hook).
