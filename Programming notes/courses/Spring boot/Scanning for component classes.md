- Spring will scan your java classes for special annotations example: `@Component` etc.
- And it will automatically register the beans in the spring container.
![[Pasted image 20240406214831.png]]
- By default spring boot starts component scanning from same package as your main spring boot application.
- It also scans sub packages recursively.
- If you want to scan other packages, you must specify them explicitly.
![[Pasted image 20240406215844.png]]

