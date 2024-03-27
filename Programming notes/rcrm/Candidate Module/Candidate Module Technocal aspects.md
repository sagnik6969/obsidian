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

> The file `candidate.json` has default data. if user modifies the default settings the changes are stored in database.
> 

### `EntityColumns.php`
> Here we fetch the updated settings and send them to frontend. It uses `candidate.json`

- `detailPageOrder` => position of the column in details page.
- `listPageOrder` => position of the column in the list page.
- `$entity` => name of the table for which We are fetching columns.
- `eeocompliance` => means employer does not discriminate based on race & gender etc.
- `_jobAssociatedCustomFields` => appears to be a repetition.
- [List And Details Page Rearrangement - Feature Requirements - Confluence (atlassian.net)](https://rcrm.atlassian.net/wiki/spaces/RC/pages/222626101/List+And+Details+Page+Rearrangement)
- `$accountId` => `accountId` of the owner.
- `addcandidateformfields` => fields in add candidate form.
- `addcandidateformsectionfields` => fields in sections in add candidate form (example education)
- 
- 

### `FormFieldReposetary.php`

> used for add candidate forms. 
> used to store / update form fields.
> store data into `tbl_account_settings`

> `entity type id` => represents different entities example. `candidate` , `contact`, `jobs` etc
> In the database we store all entity custom fields in a single table => `tbl_extra_fields`. These custom fields are identified through `user_id` and `entity_type_id`.

### `CandidateRepositary.php`
`public function addCandidate` => used to add a new candidate.

### `ExternalPageRepositary.php`
> Used to manage external pages.
> `function applyUpdateCandidate` => handles => `apply to job`, `update profile request` and `talent pool request`.
> if the request has a job slug then it is a applied candidate else it is a talent pool candidate.
> 

`tallent pool page` => external page from where candidate can apply.

### Candidate page setting in Admin  settings page.


## Routes
##### `/v1/candidates/search/get`
1. returns total candidate count and filtered candidate count.
2. It no filter is applied then `total_candidate_count` = `filtered_candidate_count`
3. first `count` function in `condidateController` is called.
4. 


