#### 1. Functions of vitest
1. `describe it expect`

#### 2. @testing-library/vue
1. `render screen`

#### 3. Render
1. `render(SignUp)`
2. To render an element with props `render(HelloWorld,{ props: { msg: 'Hello Vitest' } })`
3. `const { container } = render(SignUp)` => `container` id equivalent to `document` in vanilla JavaScript . 
#### Screen
1. `screen.getByText('Hello Vitest');
2. `const header = screen.getByRole('heading', { name: 'Sign Up' })` => `name` is text inside heading
3. `const signUpButton = screen.getByRole('button',{'name':'Sign up'});`
4. `screen.queryByLabelText('Username')`
5. `screen.queryByPlaceholderText('Username')`
6. 
#### Expect
1. `expect(element).toBeTruthy()`
2. to increase the functionality `expect`
```php
import * as matchers from '@testing-library/jest-dom/matchers'
expect.extend(matchers);
```
3. `expect(element).toBeInTheDocument();` => `toBeInTheDocument` is provided by matches
4. `expect(screen.queryByLabelText('Password')).toHaveAttribute('type', 'password')`
5. `expect(signUpButton).toBeDisabled();`
6.  `expect(axios.post).toHaveBeenCalledWith('api/vi/users', {username: 'test_user'})` => to use this function we first need to `vi.mock('asios')`
7. `expect(requestBody).toEqual({})`

#### @testing-library/user-event
1. `import userEvent from '@testing-library/user-event'`
2. `const user = userEvent.setup()`
3.  `await user.type(password, 'asdf')`
4. `await user.click(signUpButton)`

#### Mock-service-worker
```php
  

import { setupServer } from 'msw/node'
import { HttpResponse, http } from 'msw'

 let requestBody
 const server = setupServer(
        http.post('/api/vi/users', async ({ request }) => {
          requestBody = await request.json()
          return HttpResponse.json({})
        })
      )
      server.listen()
............
............
 await waitFor(() => {
        expect(requestBody).toEqual({
          username: 'test_user',
       })
  })
server.close();

```

#### Wait for
1. by default waits for 1 second before executing the callback.
2. 