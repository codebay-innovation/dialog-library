# Issue repository [![Codebay Innovation](https://www.codebay-innovation.com/components-auto-generator/codebay_logo.png)](https://www.codebay-innovation.com/)
This is the main repository for report issues related with the Codebay AEM Dialog Library

# Dialog Library
[![Powered By Codebay Innovation](https://img.shields.io/badge/Powered%20By-Codebay%20Innovation-37c755?labelColor=27d1e0)](https://www.codebay-innovation.com/)

This dialog library provides many examples of different dialog configurations, with different layouts, widgets and utilities, that can be used by a developer when developing  a component dialog.

Check its functionality and directly copy the code to me moved to your project. 

This product has been designed to speed up the dialogs creation process, check it’s functionality and directly copy the code, and the use of best practices.

## Introduction

This dialog library provides many examples of different dialog configurations, with different layouts, widgets and utilities, that can be used by a developer when developing a component dialog.

Check its functionality and directly copy the code to me moved to your project. This product has been designed to speed up the dialogs creation process, check it’s functionality and directly copy the code, and the use of best practices. 

## Installation

### Local instance
To install the library on a local instance, you can directly install the provided package using the package manager.

### Cloud instance
To install the library on a cloud instance, you need to include the package on your project, and install it through the deployment pipeline. Follow the nexts steps to install the dialog library:

1. Create a new “resources” folder inside your ui.apps module
2. Add the connector package provided inside the “resources” folder
3. Add the following dependency on the dependencyManagement section of your main POM.xml
``` xml 
    <dependency>
        <groupId>com.codebay</groupId>
        <artifactId>dialog-library</artifactId>
        <version>1.0.0</version>
        <type>zip</type>
        <scope>system</scope>
        <systemPath>${project.basedir}/ui.apps/src/main/resources/dialog-library-1.0.0.zip</systemPath>
    </dependency>
```
4. Add de dependency in your POM.xml file of module “all”.
```xml
    <dependency>
        <groupId>com.codebay</groupId>
        <artifactId>dialog-library</artifactId>
        <type>zip</type>
        <scope>system</scope>
        <systemPath>${project.basedir}/../ui.apps/src/main/resources/dialog-library-1.0.0.zip</systemPath>
    </dependency>
```
5. Add the connector package as embedded depedency in “embeddeds” section of your POM.xml file of module “all”.
```xml
    <plugin>
        <groupId>org.apache.jackrabbit</groupId>
        <artifactId>filevault-package-maven-plugin</artifactId>
        <extensions>true</extensions>
        <configuration>
            ...
            <embeddeds>
                ...
                <embedded>
                    <groupId>com.codebay</groupId>
                    <artifactId>dialog-library</artifactId>
                    <type>zip</type>
                    <target>/apps/codebay-dialog-library-vendor-package/application/install</target>
                </embedded>
                ...
            </embeddeds>
            ...
        </configuration>
    </plugin>
```
6. Add a filter for the connector package on your filter.xml file of module “all”.
```xml
    <workspaceFilter version=”1.0”>
        ...
        <filter root=”/apps/codebay-dialog-library-vendor-package/application/install”/>
        ...
    </workspaceFilter>
```

After following the previous instructions, the deployment pipeline can be run in the desired environment and the library will be ready to use. 

## How to use

- Once the dialog library is installed it will be visible in the Sites section of AEM.
- Open the following page: /content/dialog-library/dialog-examples
- On this page, a list of different components is displayed, and each one contains an example.

    It displays a brief description of the functionality and, if applicable, the stored value once the dialog has been configured, so that the user can verify the correct behaviour.

    Inside the dialog of each copy, is provided a CTA “Copy code”.

    When clicking this button, the code of the widget is copied to the clipboard, so that it can be easily moved to the desired project.

    In case that another file must also be copied (such as an associated clientlib), an alert message is displayed, indicating the resource that must be copied (it is possible to get it from the CRX).
