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
#### `/v1/candidates/count/get`
1. returns total candidate count and filtered candidate count.
2. It no filter is applied then `total_candidate_count` = `filtered_candidate_count`
3. first `count` function in `condidateController` is called.
4. in this function we perform request validation.
5. then we call `candidateRepository => getCount` function. In this function actual business logic is performed.
6. at last we format the response received from `candidateRepository => getCount` using `webAppGetRequestRespond` function. and finally return the response.
##### `candidateRepository => getCount`
- This function accepts request params as an input.
- it first checks if `columns` key exists in request header if not then it returns error response. This key contains settings of columns which is similar to `candidate.json`.
- the next if statement checks `count($params) <= 1)` => not sure what it does.
- `$where = '';` => all the where conditions required to get count  of  all candidates is stored here.


#### `/v1/candidates/search/get`
1. Returns list of filtered candidates. If no filter is applied then returns all candidates.
2. it calls `CandidateController@search`
3. here we validate the request and call `candidateRepositary => search` to get the search results. 
4. after that we format the response using `webAppGetRequestRespond` and return the final response.

##### `candidateRepositary => search`
-  In this function actual business logic is performed.
- This function accepts request params as an input.
- it first checks if `columns` key exists in request header if not then it returns error response. This key contains settings of columns which is similar to `candidate.json`.
- the next if statement checks `count($params) <= 1)` => not sure what it does.
- Then we check for `$params['viewMore']` (I think if user is not satisfied with initial search results then he can click on view More button to fetch additional results. but **I cant find this button On the frontend**).
###### If `$params['viewMore']` is true
- We fetch all column settings from `entityColumns.php` and fetch the search result from `candidateModel => getViewMoreSearchedResult` and return the response.
###### else
- first we check for `hotlist_id` column. `hotlist_id = null` if no hotlist is selected, `hotlist_id = -1`  if `Not In Any Hotlist` is selected. `hotlist_id = {id_of_the_hotlist}` if a specific hotlist is selected. 
###### Next
- It fetches appropriate `$candidatesQuery` (collection of candidates) based on the feature flags.
- 



### Show Candidate
- I will explain `showCandidate` function with this explanation you will be able to understand other functions also
```php
public function showCandidate($slug)
{

        $slug = rawurldecode($slug); // process the candidate slug
        $candidate = Candidate::findBySlug($slug); 
        // fetch the candidate from db 
        // It does not nontain custom columns

        if (!$candidate || $candidate->accountid != $this->user->accountid) {

            return [
                "message_type" => 'is-danger',
                "message" => 'Candidate not found',
                "data" => [],
                "status" => 'fail',
                "silent_progress" => false
            ];
        }
        // checks if the woner of the candidate is the account the user is part of. 


        // Access control for view company
        if(Gate::denies('can-view', ["candidates", $candidate->ownerid])) {
            return $this->accessDenied("View candidate action not allowed");
        }
        // checks whether the user can view the candidate using candidates->owner_id
        // this case fails when candidate belongs to the same account but belongs to some other user
  

        $candidate = $this->user->candidatesView()->where('slug', $slug)->first();
        //candidatesView => abstruction of sql view
        //it fetches all candidates along with custom columns.


        $candidate->profilepicUrl = $candidate->profilepic;
        $candidate->profilepic = encryptFileKey($candidate->profilepic);
        //encryptFileKey => encrypts the url
  

        // Fetch custom column number from tblextrafields
        $customColumnsData = ExtraFields::where(['accountid' => $this->user->accountid, 'entitytypeid' => Candidate::ENTITY_TYPE_ID, 'extrafieldtype' => 'file'])->get();
        foreach($customColumnsData as $customColumnData) {
            $customColumn = 'custcolumn'.$customColumnData->columnid;
            $candidate->$customColumn = encryptFileKey($candidate->$customColumn);
        }
       // the above loop is not used to fetch the custom columns (they are already fetched)
       // it is used to used to encrypt the file urls.

  

        // get previous user slug
        $previousCandidateRecord = $this->user->candidates()
            ->where('srno', '>', $candidate->srno)
            ->orderBy('srno', 'ASC')->first();

        $previousCandidate = $previousCandidateRecord ? $previousCandidateRecord->slug : '';
        // get next user slug
        $nextCandidateRecord =  $this->user->candidates()
            ->where('srno', '<', $candidate->srno)
            ->orderBy('srno', 'DESC')->first();
        $nextCandidate = $nextCandidateRecord ? $nextCandidateRecord->slug : '';

// $previousCandidate and $nextCandidate will be used for previous and next buttons
  
  
        $candidateDetail = array(
            'next' => $nextCandidate,
            'previous' => $previousCandidate,
            'candidate' => $candidate
        );
        
        return [
            "message_type" => 'is-success',
            "message" => '',
            "data" => $candidateDetail,
            "status" => 'success',
            "silent_progress" => true
        ];
    }
```