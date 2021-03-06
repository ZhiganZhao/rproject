rproject
========

This is a simple package for project management in R. The folder structure looks like
* Root folder
 * project.ini
 * Project1
    * config.ini
    * Rcode
    * Resources
    * Results
 * Project2
    * config.ini
    * Rcode
    * Resources
    * Results

In the project.ini, all project will be listed
```
p1 = Project1
p2 = Project2
```

Each project has a prefix (short name), e.g. p1 for Project1 and p2 for Project2. All common functions for each project are stored in to Rcode subfolder named as prefix+Functions (e.g. p1Functions.R for Project1 and p2Functions.R for Project2).


-----
To install:

the latest development version: 

```{r}
library(devtools)
install_github("byzheng/rproject")
```

-----
How to use

* Source functions in the project. Using  ```project_fun``` to source functions in a project. You can write R codes and functions in the files, but ```project_fun``` will skip all R codes.
```{r}
# Only p1Functions.R
project_fun()
# All functions in the Rcode folder
project_fun(all = TRUE)
# Functions from another project if you are working in Project 1
project_fun(project = 'p2')
```

* Generate file path in project. You can run R codes from any subfolders in a project. ```project_filepath``` will generate the correct file path.
```{r}
# File in current project
project_filepath('Resources/tmp.csv')
# File in another project
project_filepath('Resources/tmp.csv', project = 'p2')
```
