# Local Development Server Setup

There are many ways to get live and local web servers running, too many for us to mention. The ClassicPress Community can probably help with your specific configuration, but for simplicity, we suggest anyone not familiar with web services should follow this guide and setup XAMPP as a Local Web Server to make it easier for us to help you.

## Installing XAMPP

(some versions of XAMPP use MariaDB)  
*Windows Version Shown Here, Linux and OSX Versions are also available*

- Download the installer from [**Apache Friends**](https://www.apachefriends.org/index.html)  
- When the download finishes, run the XAMPP installer  
- **Click Next to choose which components to install**

![XAMPP Welcome](/dev-docs/img/xampp-welcome.png)

### In addition to the required components (Apache & PHP), you should select

- **MySQL** (or MariaDB)
- **phpMyAdmin**

### Once the options you need are selected, click Next

![XAMPP Select](/dev-docs/img/xampp-select.png)

### You can select the folder to install XAMPP, but we suggest you leave it as the default

![XAMPP Folder](/dev-docs/img/xampp-folder.png)

### Choose your preferred language and click Next

![XAMPP Lang](/dev-docs/img/xampp-lang.png)

### Click Next when you are ready to run the installer

![XAMPP Install](/dev-docs/img/xampp-install.png)

### When the install finishes, launch the Control Panel to start working with XAMPP

![XAMPP Control](/dev-docs/img/xampp-control.png)

## Start & Test your XAMPP Server

### For everything to work, you need to start the two modules shown below

- **Apache**
- **MySQL** (or MariaDB)

### Start the modules using the XAMPP Control Panel

![XAMPP Start](/dev-docs/img/xampp-start.png)

### Once running, you should see the status change to green

![XAMPP Status](/dev-docs/img/xampp-status.png)

### Test that your server is working locally by going to `http://localhost/` in a browser

**If you see a page similar to the image below, you have a functioning XAMPP Server.**

![XAMPP Working](/dev-docs/img/xampp-working.png)

## Adding ClassicPress to the Server

At this point there is a different configuration if you planned on contributing code to [ClassicPress Core](https://github.com/ClassicPress/ClassicPress/blob/develop/.github/CONTRIBUTING.md) (the main files that make up the ClassicPress Package). This document deals with installing ClassicPress locally so you can test it and see how things work, this configuration is also fine if you are designing Plugins or Themes for ClassicPress or to submit add-ons to the [ClassicPress Directory](DIRECTORY_SUBMISSIONS.md).

To start, you need to visit [**ClassicPress.net**](https://www.classicpress.net/get-classicpress/) and download the latest version of ClassicPress. Now in Windows, navigate to the folder where you installed XAMPP. If you stayed with the installation default that should be `C:/xampp`. Find the **htdocs** subfolder and extract the zip file you downloaded from ClassicPress.net into it. *\* You can safely delete the existing files and folders in htdocs or you can leave them alone (we deleted them)* If you deleted them as we have, the folder should now look like this.

![CP Files](/dev-docs/img/cp-files.png)

## Create a Database for ClassicPress

### You need to create a database for ClassicPress to use  

**Launch phpMyAdmin by clicking Admin for the MySQL Module:**

![XAMPP Admin](/dev-docs/img/xampp-admin.png)

### Now click **Databases** at the top of the phpMyAdmin page as shown

![CP DB](/dev-docs/img/cp-create-1.png)

### Enter the desired name for your database (or use our example) and click **Create**

![CP Create](/dev-docs/img/cp-create-2.png)

**For a Live Web Server, there are serious security concerns with the following configuration, but for local development & testing, creating a database user is not required. Be aware that the XAMPP Server currently has no root database user password and that needs to be corrected if the server is ever connected to the internet.**

## Run the ClassicPress Installer

### You should be able to visit your site at `http://localhost/` and see the ClassicPress installer

**Select your desired language and then click Continue.**

![CP INstall](/dev-docs/img/cp-install.png)

### Now You should be shown the following information page, when ready click Let's go!

![CP Info](/dev-docs/img/cp-info.png)

### Next are the database details, enter them like this

- **Database Name** - Name of the database created with phpMyAdmin (testsite)
- **Username** - root
- **Password** - leave blank

### Once the information is entered, click Submit

![CP Data](/dev-docs/img/cp-data.png)

### This page confirms that ClassicPress has found your database, when ready click Run the installation

![CP Run](/dev-docs/img/cp-run.png)

### Next are a few Site Details, you can use our examples or your own settings

**When finished, click Install ClassicPress**  
![CP Finish](/dev-docs/img/cp-finish.png)

### If the installation completes successfully you should see this page

**Click Log In to access your site**  
![CP Login](/dev-docs/img/cp-login.png)

### Now enter your Username and Password to Log In

![CP User](/dev-docs/img/cp-user.png)

**You should now have a working ClassicPress site running at `http://localhost/` and can start to develop**

![CP Site](/dev-docs/img/cp-site.png)
