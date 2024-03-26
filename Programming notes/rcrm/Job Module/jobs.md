https://rcrm.atlassian.net/wiki/spaces/EN/pages/1899790341/Module+-+Jobs+For+Technical+Session+Feb+17+2022
![[Pasted image 20240326070745.png]]
- **Premium job boards** => we need to pay for posting the job.
- **Free job boards** => we dont need to pay.

## _**Access Control:**_

|                        |             |                          |            |            |                  |                 |
| ---------------------- | ----------- | ------------------------ | ---------- | ---------- | ---------------- | --------------- |
| **Role**               | **Add Job** | **View Job**             | **Edit**   | **Delete** | **Change Owner** | **File Access** |
| Account Owner          | Yes         | Everything               | Everything | Yes        | Yes              | Everything      |
| Admin                  | Yes         | Everything               | Everything | Yes        | Yes              | Everything      |
| Team Member            | Yes         | Everything               | Everything | No         | Owned Only       | Everything      |
| Restricted Team Member | Yes         | Owned Only/ Collaborator | Owned Only | No         | Owned Only       | Everything      |
In recruit crm we have above 4 type of roles.

- We can change different settings in job application form in admin settings.
- `default job application form visibility`. If checked candidates can apply to the job from outside.
- `post on job boards.` => when a new job is added it will get automatically get posted in free job boards. 
### Assigned candidates.
- `All candidates` => All candidates which are assigned to a job. 
- `visibility` => if the candidate is visible to the contact associated with the job.
- `field shared with clients` => the columns which are shared with the clients.
- In admin settings we can set global visibility for the columns.
- `submit candidates` => we can either submit a list of candidates or we can submit a link by clicking which contacts can view the candidate list.
- by clicking the link clients can view the candidate and also edit the candidate status and submit client feedback.
- users can view client feedback in client feedback page.
- `related deals` => If someone adds the job to any deal the the deal will be shown in related deal section.
### Job Status
- we can change the available job statuses in admin settings.
- We can change the job status from admin page
- list of all available job statuses are stored in `tbl_jobstatus`
- we also store custom job statuses in this table along with the `account_id`.

### Public job page settings
- we can access this settings in admin section
- To upload the jobs automatically to job boards you have to fill-up the fields which are required to post in job boards.
- If I edit the job inline then the job will not get posted.
- However if we update the job in update job from then the job will get posted.
- To check whether the job is posted in the job board or not. => run the following raw query in admin => `raw database`
![[Pasted image 20240326211937.png]]
- when the job posting status column has value 4 that means the job is posted.
- For a job to get posted in free job boards. it should be in open stage. And it should be updated in last 7 days for free plan and last 30 days for business plan.
- 