# Error when try to upload files.

steps:
- open .env and check for APP_URL  " it must be same as your site url"
- check for file permissions 
- check did you link your storage 
- check in php.ini file for temp upload_tmp_dir = c:\windows\temp or other folder if exist on linux ( this is usualy windows specific error)