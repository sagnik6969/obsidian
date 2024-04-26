- spring data rest creates rest end points by adding an *S* at the end of the entity name.
- But it cant handle complex plural forms. Example: person, sylabus
- In this case you need to specify plural name manually.
#### Solution
- Specify plural name with annotation in the repository class.
