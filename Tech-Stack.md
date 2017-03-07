## Programming Stack

| Tech                            | Use  | Reason                                   | Lifecycle |
| ------------------------------- | ---- | ---------------------------------------- | --------- |
| Java 8 / JVM                    |      |                                          |           |
| Groovy                          |      | Developer friendly especially for scripting, XML and JSON |           |
| Egis Kernel                     |      | Created before CgitDI and friends were released, Migrade to CDI API - To consider migration to full CDI kernel. |           |
| Hibernate / JPA                 |      | Need to support multiple DB platforms    |           |
| Jetty                           |      | Easily embeddable                        |           |
| Hazelcast                       |      | Easily embeddable, more activity than JGroups |           |
| PostgreSQL / MySQL / SQL Server |      | 3 most common db platforms               |           |
| Lucene                          |      | Easily embeddable, supports single node and custom filters for advanced ACL's |           |
| TestNG                          |      | Better support for listeners, ignores etc. |           |
| C#                              |      |                                          |           |
| Golang                          |      | A better alternative to C and C++        |           |
| Python                          |      | Developer friendly, available by default on Ubuntu |           |
| Markdown                        |      | Ease of onboarding / migration between platforms - Easily diffable for PR's |           |
| Gitbook                         |      | Most mature, open source platform - Outgrew MkDocs |           |
| ES6 / Babel                     |      | Coffeescript is on life support, Typescript support for duck typing, importing plugins etc is more limited |           |
| NPM                             |      | Consider migrating to Yarn               |           |
| Gulp                            |      | Faster than grunt with better and more up to date plugins |           |
| Webdriver                       |      |                                          |           |
| Karma / Jasmine                 |      |                                          |           |
| ExtJS                           |      | Lack of backwards compatibility, unfriendly licensing for app builders | EOL       |
| Angular (1 or 2)                |      | Too complex to learn / debug - Lack of backwards compatibility | EOL       |
| Vue.js                          |      | To test and consider - values align to our culutral manifesto - primarily KISS | New       |
|                                 |      |                                          |           |
|                                 |      |                                          |           |



## Build Stack

| Tech           | Use                                      | Reason                                   | Lifecycle             |      |
| -------------- | ---------------------------------------- | ---------------------------------------- | --------------------- | ---- |
| **Gradle**     |                                          | Supports everything maven does, but is more customizble/plugable while also being less verbose |                       |      |
| **Ant**        |                                          | Aging technology                         | Migrate to gradle/npm |      |
| **Babel Gulp** |                                          |                                          |                       |      |
| **npm**        | javascript artificact repository         |                                          |                       |      |
| **Github**     | Code repository, review, documentation hosting |                                          |                       |      |
| **CircleCI**   | Primary build environment                | Cheaper then Travis CI - Supports MacOSX |                       |      |
| **AppVeyor**   | Build server for windows based projects  | Only SaaS CI with windows support        |                       |      |
| **Jenkins**    | Build server for old client projects     | Limited support for autoscaling - requires non trivial maintenance of slaves | Migrate to CircleCI   |      |
| **Codacy**     | Code linting                             | Support for Java and JS                  |                       |      |
| **Codecov**    | Code coverage                            | Migrate to codacy to unify quality metrics | Migrate to codacy     |      |
| **Amazon S3**  | Installer repository, Jar repository - Nexus, JFrog or the more common alternatives | S3 is dependency free and low cost with +- 1GB per day of artifacts |                       |      |



## Infrastructure



| Infrastructure  | Use                                      |
| --------------- | ---------------------------------------- |
| Ubuntu LTS      | Server OS                                |
| Docker          | Used in builds and dev/test environments - being assessed for production usage |
| PostgreSQL      | SaaS primary database due to better data integrity and friendlier licensing |
| ansible         | cluster management and local machine environment |
| VMWare ESXi     | Virtualization provider                  |
| VMWare vCenter  | EOL - Appliance proved very unreliable, esx-cli replications 90% of functions |
| Amazon EC2      | DR "site" - we spin up, deploy and restore backups from S3 |
| Amazon S3       | Backups for both blobs and database backups. 1 bucket per tenant/client |
| Amazon DynomoDB | Basic storage of tenants, used in DR to know which clients to restore |
| Cloudflare      | There are local DNS and cache edge servers, Upgradability to WAF is nice to have |
| Google Drive    | WIP specs, on project completion docs should be archived to PT |
| Sendgrid        | SMTP server                              |
| Google Apps     | Email (IMAP/POP) provider                |
| Hipchat         | Team chatrooms, Might migrate to Slack at some point |
| Corello         | Trello analysis                          |
| Trello          | High level dev and sales tracking        |
| Fortigate       | Firewall and IPS - Reasonable prices, Out of the box HA and VPN |
| Dell            | Reasonable prices, especially for HDD's, iDRAC works fairly well |
| Docker Hub      | Hosting of docker images                 |



## Monitoring

| Tech                                     | Use                                      | Reason                                   |
| ---------------------------------------- | ---------------------------------------- | ---------------------------------------- |
| Dripstat                                 | JVM and transaction monitoring           | Provides free monitoring for small JVM's and stepped levels for higher. |
| Plumbr                                   | JVM and transaction monitoring           | EOL, Root cause of 2 - 3 downtime events, inflexible pricing |
| Newrelic                                 | Server monitoring                        | EOL                                      |
| Pagerduty                                |                                          |                                          |
| Nodegrid                                 | Website monitoring                       |                                          |
| [health dashboard](https://github.com/egis/HealthDashboard) | Health tracking of servers, network devices and apps | Nagios and similar tools are complex and difficult to setup & maintain / SaaS tools are expensive when you get to many small endpoints to track |

