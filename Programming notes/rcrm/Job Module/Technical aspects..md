- All jobs are stored in `tbljobs`
- `viewjob` => Is  a `sql` `view` => It contains all the tables required in frontend
- `jobs_custom_fields_t` => stores custom fields for jobs
- `job_secondery_contacts` => we store relation between job and contacts.
- `jobs.json` => works similar to `candidates.json`. stores all default settings related to jobs table. 
- When used changes the default settings in the jobs table the new settings gets saved in `tbl_datatable_settings` 
- `$router->post('/search/get', 'JobController@search');` => fetches the jobs table according to the table settings.
- similar to `candidate` in `entityColumns.php` we have a case for jobs also. If the user updates default table settings it will get stored in the database. In `entityColumns.php` we first fetch `jobs.json` the we try to fetch the settings from database which user has updated.
##### Job List page
- for all cases where we fetch a list (candidate, contact, company, jobs). we use `searchEntity.php`.
- In `searchEntity.php` we only deal with the views like `viewCandidate`, `viewContact`, `viewDeals`, etc.

##### Add job
1. `jobRepositary.php` => add job function.
2. It is called through the `jobController.php`.
3. here we store the values of default columns `tbl_jobs` and the value of custom columns in `job_customcolumn` table.
4. After saving the job if the job has job description file then we move that job to that particular job's slug location.
5. If the job has address then we use that address for radius search.
6. if the job has secondary contacts then we also add some entries to `secondary_contacts` table.
##### Job Details
- uses `jobRepositary` => `showJob` function.
- `showJob` accepts the slug and based on the slug it fetches the job from `viewJob`.
- In this function we also check for the access control. 
- with the response we also send previous job record and next job record to work with previous and next buttons.
##### Assigned candidates
- `jobRepositary` => `getCandidatesByJob` => To fetch the candidates assigned to a job.
- here we check if the `assigned candidates` table is in list view or `canban` view. if `$page == 'widget'` then it is in list view else in `canban` view. Here widget means 1 row (I think).

##### CV Library
- It is a job board
- `CvLibraryRepository.php` used for integration with CV library (https://www.cv-library.co.uk/)
- Weever we add the job and cv library settings are available in the user object.
- When job is added successfully we will call `postJobToCvLibrart function`
- CV library settings are stored in `tbl_cv_library_settings` in that table we store CV Library `username` `email` `password`  We use these credentials to authenticate with cv library and post the job. 
- If the job is successfully posted cv library returns an id. We store this id in `tbl_jobs` table in the column `cv_job_posting_id`.