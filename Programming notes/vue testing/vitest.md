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
=> note the above will add `this.$t`
=> it also takes care of `useI18n` function. 
=> to change `i18n.locale` we have to import the local configuration file which is used in `app.use`
=> note these global plugins need to be imported from local directories for example `router` must be imported from local `router.js`
#### Screen
1. `screen.getByText('Hello Vitest');
2. `const header = screen.getByRole('heading', { name: 'Sign Up' })` => `name` is text inside heading
3. `const signUpButton = screen.getByRole('button',{'name':'Sign up'});`
4. `screen.queryByLabelText('Username')`
5. `screen.queryByPlaceholderText('Username')`
6. `expect(screen.queryByRole('status')).not.toBeInTheDocument()`
7. `const text = await screen.findByText('User create success')`
8. `screen.queryByTestId('form-sign-up')`
9. `screen.queryByAltText('user1'))`
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
11. `expect(mockSetItem).toHaveBeenCalledWith('app-lang', language)` => this will only work if you add `const mockSetItem = vi.spyOn(Storage.prototype, 'setItem')` or equivalent `vi.mock('location')`
12. `expect(signUp).toHaveBeenCalledTimes(1)`
13. ` expect(requestBody).toStrictEqual({email: 'text@example.com'})`
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
=> To get request headers in `msw`
1. `acceptLanguage = request.headers.get('Accept-Language')`
=> to access route params in `msw`

```js
const server = setupServer(
  http.patch('/api/v1/users/:token/active', ({ params }) => {
    counter++
    token = params.token
  })
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
```js
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

```js
vi.mocked(useI18n).mockReturnValue({
  t: (key) => en[key]
})
// the above and bellow code does exactly same work.
// to mock a  function we first need to vi.mock('library name/path')
 useI18n.mockReturnValue({
  t: (key) => en[key]
})
```

=> to mock `this.$t`
```js
 const result = render(SignUp, {
    global: {
      mocks: {
        $t: (key) => en[key]
      }
    }
  })
```
4. `vi.spion()` 
```js
const mockSetItem = vi.spyOn(Storage.prototype, 'setItem')
 // we cant use vi.mock => vi.mocked() here because vi.mock requires a path and Storage.prototype
 // does not have a path
 // spy on does not need vi.mock('....)
 // can mock functions directly
 // first argument is the object name where function is located
 // second argument is the name of the function
expect(mockSetItem).toHaveBeenCalledWith('app-lang', language);
// toHaveBeenCalledWith => only works with spyon
```
5. `const mockNavigatorLanguage = vi.spyOn(window.navigator, 'language', 'get')` => language is getter function.  `get` => tells vi that language is a getter function.
6. `mockNavigatorLanguage.mockReturnValue(undefined)`
7. `mockNavigatorLanguage.mockReset()` => `works similar to vi.clearAllMocks()`
8. clear all mocks vs reset all mocks => If you want to test mock function called times, clear before you use If you want to make sure mock return value wouldn't pollute other test case, call reset.

```js
vi.mock('@/locales/index.js', () => {
  return {
    i18n: {
      global: {
        locale: 'ab'
      }
    }
  }
})
```
9. the second argument to `vi.mock` is factory to the referred file.
10. To mock a vue file 
```js
vi.mock('@/views/activation/Activation.vue')
// The above will mock the functionality of Activation.vue
// => it will search for mock file in the __mocks__ folder under '@/views/activation'
// in the actual file due to axios the test were
// failing because in the test we are not returning any response
```
11. `vi.spyOn(window, 'confirm').mockReturnValue(0)` 
12. `expect(window.confirm).toHaveBeenCalledTimes(1)`
13. `// we can call the above function only when window.confirm is bound by vi.spyOn()`
14. 



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

#### i18n
```js
// the state of language selector is preserved in between tests.
// in the bellow tests if there are tests after the given tests the value of the
// language selector will be tr.
// to solve this issue
afterEach(() => {
i18n.global.locale = 'en'
})
```
#### Router
=> router should be included in `render => global => plugins`
```js
 router.push('/users/1')
 await router.isReady() //Returns a Promise that resolves when
 //the router has completed the initial navigation
 render(App)
```
=> you can use ref and reactive inside `spec.js` file

#### Local Storage
1. `localStorage.clear()`
2. 
3. 








