# Cultural Manifesto

>  Kevin Scott - The VP of engineering at LinkedIn/AdMob coined the term [cultural manifesto](http://firstround.com/review/how-i-structured-engineering-teams-at-linkedin-and-admob-for-success/)

## Agile

We try and implement modern agile principles - while we are far from a good example of a modern agile organization, it is something we aspire to be:

<a href="http://modernagile.org"><img src="http://modernagile.org/img/modernAgileWheel/modern_agile_wheel_english.svg" width="300"></a>

## How we make things

>  **Favour KISS("Keep it simple, stupid") above all else, complexity is hard to debug**

#### API Design


* API's (REST or Java based) should be stable and backwards compatible
* Eliminate boilerplate
* Methods and parameters should be self documenting
* Avoid checked exceptions
* Favour appending to the API and marking the old method as depreceated over updating/ replacing
* Enforce API encapsulation by importing only the `*-api.jar` where possible
* Use sane defaults, make configuration optional or encapsulated in a builder/ config object


#### Build vs Buy vs OpenSource

> Favour building over using batteries included frameworks and libraries

* **Build** when there are no alternatives or the alternatives are too expensive or complex.  

* **Open Source** libraries should be used when possible, just ensure that the project will have longevity i.e. backed by an organisation like Apache, Google or a 2+ man commercial operation.  

*  **Buy** when then the TCO is lower than building (including initial development and maintenance)

#### Design

- Include feature toggles so that broken features can be turned off, and behaviour can be changed based on a clients needs. Do not change the default feature setting until at least a major release.
- Backwards compatibility is critical in terms of behaviour, configs and data. Upgrades between releases 5y+ years old is not unheard of.
- Backend services should be stateless if at all possible, Never store session user state.
- While PaperTrail is deployed as a monolithic application it is composed of many modules and repositories. The primary reason is to reduce testing times. In addition each repository can have it's own lifecycle for languages and tooling 

#### Testing

- Design for testability and more importantly test speed and stability
- [Write tests. Not too many. Mostly integration](https://blog.kentcdodds.com/write-tests-not-too-many-mostly-integration-5e8c7fff591c)
- Practise TDD (Test driven development) at the feature or e2e level, not unit test level
- Don't create tests for the sake of it as tests require maintenance - tests should actually test something that could potentially break 


#### DevOps Toolchain

* Use a GitHub repo per project, module or client. You can use submodules or just clone repos to the same directory to simulate a Mono Repo

  *Without a dedicated SDET team,  testing times for a Mono Repo become too long*

* CircleCI is the primary CI system, AppVeyor is used for Windows and SQL Server tests

* Use a git [forking workflow](https://www.atlassian.com/git/tutorials/comparing-workflows#forking-workflow) with [pull requests](https://www.digitalocean.com/community/tutorials/how-to-create-a-pull-request-on-github) (PR), the team lead / project owner is the only one with write access to the main repo. 

  * Feature branches may be used locally, but should be removed before creating a PR
  * Create a tag per new GA release
  * Create a new branch when working on major new releases to be able to backport fixes to the stable release

* Use AngularJS style [commit messages](https://github.com/angular/angular.js/blob/master/CONTRIBUTING.md#commit)

* Lifecycle Stages:
See [Tech Stack](https://github.com/egis/handbook/blob/master/Tech-Stack.md)  
  * **New** - *Use cautiously and only for POCs or low risk items*
  * **OK** - *Can be used in place of standard by developer choice*
  * **Standard** *The default*
  * **Old**  *Continue use for current projects, but avoid for new projects / tasks*
  * **Migrate** *Migrate at the first possible opportunity avoid new features or improvements*
  
## How we operate things

* KISS, Avoid shared state and SANs
  * e.g. ESXi with local disk
* Backup to Amazon S3 and allow rapid automated restore to EC2 for testing 
  * **NB: Test at least once per quarter**
* Use 2 factor authentication and password databases (LastPass), favor SSH keys over passwords
* Favour automation e.g. ansible

## How we function as a team

* Daily cross functional standups for real time comms
* Jira for issue tracking, Google drive for doc collaboration
* Slack for semi-sync comms
* Email or face 2 face meetings for everything that doesn't fit above

### Team Structure

A flat communication structure, but a normal hierachical organizational structure with each manager having no more than 7 - 10 direct reports

* Prefer long time permanent staff over contractors - The value to the company increases with experience in the domain.
* Always have new hires conduct a real life technical test e.g. coding/ prepping a server/ writing a spec

### OKR

See [OKR - reWork](https://rework.withgoogle.com/guides/set-goals-with-okrs/steps/introduction/)  and [OKR - Betterworks](https://www.betterworks.com/okr/)  

OKR are similar to KPI's but they differ in a few ways:

* Negotiated individually for each team member
* Target 70% completion rate, too low and people become demotivated, too high and they are not being challenged
* Should align with team and company wide OKRs

### 1-1

> "You spend so much time finding great people, it’s worth it to help them grow to be the best they can be." 

See [What is a 1-1](https://wavelength.asana.com/workstyle-what-is-a-1-1/) 

* Mandatory regular scheduled meeting between for each employee and their manager
* Not for status updates, more about career growth, monitoring OKRs and **getting** feedback



### Roles and Titles

Roles and job titles are based on ability



| Capability                               | Junior | Dev  | Senior | Full Stack | Team Lead | Architect |
| ---------------------------------------- | ------ | ---- | ------ | ---------- | --------- | --------- |
| UI                                       | ✔      | ✔    | ✔      | ✔          | ✔         | ✔         |
| Backend fixes and improvements           | ◯      | ✔    | ✔      | ✔          | ✔         | ✔         |
| Backend Features                         | ◯      | ◯    | ✔      | ✔          | ✔         | ✔         |
| Business Analysis                        | ●      | ●    | ● ●    | ● ●       | ● ● ●     | ● ● ●    |
| Bootstrap a project with a build pipeline, tests, CI, etc. |        |      | ✔      | ✔          | ✔         | ✔         |
| Justify a tech stack                     |        |      | ✔      | ✔          | ✔         | ✔         |
| Evaluate tech stacks for a specific environment |        |      | ◯      | ◯          | ◯         | ✔         |
| Design a database schema                 |        |      | ◯      | ✔          | ◯         | ✔         |
| Deploy and support application into production |        |      |        | ✔          | ◯         | ✔         |
| Debug at the OS and Network level        |        |      |        | ✔          | ◯         | ✔         |
| Plan and manage the workload and/or act as scrum master |        |      |        |            | ✔         | ◯         |
| Mentor and Coach Developers              |        |      |        |            | ✔         | ✔         |
| Design and create developer tooling      |        |      |        |            |           | ✔         |
| Create a technology roadmap and strategy |        |      |        |            |           | ✔         |
  
✔ - Must have   
 ◯ - Nice to have  
 ● - Limited Experience  
 ●● - Practial Experience   
 ●●● - Advanced / Expert  
 
### Performance Management

* Performance is monitored by managers through day to day interaction, review of public comms and via KPIs/ OKRs

* Constructive critical feedback should be in private as soon as possible after the event

* Positive feeback should be in public

  #### Performance Improvement Plans (PIP)

* Should regular coaching not be sufficient to improve performance to required levels an employee will be placed on a PIP which will have specific objectives that need to be met in order to retain employment. PIPs run for 1 - 3 months depending on the scenario with weekly written feedback on progress towards the objectives.

* PIPs are not meant to be a mechanism for providing evidence of poor performance for dismissal, but rather a formalized mechanism to improve performance.

