- `@RequestMapping` handles all the HTTP methods made to the specified endpoint
- `@GetMapping` handles only `GET` requests made to the specific endpoint.

#### To handle only get requests with `@RequestMapping`
```java
@RequestMapping(path="/processForm",method=RequestMethod.GET)
```

#### GET vs POST

| GET                                          | POST                 |
| -------------------------------------------- | -------------------- |
| Has a max character limit of 1000 charactors | No character limit   |
| Cant send binary data                        | Can send binary data |
| Can bookmark url                             | Cant bookmark url    |
