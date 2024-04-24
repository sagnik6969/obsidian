- Exception handler code is only for a specific rest controller.
- it cant be reused by other controller.
- We need global exception handlers.
       1. Promotes reuse.
       2. Centralized exception handling.
#### Spring `@ControllerAdvice`
- `@ControllerAdvice` is similar to an interceptor or filter. 
- Preprocess request to controllers.
- Postprocess responses to handle exceptions.
- Perfect for global exception handling.
- This is real time use of aspect oriented programming.
- `@ControllerAdvice` will preprocess requests going to controllers and postprocess responses coming out of controllers.

#### Development process
- 