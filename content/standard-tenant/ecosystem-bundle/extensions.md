---
title: Extensions
layout: bundle
weight: 30
section:
  - platform_administration
helpcontent:
  - label: extensions
    title: Extensions
    content: "On the **Extensions** page, you find a list of all extension packages available in your tenant. Extension packages are combinations of plugins and blueprints which can be packed together into a single file and deployed to the platform. To add a new extension package, click **Add extension package** at the top right."
---

Click **Extensions** in the **Ecosystem** menu in the navigator to display all extensions in your account.

Extensions make it easier to share and reuse UI features across different applications. UI features can be developed as plugins and added to an application without coding knowledge. There are two types of extensions:

- Plugins
- Blueprints

Blueprint applications must be deployed, while plugins are added to other applications. This allows you to scaffold entire solutions or to extend existing ones. Due to the micro frontend technology, this can happen at runtime without rebuilding.

### Plugins {#plugins}

Switch to the **Plugins** tab of an application to view all plugins installed on an application.

<img src="/images/users-guide/Administration/admin-application-plugins-grid.png" alt="Plugins grid" style="max-width: 100%">

In the **Plugins** tab you can add and remove plugins. Additionally, you can install plugins to an application.



### Packages {#packages}

Packages are combinations of plugins and blueprints which can be packed together into a single file and then be deployed to the platform. Thus, packages offer better shareability and reusability of UI features across different applications and allow to add UI features to applications without coding knowledge.

Packages can contain two types of content:

- [**Plugins**](#plugins) can be used to extend existing applications without the need of re-building the application.
- **Blueprints** are combinations of multiple UI functionalities which can be hosted by the platform and can be used to create a new application from scratch.

Packages can be located on the **Packages** tab in the **Applications** page.

<img src="/images/users-guide/Administration/admin-application-packages.png" alt="Packages view">

Packages can be filtered by name, creator type, availability and type of content.

To add a new package click **Add extension package** at the top right.

By clicking on a package, you can see the package details such as **Package overview** which includes a description and images as well as some meta information which is taken from the *package.json*.

Additionally, it is possible to view all available plugins within the selected package at the right. To install a plugin click **Install plugin** and select the desired application.  

<img src="/images/users-guide/Administration/admin-application-packages-info.png" alt="Packages overview">

In the **Versions** tab, you see all previously uploaded binaries related to the current package. The binaries displayed on this tab can be downloaded via the context menu next to each package version entry.

<img src="/images/users-guide/Administration/admin-application-packages-versions.png" alt="Versions view">

You can select or upload different versions. Versions indicate the state of the package. They can be used to verify whether a certain package is outdated and needs to be updated. By clicking on a version additional information is provided such as package contents, applications or plugins. Tags can be used to give versions meaningful names. The "latest" tag is used to indicate the default version which will be selected in case no tag is provided. The "latest" tag is set by default to the latest version whenever a version is uploaded without a given tag.

To switch to a different version open the context menu for the desired version and click **Set as latest**. To delete a version click **Delete**.
