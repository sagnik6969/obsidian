#### Option 1: Use `java -jar`
command: `java -jar myApp.jar`
#### Option 2: If maven is already installed in the system
`mvn clean compile test`
#### Option 3: If maven is not installed in your system
`./nvnw.cmd clean compile test`
#### Option 4: Use spring boot maven plugin
- we can use this plugin to package our application into an executable jar or war file.
- to package our application into jar / war file `./mvnw package`
- to run our application `./mvnw spring-boot:run`
- `Scanner sc = new Scanner(System.in);` => `System.in` tells java where to look for inputs.
- `rand` => used to generate random number
- `Math` => `pow`,`max`,`min`