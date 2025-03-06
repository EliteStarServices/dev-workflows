# CURRENTLY THIS FILE IS A PLACEHOLDER (not fully updated)

## ClassicPress Development Server

### Installing XAMPP

SOME VERSIONS OF XAMPP USE MARIADB  
Windows Version Shown Here, Linux and OSX Versions are also available.

  

Download the installer from [**Apache Friends**](https://www.apachefriends.org/index.html). When the download finishes, run the XAMPP installer. Click Next to choose which components to install.

![](https://elite-star-services.com/wp-content/uploads/self-host-img/xampp-welcome.png)

In addition to the required components (Apache & PHP), you should select:

*   **MySQL** (or MariaDB)
*   **phpMyAdmin**

Once the options you need are selected, click Next.

![](https://elite-star-services.com/wp-content/uploads/self-host-img/xampp-select.png)

You can select the folder to install XAMPP, but we suggest you leave it as the default:

![](https://elite-star-services.com/wp-content/uploads/self-host-img/xampp-folder.png)

Choose your preferred language and click Next.

![](https://elite-star-services.com/wp-content/uploads/self-host-img/xampp-lang.png)

Click Next when you are ready to run the installer...

![](https://elite-star-services.com/wp-content/uploads/self-host-img/xampp-install.png)

When the install finishes, launch the Control Panel to start working with XAMPP.

![](https://elite-star-services.com/wp-content/uploads/self-host-img/xampp-control.png)

### Start & Test your XAMPP Server

For everything to work, you need to start the two modules shown below:

*   **Apache**
*   **MySQL** (or MariaDB)

Start the modules using the XAMPP Control Panel:

![](https://elite-star-services.com/wp-content/uploads/self-host-img/xampp-start.png)

Once running, you should see the status change to green:

![](https://elite-star-services.com/wp-content/uploads/self-host-img/xampp-status.png)

Test that your server is working locally by going to `http://localhost/` in a browser. If you see a page similar to the image below, you have a functioning XAMPP Server.

![](https://elite-star-services.com/wp-content/uploads/self-host-img/xampp-working.png)

### Adding ClassicPress to the Server

First, you need to visit [**ClassicPress.net**](https://www.classicpress.net/get-classicpress/) and download the latest version of ClassicPress. Now in Windows, navigate to the folder where you installed XAMPP. If you stayed with the installation default that should be `C:/xampp`. Find the **htdocs** subfolder and extract the zip file you downloaded from ClassicPress.net into it. _\* You can safely delete the existing files and folders in htdocs or you can leave them alone (we deleted them)_ If you deleted them as we have, the folder should now look like this.

![](https://elite-star-services.com/wp-content/uploads/self-host-img/cp-files.png)

### Create a Database for ClassicPress

You need to create a database for ClassicPress to use. Launch phpMyAdmin by clicking Admin for the MySQL Module:

![](https://elite-star-services.com/wp-content/uploads/self-host-img/xampp-admin.png)

Now click **Databases** at the top of the phpMyAdmin page as shown:

![](https://elite-star-services.com/wp-content/uploads/self-host-img/cp-create-1.png)

Enter the desired name for your database (or use our example) and click **Create**.

![](https://elite-star-services.com/wp-content/uploads/self-host-img/cp-create-2.png)

For a Live Web Server, there are serious security concerns with the following configuration, but for local development & testing, creating a database user is not required. Be aware that the XAMPP Server currently has no root database user password and that needs to be corrected if the server is ever connected to the internet.

### Run the ClassicPress Installer

Now You should be able to visit your site at `http://localhost/` and see the ClassicPress installer. Select your desired language and then click Continue.

![](https://elite-star-services.com/wp-content/uploads/self-host-img/cp-install.png)

Now You should shown the following information page, when ready click Let's go!

![](https://elite-star-services.com/wp-content/uploads/self-host-img/cp-info.png)

Next is the database details, enter them like this:

*   **Database Name** - Name of the database created with phpMyAdmin (testsite)
*   **Username** - root
*   **Password** - leave blank

Once the information is entered, click Submit.

![](https://elite-star-services.com/wp-content/uploads/self-host-img/cp-data.png)

This page confirms that ClassicPress has found your database, when ready click Run the installation.

![](https://elite-star-services.com/wp-content/uploads/self-host-img/cp-run.png)

Next are a few Site Details, you can use our examples or your own settings. When finished, click Install ClassicPress.

![](https://elite-star-services.com/wp-content/uploads/self-host-img/cp-finish.png)

If the installation completes successfully you should see this page. Click Log In to access your site.

![](https://elite-star-services.com/wp-content/uploads/self-host-img/cp-login.png)

Now use your name and password to Log In.

![](https://elite-star-services.com/wp-content/uploads/self-host-img/cp-user.png)

You should now have a working ClassicPress site running at `http://localhost/` and can start to develop.

![](https://elite-star-services.com/wp-content/uploads/self-host-img/cp-site.png)