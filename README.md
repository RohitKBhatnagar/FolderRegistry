# Registry for Top Level Folders

## Establishing New Team Folders

New team folders can be requested by following these simple steps:

- Clone this repository to your local repo
- Create a new YAML file for each folder name inside the userInputDir directory.
- The file should be name the same as the folder you wish to create. For an example to create a directory named Jenkins PIPE Project the name of the YAML should be jenkinspipeproject.yaml
- Fill in the details as per the guidelines below and then create a pull request.

Inside the `userInputDir` there is an example YAML file with example data that user needs to refer. Below is the content of that file:

```
- Name: Sample Example
  description: A team folder for the Sample Example project team.
  ESF: Enterprise Service Framework program name /service name
  Duplicate: True/False
  maintainers:
  - Maintainers email
  groups:
    SampleExampleAdmin:
      members:
      - cd_sample_ex_admin
      roles:
      - FolderAdmin
    SampleExampleUser:
      members:
      - cd_sample_ex_user
      roles:
      - Developer
    SampleExampleReadOnly:
      members:
      - cd_sample_ex_ro
      roles:
      - ReadOnly
    SampleExampleBuildOnly:
      members:
      - cd_sample_ex_bo
      roles:
      - BuildOnly
```
#### Folder Name

The name of the folder. In the example above, the folder name is 'Sample Example'.

#### ESF 

You must include the ESF field containing a valid Enterprise Service Framework Program and Service Name. you can find teams ESF value in https://sso.iapp.mastercard.int/apie/esf/.

#### Duplicate (Duplicate Folders)

Folders with similar names are allowed on different masters with approval from the Builder Tools team.
You can open a Work Order to Builder tools prod support team (https://fusion.mastercard.int/confluence/display/CD/How+to+open+a+Remedy+Work+Order+for+Builder+Tools).
This option of creating duplicate folder names is not available in the subfolder.

#### Maintainers email

Provide the generic email address of the project or the respective member who maintains the folder, 
one or more email addresses that can be used to contact the Folder maintaner(s).

#### Folder Groups

A group describes a population of users that have a certain set of permissions (which are defined
by a role). In the following example, a group named 'SampleExampleAdmin' is composed of members of
the 'cd_sample_ex_admin' LDAP group and has the permissions granted by the 'FolderAdmin' role.

```
SampleExampleAdmin:
    members:
    - cd_sample_ex_admin
    roles:
    - FolderAdmin
```

Minimally, at least one group must be defined that is assigned to the `FolderAdmin` role.

#### Group Members

Group members are expressed as a list of LDAP group names. Some guidelines:

- Groups of the format `cd_<team/proj name>_<access level>` are preferred, where access level is
  `admin`, `user`, or `ro` (read-only).
- Existing LDAP groups are allowed, but must not contain spaces and must belong to the 
  `MasterCard Groups` subtree.
- Use of existing groups may be phased out in favor of `cd_` oriented groups.

#### Group Role

Groups are granted privileges by association with a role. The typical roles are `FolderAdmin`,
`Developer`, and `ReadOnly`.

### Available Roles

#### `FolderAdmin`

A folder administrator. Can update the configuration of the folder and perform CRUD operations
on folder content (jobs, pipelines, credentials, subfolders). Additionally, has all the privileges
of the `Developer` role.

#### `Developer`

Can perform CRUD operations on jobs and pipelines within the folder, as well as trigger jobs to run.

#### `ReadOnly`

Can see folder contents and job configurations, but cannot modify anything or trigger jobs.

#### `BuildOnly`

Similar to `ReadOnly`, but can trigger jobs to run.

# Register Sub-Level Folders for `Cookbook Integration` & `Chef-Object Pipelines`

To create sub-level folders under cookbook integration and chef-object pipelines you can create a PR to their respective YAML files. The format will be same as the root level folder. 

```
|____subfolder
| |____CookbookIntegrationPipeline.yaml
| |____ChefObjectPipeline.yaml
```
