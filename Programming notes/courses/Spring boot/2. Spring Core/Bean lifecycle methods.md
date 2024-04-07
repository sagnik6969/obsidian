![[Pasted image 20240407100535.png]]
#### Purpose of bean lifecycle methods and hooks
- You can add custom code during bean initialization.
    1. calling custom business logic method.
    2. Setting up handles to resources (database, sockets, files etc)
- You can add custom code during bean destruction
     1. Calling custom business logic method
     2. Clean up handles to resources.
#### To add custom initialization code once the bean has bean has been constructed
![[Pasted image 20240407101305.png]]
#### To do cleanup tasks before destruction
![[Pasted image 20240407101534.png]]

#### Development process
1. define methods for `init` and destroy.
2. add annotations `@PostCOnstruct` and `PreDestroy`

#### Important notes
- **For "prototype" scoped beans, Spring does not call the destroy method.**
- Prototype beans are lazy by default. There is no need to use the @Lazy annotation for prototype scopes beans.


