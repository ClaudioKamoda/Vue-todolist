# To-Do List

This project is dveloped using Vue.js, proposed by the web dev course I'm taking, **_FrontStart_** by @IsadoraStangarlin.

This is a introduction project to Vue.js, using the basic functionalities like conditional **_classes_**, **_computed_**, **_props_**, **_:for_**, **_v-on_** and **_watch_**.
The cool twists to this To-Do List is that it's data is saved on local storage, so every time you close and reopen the tasks you didn't complete yet will be there. Simulating a conection to a database.
I also worked with javascript dates for the first time by adding a **_dateCreated_** field on each task.

![To Do List in action](https://github.com/ClaudioKamoda/Vue-todolist/blob/main/src/assets/example.gif)

How to setup the prohect on your machine:

## Project setup

```
npm install
```

### Compiles and hot-reloads for development

```
npm run serve
```

### Compiles and minifies for production

```
npm run build
```

### Lints and fixes files

```
npm run lint
```

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).

## Project Log:

#### October 20, 2021:

-   Added new element to the list with **_v-on:keyup:enter_**.
-   Implemented access to the **_local storage_** to keep the data.
-   Added style to show a line through the completed item.

#### October 24, 2021:

-   Installed **_feather icons_**.
-   Added simple style to the project.
-   Added the option to delete an item.
-   Improved UX by marking an item by clicking on it's name.

#### October 25, 2021:

-   Created new component called **_ListItem.vue_**.
-   Refactored the code to contain the correct properties.
-   Adjusted the css of the **_ListItem_** component.

#### November 14, 2021:

-   Added date of creation as a property of each item.
-   Styled the text.
-   Corrected delete bug.
