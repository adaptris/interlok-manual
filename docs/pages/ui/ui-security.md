The GUI web application allows multiple users to log-in using one of the existing roles:

Role | Privileges | Meaning
------------ | ------------- | ------------
Admin | access to all pages (with operational access) | An admin has all the rights in the web application, he can start/stop Adapters, Channels and Workflows, access the Runtime page and add any widget, access the config page and modify the Adapter configuration and also manage (add/edit/delete) users.
User | access to dashboard, widgets, config (with operational access) | A user can do most of what the admin can do except undertaking any User management action. Most users should have this role allocated.
Monitor | access to dashboard, widgets (with operational access) | A Monitor user can use the dashboard controls to start and stop various components and they can use the widgets page to monitor the containers, but they can not alter config nor do they have access to security settings.
View Only | access to dashboard, widgets (no operational access) | A view only user cannot change the state of the application except in the Runtime page. It means that he will not be able to start/stop any Adapter, Channel and Workflow, neither be able to access the Adapter configuration page nor the User page. This role is design for monitoring only.
Disabled | no access to the webapp | A disabled user cannot log in the application. This role is design for temporarily not alowing access to a user.

## Login ##

From 3.11 URL rewriting for jsessionid has been disabled. URL rewriting has significant security risks and is generally not recommended.

The general idea is that since the session id appears in the URL, it may be easily seen by third parties:
- Users often copy and paste  links without knowing the attached session id compromises their security
- Server log files can record the 'Referer' header, which will record session ids in the log

If you want to use URL rewriting for jsessionid for any reasons (for instance cookies disabled in the browser) you will have to modify the web.xml in the webapp/interlok-ui.war file.
Open or extract the war file, edit the web.xml and remove:

```xml
<context-param>
  <param-name>org.eclipse.jetty.servlet.SessionIdPathParameterName</param-name>
  <param-value>none</param-value>
</context-param>
````

You can read more information about it on the [Jetty Documentation Site](https://www.eclipse.org/jetty/documentation/9.2.22.v20170531/session-management.html#setting-session-characteristics).

## User page ##

You can access the User page by clicking on the down arrow next to your user name and on the User Admin item. The User page lists all the users able to access the GUI web application. After a fresh installation the GUI will only have the admin user.

![User Page](../../images/ui-user-guide/user.png)

## Add User ##

If an admin wishes to add a new User he should click on the Add User button.

![User Page - Add User Button](../../images/ui-user-guide/user-add-user-button.png)

Clicking on the Add User button will open a modal window containing a form that need to be filled.

![User Page - Add User Form](../../images/ui-user-guide/user-add-user-modal.png)

- Username: User identifier. Required to log in.
- First Name: User first name.
- Last Name: User last name.
- Password: Password needed to log in.
- Confirm Password: Confirm that the password has been entered correctly. The confirm password should be type and not copied from the password.
- Roles: Permission role given to a user. If no role has been selected the user will not be able to log in.
- Display Welcome?: Whether or not the user should have the Welcome splash screen on his first login.

When created a User is added to the user list.

![User Page with two users listed](../../images/ui-user-guide/user-two-users.png)

## Edit User ##

A user can be edited using the edit User button.
![User Page - Edit User Button](../../images/ui-user-guide/user-edit-user-button.png)

The edit User modal is the same as the add User modal. The only differences are:
- The username cannot be changed.
- The password doesn't need to be provided. If left blank it will remain the same.
- A user cannot change his role if editing himself.

## Delete User ##

If not needed a User can be easily deleted using the delete User button.
![User Page - Delete User Button](../../images/ui-user-guide/user-delete-user-button.png)

The application will ask for confirmation. Deleting a user means that he will not be able to access the GUI web application anymore and that his Runtime page settings will be lost. A User is not allowed to delete himself.
