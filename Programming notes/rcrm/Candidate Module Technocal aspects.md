### `candidate.json`
#### location: `app/includes/candidates.json`
##### Description
It constants the list of columns in the candidate list page. The properties are used in the frontend to display different settings and functionality.
```
"filter_type": "is",
"filter_size": 200,
"filter_type_locked": false,
"filter_value": null,
"filter_value_second": null,
```
- these are used in advanced search
![[Pasted image 20240322220527.png]]

- `filter_type` => displays `Select Filter type` option
- `filter_size` => I guess maximum no of characters allowed in the filter.
- `filter_type_locked` => If yes you cant modify the filter type.
- `filter_value` => i guess DEFAULT VALUE in enter your search

```
"service": "/qualifications",
"data": false
```
- service => can be used to fetch the data in dropdown for advanced search
![[Pasted image 20240322222121.png]]
