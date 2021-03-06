The GUI web application allows to configure some properties to change the ui resources file system path (Since 3.0.5) and new component Id generator:

![System Preferences](../../images/ui-user-guide/system-preferences.png)

You can access the System Preferences page by clicking on the down arrow next to your user name and on the System Preferences item.

## System Preferences page

The system preferences are:

- **Config Template Url:** Directory where are located the UI templates used in the configuration page.
- **Config Export Url:** Directory where adapter configuration file get exported. The export is done in the configuration page. (Removed Since 3.7.1).
- **Config Store Url:** Directory where configurations are saved (and auto saved).
- **Config Project Store Url:** Directory where configurations projets are saved (and auto saved) (Since 3.7.0).
- **Vcs Repo Url:** Directory where all the VCS (Suversion, Git) repositories get stored.
- **Id Generator:** Random Id generator strategy for new component in the configuration page: (Since 3.5.0).
    - **Random Name:** The generated Id will be a mix of a random famous scientist surname and a random adjective, e.g. amazing-darwin. (Default Since 3.5.1).
    - **Class Name and Random Id:** The generated Id will be a mix of the component class name or alias and a random number, e.g. Channel-1209003.
    - **Creates a GUID using com.adaptris.util.GuidGenerator:** The ID is generated using the com.adaptris.util.GuidGenerator class, e.g. 37cc799e-bd50-4560-a735-1320e0a78ebe.
- **Disable External Resources:** Disable automatic loading of external resources such as optional components information or Interlok blog articles. (Since 3.9.3).

?> **NOTE** All the changes require a container restart to take effect.

## System Properties

The system preference **Disable External Resources** can be set using the system property *interlok.ui.disableExternalResources*:

```
-Dinterlok.ui.disableExternalResources=true
```

for example, to start interlok and disable automatic external resources loading:

```
java -Dinterlok.ui.disableExternalResources=true -jar lib/interlok-boot.jar 
```
