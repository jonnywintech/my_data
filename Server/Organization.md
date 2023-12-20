to organize files you can place main domain in main folder and leave rest for subdomain folder

#### Folder structure

|`folder name`|`description`|
|---|---|
|main|main domain|
|subdomain|rest of websites|

|
|-- main
|-- subdomains

Create or edit .htaccess file in root folder and give it following code
```.htaccess
# .htaccess main domain to subfolder redirect
# Copy and paste the following code into the .htaccess file
# in the public_html folder of your hosting account
# make the changes to the file according to the instructions.
  
# Do not change this line.
RewriteEngine on
  
# Change yourdomain.com to be your main domain.
RewriteCond %{HTTP_HOST} ^(www.)?yourmaindomain.com$
  
# Change 'subfolder' to be the folder you will use for your main domain.
RewriteCond %{REQUEST_URI} !^/subfolder/
  
# Don't change this line.
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
  
# Change 'subfolder' to be the folder you will use for your main domain.
RewriteRule ^(.*)$ /subfolder/$1
  
# Change yourdomain.com to be your main domain again.
# Change 'subfolder' to be the folder you will use for your main domain
# followed by / then the main file for your site, index.php, index.html, etc.
  
RewriteCond %{HTTP_HOST} ^(www.)?yourmaindomain.com$
RewriteRule ^(/)?$ subfolder/index.php [L]<div class="open_grepper_editor" title="Edit & Save To Grepper"></div>
```
replace `yourdomain.com` and `subfolder` with your domain and folder names