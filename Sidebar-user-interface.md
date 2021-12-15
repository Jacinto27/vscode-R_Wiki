The sidebar contains a workspace viewer, help pages viewer, and live share
controller.

<img width="1791" alt="workspace" src="https://user-images.githubusercontent.com/4662568/122624265-f3164f80-d0d1-11eb-8801-9d5fe2ce930f.png">

## Workspace viewer

The workspace viewer displays the information of the objects in the global
environment of the attached R session.

Objects could be viewed (sending `View(obj)` to the terminal) or removed
(sending `rm(...)` to the terminal).

The following option could be used to show to the second level of nested
structures so that the list elements or data frame columns could be shown in the
workspace viewer.

```r
options(vsc.str.max.level = 2)
```

<img width="314" alt="workspace viewer" src="https://user-images.githubusercontent.com/4662568/122624302-2b1d9280-d0d2-11eb-9d7b-9e7291748d84.png">

## Help pages viewer

The help pages viewer lists several options to work with help pages, topics, and
packages.

<img width="316" alt="help pages viewer" src="https://user-images.githubusercontent.com/4662568/122624322-3f618f80-d0d2-11eb-9113-b524af861039.png">

## Package management

In the help pages viewer, one can also install and remove packages. In the
viewer, pressing any key will trigger the search mode so that one can easily
find a package by name.

<img width="604" alt="install package" src="https://user-images.githubusercontent.com/4662568/122624375-746de200-d0d2-11eb-9d95-d30e76bccea9.png">
