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
- `data` => used to store additional info in json format which is not stored in db.
- based on `service` and `data` dropdown is shown.
```
"dropdown_value": false,
"dropdown_field": false,
```
- whatever data we are getting from `service` `url` based on that `dropdown_value` and `dropdown_field` is set. dropdown value is `id` and dropdown field is `name`.
```
"label": "Off-Limit Status",
"external_label": "Off-Limit Status",
"longlabel": "Off-Limit Status",
```
- `label` => used for table headers.
- `external_label` => used in external pages.

```
"allow_on_import" : true,
"allow_on_export" : true,
"allow_on_apply" : false
```
- `allow_on_import` => whether the field is allowed to be imported from resume or not.
- `allow_on_apply` => whether the field is allowed to applied from external apply form 
-  `hide_on_detail_page` => if true the field wont be visible on the detail page.
- `is_bulk_editable` => is the filed is allowed to be updated in a bulk update.
- 