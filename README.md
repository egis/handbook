## Getting started

This wiki describes how to install supporting Papertrail tools for development on your Mac. Before we can start, you 
need to go through the [Mac OSX Setup guide](http://sourabhbajaj.com/mac-setup/) to help you install all the baseline 
tools that are required.

**NOTE :** As you read and follow these steps, please feel free to send any feedback or comments you may have.

### Additonal tools

The following additional tools need to be installed as they are not part of the baseline setup. It is 
advisable to use Brew to install these packages as it will help manage future updates/upgrades :

* **PostgreSQL 9.4** : bash brew install homebrew/versions/postgresql94
* **PgAdmin3**  : brew cask install pgadmin3
* **Gradle**  : brew install gradle  
* **IntelliJ** : brew cask install intellij-idea 
* **LibreOffice** : brew cask install libreoffice 
* **Hipchat** : brew cask install hipchat

### Papertrail source

All Papertrail source is located in the [Mailcomp (Pty) Ltd t/a Egis GitHub Repo](https://github.com/egis).
There, you will find sub-repositories that contain a description of the module/sub-modules. Read this carefully as it 
will give you and in-depth overview of how the module/sub-modules operates.
                                                                                                                                 
### Papertrail Dev Portal

In laymen terms, Papertrail has a UI and backend component. To understand Papertrail in more detail, have a look at the 
[PaperTrail Developer Portal](http://developer.papertrail.co.za/#bootstraping-projects) for a in-depth understanding on 
it's components, how to build and deploy them, how they go through the Dev Ops Cycle,etc
