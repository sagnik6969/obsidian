#### 1. Functions of vitest
1. `describe it expect`

#### 2. @testing-library/vue
1. `render screen`

#### Render
1. To render an element with props `render(HelloWorld,{ props: { msg: 'Hello Vitest' } })`

#### Screen
1. `screen.getByText('Hello Vitest');

#### Expect
1. `expect(element).toBeTruthy()`
2. to increase the functionality `expect`
```php
import * as matchers from '@testing-library/jest-dom/matchers'
expect.extend(matchers);
```
3. `expect(element).toBeInTheDocument();` => `toBeInTheDocument` is provided by matches
4. 