# RH-SSO Quickstarts

The quickstarts demonstrate securing applications with RH-SSO. They provide small, specific, working examples
that can be used as a reference for your own project.


Introduction
------------

These quickstarts run on Red Hat JBoss Enterprise Application Platform 6.4 or 7.

Prior to running the quickstarts you should read this entire document and have completed the following steps:

* [Start and configure the RH-SSO Server](#rh-sso)
* [Start and configure the JBoss EAP Server](#jboss-eap)

Afterwards you should read the README file for the quickstart you would like to deploy. See [examples](#examples) for
a list of the available quickstarts.

If you run into any problems please refer to the [troubleshooting](#troubleshooting) section.

TODO: add steps for OCP deployment.

<a id="rh-sso"></a>Start the RH-SSO Server
------------------------------------------

By default the RH-SSO Server uses the same ports as the JBoss EAP Server. To run the quickstarts you can either run the
 RH-SSO Server on a separate host (machine, VM, Docker, etc..) or on different ports.

To start the RH-SSO server on a separate host:

1. Open a terminal on the separate machine and navigate to the root of the RH-SSO server directory.

2. The following shows the command to start the RH-SSO server:

   ````
   For Linux:   RHSSO_HOME/bin/standalone.sh -b 0.0.0.0
   For Windows: RHSSO_HOME\bin\standalone.bat -b 0.0.0.0
   ````

3. The URL of the RH-SSO server will be http://&lt;HOSTNAME&gt;:8080 (replace &lt;HOSTNAME&gt; with the hostname of the separate host).

To start the RH-SSO server on different ports:

1. Open a terminal and navigate to the root of the RH-SSO server directory.

2. The following shows the command to start the RH-SSO server:

   ````
   For Linux:   RHSSO_HOME/bin/standalone.sh -Djboss.socket.binding.port-offset=100
   For Windows: RHSSO_HOME\bin\standalone.bat -Djboss.socket.binding.port-offset=100
   ````

3. The URL of the RH-SSO server will be *http://localhost:8180*

### <a id="add-admin"></a>Add Admin User

Open the main page for the RH-SSO server ([localhost:8180](http://localhost:8180) or http://&lt;HOSTNAME&gt;:8080). If
this is a new installation of RH-SSO server you will be instructed to create an initial admin user. To continue with
the quickstarts you need to do this prior to continuing.

### <a id="add-roles-user"></a>Create Roles and User

To be able to use the examples you need to create some roles as well as at least one sample user. To do first this open
the RH-SSO admin console ([localhost:8180/auth/admin](http://localhost:8180/auth/admin) or http://&lt;HOSTNAME&gt;:8080/auth/admin) and
login with the admin user you created in the [add admin user](#add-admin) section.

Start by creating a user role:

* Select `Roles` from the menu
* Click `Add Role`
* Enter `user` as `Role Name`
* Click `Save`

Next create a user:

* Select `Users` from the menu
* Click `Add user`
* Enter any values you want for the user
* Click `Save`
* Select `Credentials` from the tabs
* Enter a password in `New Password` and `Password Confirmation`
* Click on the toggle to disable `Temporary`
* Click `Reset Password`
* Click `Role Mappings`
* Select `user` under `Available Roles` and click `Add selected`

As an alternative to manually creating the role and user you can use the partial import feature in the admin console and import
the file [config/partial-import.json](config/partial-import.json) into your realm.

One more step, if you want to access the examples with the admin user you need to add the `user` role to admin user:

* Select `Users` from the menu
* Click `View all users`
* Click `Edit` for admin user
* Click `Role Mappings`
* Select `user` under `Available Roles` and click `Add selected`

