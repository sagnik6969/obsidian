- Data binding is the process of converting JSON data to a java POJO or to convert POJO to json.
- `POJO => ` Plan Old Java Object
#### JSON data binding with `jackson`
- Spring uses `jackson` project behind the scenes.
- Jackson handles data binding between JSON and java POJOS.
#### JSON to java POJO
- Convert JSON to java POJO `=>` Call setter method on POJO. `=>` Jackson will do all this work behind the scenes.
#### Java POJO to JSON
- call getter methods on POJO.
#### Spring and Jackson support
- Spring will automatically handle `jackson` integration.
- JSON data being passed to rest controller is automatically converted to POJO.
- Any java object being returned from rest controller is converted to json.
- All this happens automatically behind the scenes thanks to `spring <=> jackson`
