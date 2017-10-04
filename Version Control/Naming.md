# Naming Conventions
When creating repositories it's important to keep the names informative and with a structure similar between projects. This hopefully helps to navigate among a growing base of repositories.


## Naming Repositories
The names should be a coupled maximization of name length and information. The base structure should be composed of up to 3 words:

```
[client]-[specific_project]-[extension_key]
```

* `[client]` – Your client's acronym or abbreviation.
* `[specific_project]` – The name (preferably and acronym or abbreviation as well) for the project in question.
* `[extension_key]` – Extra information that allows for severals repositories to share the same base name when there a greater modularity. Bellow is a list of some keywords and their significance:
  * `frontend` – This is the repository that contains the front end code.
  * `api` – This contains an API or API related code.


## Naming Pull Requests
All Pull Request should state if it is a *fix* or a new *feature*, followed by information.

```
fix/what_it_fixes

feature/what_it_does
```

### Special Tags
#### [WIP]
Tag pull request titles with [WIP] to indicate a "Work In Progress" state.
```
[WIP] Send weekly reports)
```
#### [CLIENT]
Tag pull request titles with [CLIENT] to indicate an already approved state but pending for a "GO" to production.
```
[CLIENT] Send weekly reports)
```
