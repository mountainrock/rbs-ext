# Introduction #

  1. Server Requirements
  1. Installation
  1. Email Templates
  1. Multi-Language Setup
  1. Template Customization
  1. Troubleshooting
  1. Files for Cron jobs
  1. Version History

# Details #



---

**Server Requirements**

  * Operating System: Linux, Windows
  * Web Server: Apache
  * PHP 5 or higher
  * MySQL 5 or Higher
  * Mod\_rewrite
  * Cron Jobs
  * GD library

**Installation**

  1. Upload all files in the archieve to the root directory or subdirectory (i.e yoursite.com/site).
  1. Run the /install directory to install the system (i.e yoursite.com/site/install)


**Manual Installation**

  1. Edit the file app/config/config.php and edit your mysql details in the following lines:
```
$config['hostname'] = "hostname";
$config['db_username'] = "mysqluser";
$config['db_password'] = "mysqlpass";
$config['db'] = "mysqlDB";
```
  1. $config['base\_url'] = "Site URL "; (i.e yoursite.com/site)
  1. In PhpMyAdmin, import the file install/cogzidel.sql to create the database structure.
  1. Change the permission of the following folders and its subdirectories to 0777:
```
/files/logos

/files/portfolios
/files/project_attachment
/files/site_logo
/files/tempFiles
/install
/app/config
```
  1. You are done
  1. To access the admin panel /siteadmin (i.e yoursite.com/site/index.php/siteadmin), login with user: admin pass: admin on the main member login page



**Email Templates**

Steps to access email templates used in the system

  1. Go to /siteadmin (i.e yoursite.com/site/index.php/siteadmin)
  1. Login with user: admin pass: admin
  1. You will see "Email templates" link on the right side of the page. Click on that
  1. You can see list of email templates used, and there is edit icon to view and edit the contents
  1. In the content area , you can see some variables started with "!" symbol, that means those varibles will be replaced in the user end while sending mails
  1. For example "!site\_title" is used in some email templates, this varibles should be replaced with "http://yoursite.com/site" in the front end
  1. You can add new email templates here


**Multi-Language Setup**

  * Edit current language files
> > The default language we have used is "english" in app/config/config.php $config['language'] = "english";


> As of now, there is only one folder app/language/english, it has 2 folders "enduser" and "admin" , there you can find _lang.php files. Each one is corresponding to /controllers_

  * Create new language files
```
1. Go to the folder /app/language and create a new folder using the name of your language code (eg:spanish)

2. Create 2 new folders "enduser" and "admin" inside /spanish folder

3. Language files must be named with _lang.php as the file extension.For example, lets say you want to create a file containing error messages. 
You might name it: error_lang.php Within the file you will assign each line of text to an array called $lang with this prototype:$lang['language_key'] = "The actual message to be shown"; 

4. Load the language file created in /controller files, for eg: $this->lang->load('filename', 'language'); 
Where filename is the name of the file you wish to load (without the file extension), and language is the language set containing it (ie, english). If the second parameter is missing, the default language set in your app/config/config.php file will be used. 

5.Then go to admin panel -> Site settings tab -> update the "Language Code" to the name of your language folder (eg:spanish) 

```



**Template Customization**

Editing RBS design is very simple by modifying the php and CSS files. The location of the template files for the design can be found in folder:
```
/app/views/

/app/views/(header.php|footer.php) -The location of the header/footer files.
/app/css/css(front end CSS)
/app/css/ (admin area CSS) 
```

**Troubleshooting
```
1. Help, I am getting HTTP error 400 when accessing my site!

You will need to enable mod_rewrite option on your apache server
```**

**Files for Cron jobs
```
1. project/bidConsolidate()

2. project/newProjectsNotify()

3. project/biddingEndCheck()

You can run the files directly as (i.e yoursite.com/site/project/bidConsolidate)
```
8. Version History**

RBS version 1.6 RC3 (Beta release)