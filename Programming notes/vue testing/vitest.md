#### 1. Functions of vitest
1. `describe it expect beforeEach beforeAll afterAll`
2. we can add `beforeEach` inside `describe` block also 
#### 2. @testing-library/vue
1. `render screen`

#### 3. Render
1. `render(SignUp)`
2. To render an element with props `render(HelloWorld,{ props: { msg: 'Hello Vitest' } })`
3. `const { container } = render(SignUp)` => `container` id equivalent to `document` in vanilla JavaScript . 
4. To render with global dependencies 
```php

import { i18n } from '../src/locales/index.js'
const customRender = (component, options) =>
  render(component, {
    global: {
      plugins: [i18n]
    },
    ...options
  })
```
#### Screen
1. `screen.getByText('Hello Vitest');
2. `const header = screen.getByRole('heading', { name: 'Sign Up' })` => `name` is text inside heading
3. `const signUpButton = screen.getByRole('button',{'name':'Sign up'});`
4. `screen.queryByLabelText('Username')`
5. `screen.queryByPlaceholderText('Username')`
6. `expect(screen.queryByRole('status')).not.toBeInTheDocument()`
7. `const text = await screen.findByText('User create success')`
8. `screen.queryByTestId('form-sign-up')`
9. 
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
7. `expect(axios.post).toHaveBeenCalledTimes(1)`
8. `expect(requestBody).toEqual({})`
9. `expect(counter).toBe(1)`
10. `expect(input).toHaveClass('is-invalid')`
11. 
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

```php
server.use(

          http.post('/api/v1/users', async ({ request }) => {
            // if we don't add the delay form will vanish immediately after completion of the request
            // and we wont be able to capture the loading spinner.
            await delay('infinite')
          })
        )
```
=> `msw` will use the given handler for the specific test and use default handler for other tests
=> to to remove the above handler use the following code. => note 
```
beforeEach(() => {
  server.resetHandlers()
})
```
=> To return a network error
```
server.use(
          http.post('/api/v1/users', ({ request }) => {
            return HttpResponse.error()
          })
        )
```
=> to pass status with response

```
http.post('/api/v1/users', ({ request }) => {
            return HttpResponse.json(
              {
                validationErrors: {
                  username: 'Username cannot be null'
                }
              },
              { status: 400 }
            )
```

#### Wait for
1. by default waits for 1 second before executing the callback.


#### Proxy
`in vite.config.js`
```
server: {
    proxy: {
      '/api': 'http://127.0.0.1:8080'
    }
  }
```

#### Mocking
```php
beforeEach(() => {
  vi.clearAllMocks()
  // to clear the mock axios before each test.
  // if we don't clear the mock we will see unexpected results
  // expect(axios.post).toHaveBeenCalledTimes(1) => this test will fail because axios is called twice in the 2 seperate tests.
})
```
1. `axios.post.mockResolvedValue({ data: {} })` => when `axios.post` is called it returns a promise which resolves to `{ data: {} }
2. To mock the implementation of a function `axios.post.mockImplementation(() => {return 'sagnik'})`
3. `axios.post.mockRejectedValueOnce({}).mockResolvedValue({ data: {} })` => first time it will reject the promise after that it will resolve the promise

#### Describe
```php
 describe.each([
      { field: 'username', message: 'username cant be null' },
      { field: 'email', message: 'E-mail cant be null' },
      { field: 'password', message: 'Password cant be null' }
    ])('when $field is invalid', ({ field, message }) => {
    .........
    .........
 })
```






