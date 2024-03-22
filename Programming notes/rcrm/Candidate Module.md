![[Pasted image 20240322080327.png]]
![[Pasted image 20240322080526.png]]
> In the above picture we have sources from where we add the candidate. In the bottom we have all the actions we can perform on the candidates.
> **Extension** => candidates can be sourced from LinkedIn using chrome extension.
> **website** => clients website
> **Job bords** => different job Appling websites
> **Parser** => using recruit crm's resume parser.
> **API and Zapier** => can be used to add candidate using google form.
> **Hotlist** => we can create a hotlist of multiple candidates. for example if someone needs a java developer we can create a java developer hotlist.
> **Resume formatting** => recruiter can format the candidate resume according to his needs.


![[Pasted image 20240322081852.png]]
> This is the page we go to when we click on the candidates button on the sidebar.
> Here the state of the page includes which columns of the candidate will be visible to the user etc.
> 
![[Pasted image 20240322084800.png]]
> we can view the above page from admin => candidate fields.

![[Pasted image 20240322090127.png]]
![[Pasted image 20240322090721.png]]
> A user of the recruit crm's app can't change the type of the custom field directly for already imported candidates. He need to request `recruit crm` team to change the custom fields. 

![[Pasted image 20240322091337.png]]
> **slug** => slug is the last parameter of the URL.
> note task and appointments are stored in same table. we separate them using type column. for notes type = 0. for tasks type = 1 and for appointments type = 2.
> 
![[Pasted image 20240322093631.png]]
> File paths are not stored in the database. we identify the files based on the entity and slug. we need to provide entity and slug to s3 and on basics of that s3 will return us the documents.
> S3 does not allows us to create folders. so we we store folder structure on our end.
> 
![[Pasted image 20240322094658.png]]

