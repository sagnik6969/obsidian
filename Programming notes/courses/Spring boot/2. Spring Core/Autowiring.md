- done using `@Autowired` annotation'\.
- Injecting a Coach implementation Spring will  scan `@components`.
- But if there are multiple implements of the coach interface. Which one to choose.

#### Solution 1: use `@Qualifier`
1. use `@Qualifier` annotation to specify which implementation to use.
![[Pasted image 20240406235307.png]]

- It accepts `beinid` as an argument.
- `bein_id` is same as class name except the first character is in lower case.
- For setter injection we can do similar things. (use `@Qualifier`)

#### Solution 2: Use `@primary` Annotation
- add `@primary` annotation before the implementation which should be used by default.
![[Pasted image 20240407080336.png]]
![[Pasted image 20240407080405.png]]
- You can use `@Primary` and `@Qualifier` At the same time. `@Qualifier` has higher priority over primary.
- 