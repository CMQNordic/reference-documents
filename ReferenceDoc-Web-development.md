<h1 id="web-development">Reference Guide - Web Development </h1>

This is a reference document with usefull information about web development in general. Written by myself, for myslef, while learning for educational purposes and for fun. <br> <br>

<p align=right>Written by Martin Czerwinski ®CMQ Nordic AB</p>

---

<h1 id="table-of-content" >TABLE OF CONTENT</h1>

-  [**VSCode**](#visual-studio-code)
[Whats's built-in](#what-is-vscode) ◦ [Extensions](#useful-extensions-in-vscode) ◦ [Shortcuts](#useful-shortcuts-in-vscode) ◦ [Snippets](#snippets-in-vscode) ◦ [Terminal](#terminal-in-vscode) ◦ [Intellisense](#intellisense-in-vscode) ◦ [Settings and Code formatting](#settings-and-formatting)
- [**Web applications**](#diffrent-application-types)
[Diffrent application types](#diffrent-application-types)  ◦ [Typical project structure](#typical-project-structure)
- [**Node**](#node-and-npm)
[Node/Nodemon/Npm/Npx](#node-and-npm) ◦ [Node vs Browser vs Modules](#node-browser-modules) ◦ [Npm packages & versioning](#npm-packages)  
- [**Webpack**](#what-is-webpack)
[What is Webpack?](#what-is-webpack) ◦ [Webpack Dev Server](#webpack-dev-server-m) ◦ [PostCSS](#what-is-postcss) ◦ [Build for production](#build-for-production) ◦ [_webpack.config.js_](#webbpack-config-js)   
- [**Vite**](#vite)  
- **[Fonts & Icons](#frontend-ui)**   
[Postcss](#postcss-in-webdev) ◦ [Bootstrap](#vue-and-bootstrap) ◦ [Mdb](#vue-and-mdb)
- [**Documenting your code (JSdoc)**](#documenting-code)   
-   [**Good to know**](#seo-and-responsivness)    
    [Search Engine optimization](#seo-and-responsivness) ◦ [Screen sizes](#screen-resolutions) ◦ [Responsiveness](#responsivness-m)
-   [**Other frameworks and tools**](#other-frameworks)  
    [Markdown](#markdown-syntax) ◦ [Netlify](#what-is-netlify) ◦ [EMMET snippets](#emmet-snippets) - move to css,html and js guide 
-   [**Error handling**](#error-handling)   
-   [**Geo locations:**](#geo-locations) [Autocomplete](#geo-locations)   
-   [**Python**](#python) ◦ [Virtual environments](#virtual-environments)  ◦ [pip](#pip) ◦ [connect to database](#connect-to-database) 

Some really good must-read articles:  
[Refactor, structure and test your code](https://www.testim.io/blog/javascript-refactoring-5-plays-to-improve-code-quality/) <br>


<br><div id="visual-studio-code" />

## [**Visual Studio Code (VSCode)**](#)

---

Visual Studio Code ([VSCode](https://code.visualstudio.com/)) is a popular, lightweight and free code editor.  

Terminal commands:
`code` - starts from command without any project open  
`code .` - start from command with folder that command is run in

<div id="what-is-vscode" />

### **[What's built-in?](#)**

VSCode comes with various  build-in features. some of those are:
-   **JavaScript suppport:** JS runs natively in browsers and NodeJS.
-   **TypeScript support**: TS adds strict typing syntax/rules to JavaScript.
-   **Node.js & Npm**: Runtime environment for JavaScript outside a browser with default access to package manager (npm).
-   **IntelliSense**: Editing aid to code faster in form of suggestions, code completion and quick lookups. 
-   **Emmet**: Predefined short text snippets proposed by intellisense that auto-generate larger pieces of HTML, CSS or other code.
-   **Extensions:** Integrated marketplace for extensions that expand functionality of VSCode.
-   **GIT:** Integrated support for Git with handy graphical interface for most common functions.
-   **Multi-Cursor editing:** Allows you to edit multiple parts of same documents at once.
-   **Debugging, Code navigation**: Possible to debug your code easily.

<p align="right"><a id="useful-extensions-in-vscode" href="#table-of-content">↩ Back To Top</a></p>

### **[Extensions](#)**

Many extensions are getting integrated into VSCode with each release. Yor can download extensions from [marketplace](https://marketplace.visualstudio.com/). Here are examples of some usefull ones:
- ✅ `Prettier` - Opinionated code formatter
- ✅ `ESLint` - Analyze code, find & fix problems. [Config](https://medium.com/@gogl.alex/how-to-properly-set-up-eslint-with-prettier-for-vue-or-nuxt-in-vscode-e42532099a9c). [Rules](https://eslint.org/docs/rules/).
- ✅ `Code Spell Checker` - Spelling
- ✅ `Live Server` -  Fast local dev server.
- ✅ `HTML CSS Support`/`Intellisense for CSS class names in HTML` - intellisense in .html for defined/linked css classes.
- ✅ `Vue Language Features (Volar)`/ `TypeScript Vue Plugin (Volar)`
- 👍`Vue VSCode Snippets`
- ✅ `Easy Snippet` - Add/edit snippets easily
- 👍 `Todo Tree` - Shows all TODOs in the code
- 👍 `Tagnite` - smart intelissense suggestions based on IA
- 👍`CSS Peak` - Adds go-to-definition for css classes
- `Node.js Modules Intellisense` - intellisense with names of modules in import statements
- `Path Intellisense` - propose filenames in intellisense after `./`
- 👍`DotEnv` - code formatter for .env files.
- `Auto import` - import actions in intellisense
- `Bookmarks` - Fast navigation between bookmarks
- `MatchIt` - Navigates between focused, matching brackets or tags.
- `Auto Rename Tag` - Renames matching html tags automatically.
- `Auto Close Tag` - Closes matching html tags automatically.
- `PostCSS Intellisense and Highlighting`/`PostCSS Language Support`/`language-postcss` - for postcss syntax highlighting
- `Graph`/`GIT Lens`/ - git GUI
- `Gitignore` - add gitingore files for diffrent projects.
- `History` - nice git history diagrams
- `Markdown Shortcuts`/ `Markdown All in One`/`Markdown Preview Enhanced`


<p align="right"><a id="useful-shortcuts-in-vscode" href="#table-of-content">↩ Back To Top</a></p>

### **[Usefull shortcuts](#)**

Add from GUI from `settings / keyboard shortcuts`. Changes are in background written to a file named `keybinding.json`. Open from command palette: `ctrl+alt+p`-> `Keyboard Shortcuts (JSON)`.



| GENERAL&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |  | 
| :-- | :-- |
| `alt space x / n` | **Maximize / Minimize window** | 
| `ctrl alt space` | **Focus editor** |
| `windows .` | **Add icons**  |
| `ctrl shif (alp) p`  | **Command palette** <br>Cclose with `ctrl shif p` | `ctrl alt p`. |
| `ctrl  p` | **Quick search** <br>Quick way to open a file. Close with `ctrl alt p`. |
| `ctrl f` | **Search/Replace** <br> Search selected word in current document. To expand to replace wizard press `Ctrl H`. Close with `ctrl f`. |
| `ctrl w` | **Close file/tab** <br> Close currently focused tab or file. |
| `ctrl j` | **Terminal - open/hide/focus/resize/scroll** <br> Open/Hide/Focus `Ctrl J` (seperate window `Ctrl+Shift+C`), kill `Ctrl K` and clear `Ctrl L`. Use `Ctrl ▲▼` to resize terminal and `Ctrl Alt ▲▼` to scroll.|
| `ctrl shift j` | **Console - open/hide/focus** <br> Open/Hide browser chrome console .|
| `ctrl e` | **File Explorer - open/focus/toggle** <br> Open/focus/hide sidebar explorer window. When in focus use `▲▼` to navigate files and folders. Press `Enter` to open selected file. <br> `Ctrl f` to create a new file. <br> `Ctrl alt f` to create a new folder. <br> Press `◄ ►` to unfold/collapse folders. |
| `ctrl tab`<br>`cltr 1-2-3..` | **Files - toggle** <br> Toggle opened files  |

| CURSOR & SELECTION&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |  |
| :-- | :-- |
|`alt ◄ / ►` <br> `alt k / l` | **Cursor jump - line start/end**|
|  `ctrl alt enter` <br> `ctrl / alt enter` | **Cursor jump - file start / end** |
| `ctrl ◄ ► ▲▼` | **Cursor jump - words/rows** <br> Moves cursor whole words (`◄ ►`) or jumps rows (`▲▼`) |
| `Ctrl Å` | **Cursor jump - matching brackets** <br> Moves focused cursor a block to matching brackets. Extension `Matchit` is needed to support html-tags in vue files. |
| `Ctrl B` | **Cursor jump - bookmarks** <br> Move cursor to next bookmark (toggle a bookmark `ctrl b`). Extension `Bookmarks` is required |
| `ctrl alt ◄ ►` <br> `Shift Alt ◄ ►` <br> `Ctrl D` | **Select - parts or characters** <br> Parts with `ctrl alt ◄ ►` or `ctrl b` <br> Single chars with `shift alt ◄ ►` |
| `ctrl alt ▲` | **Expand selection** <br> If selection exists -expand it to matching section. |
| `ctrl d` <br> `ctrl shift d` | **Select words** <br> Select word with `ctrl d` (continuos presses select same selections downwards) <br> `ctrl shift d` adds cursor on same place to all same parts downwards (if selection exist)|
| `alt ► ◄` | **Select  line** <br> Select line with `alt ► ◄` <br> Delete line with `ctrl alt backspace` |
| `ctrl å` <br> `ctrl alt å` | **Jump / select - matching brackets** <br> _*unsure if it qorks for all file types_ |
| `Alt <click>` | **Multi cursor**   <br> Adds extra cursor for every mouse click. Use `Shift Esc` to exit. |
| `alt ▲▼` | **Move selection - up / down** <br> Move whole selected section up or down. |
| `alt shift ▲▼` | **Copy section - up / down** <br> Copy whole selected section up or down. |

<br>

| CODING&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |  |
| :-- | :-- |
| `Ctrl space` | **Show intellisense and navigate** <br> Force shows intellisense proposals. Navigating: `ctrl+space` or `shift+space` to scroll down. `ctrl+alt+space` scroll up. Select with: `tab` or `enter`. |
| `Ctrl .` | **Show spelling proposals** <br> Shows list with proposals for spelling misstakes. Extension Code Spell checker is needed. |
| `Ctrl *` | **Comment toggle** <br> Toggle the comment.  `Ctrl alt *` for whole block. |
| `Ctrl S` | **Format on save**<br> Auto-formats file when saving. <br> Enable in settings.json for `Editor: Format On Save` and `Editor: Format On Paste` |
| `Ctrl P :[nbr]` | **Go to line** <br>Go to line number in current file. When in focus hide wizard with `ctrl p`*. |
| `F12` | **Go to definition** <br> Extension for scanning folder must be installed |
| `ctrl alt backspace` <br> `ctrl backspace` | **Delete current line / word**  |
| `Ctrl Alt L` | **Wrap selection in console.log()** <br> Wraps selction in js/ts file in console.log(). |
| `Ctrl Alt T` | **Wrap selection in try/catch** <br> Wraps selection in js/ts file in try/catch. |
| `Ctrl Alt D` | **Wrap selection in `<div>`** <br> Wraps selection in js file in try/catch. |
| `Ctrl Alt I` | **Wrap selection in any html tag** <br> Wraps selection in html file in new html tag. |
| `Shift '' `  | **Wrap as string or add** <br> Wraps selection in string characters `` or adds ``|
| `Tab` or `Shift+Tab` | **Indent Row Left/Right** <br> Intends right/left whole line. |
| _optional_ | **Auto rename tags** <br>Set in settings.json: `editor.linkedEditing": true`. To work for all kind of files (ie vue) extension `Auto Rename Tag` might be needed. For vue files it works out-of-the-box with extension `Volar`. |
| _optional_ | **Auto close tags** <br>Set in settings.json: `html.autoClosingTags: true`. To work for all kind of files (ie vue) extension `Auto Close Tag` might be needed. For vue files it works out-of-the-box with extension `Volar`. |

<br>

Commands are executed in special conditional context defined by a `when` statement. 
List of conditional operators -> [here](https://code.visualstudio.com/api/references/when-clause-contexts). Available commands can be found [here](https://code.visualstudio.com/api/references/commands).
Default VSCode keyboard shortcuts [for windows in general](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf)
Read more about shortcuts at [microsoft.com](https://code.visualstudio.com/docs/getstarted/keybindings).

For example if we want to run a special shortcut command any when editor has focus (cursor is blinking) then we define when as "when: editorTextFocus". Or if we want to run it for special command only for a special language i.e. html then we set when to "resourceLangId == html".

<p align="right"><a id="snippets-in-vscode" href="#table-of-content">↩ Back To Top</a></p>

### **[Snippets](#)**

To see a **list of all snippets** for a file extension (given language) open Commad Palette `Snippets: Insert Snippet` to view list of own defined snippets,default VsCode snippets and sippets added extensions. From this list it is easy to **disable** them from being shown in intellisense.

You can **create own snippet**s. They can be global applied in all workspaces, or localy just for current workspace. Create VSCode snippets from Command Palette - `Snippets: Configure User Snippets` and choose `new global snippets...` or `new snipper for ...`.

Read more about snippets [here](https://code.visualstudio.com/docs/editor/userdefinedsnippets#_creating-your-own-snippets).

Snippets created with VSCode get extension `.code-snippets`. Extension "Easy Snippet" save the file with extension `.json` and use its filename as language they apply for.

```javascript
// Global snippets are saved here
C:\Users\<user>\AppData\Roaming\Code\User\snippets
```

<p align="right"><a id="terminal-in-vscode" href="#table-of-content">↩ Back To Top</a></p>

### **[Terminal](#)**

VSCode comes with an integrated terminal window. By default it starts with working directory that is **the root** of your opened workspace. 

> Note, you can open **an external terminal window** with command `Ctrl + Shift + C`.  

You can open several terminals at once and to right is a tabbed list of them. Remove terminal instances by pressing the Trash Can button. You can split the terminal to see 2 at once. You can also navigate to diffrent working directories by drag and dropping folders onto command `cd`.

 It is also possible to switch between _shells_ that power the terminal. It is done from a drop down in the right upper corner of the terminal window (select profile). It can also be done by opening `Command Palette -> Terminal:Select Default Shell`. There you will get a list of available choices for you operating system where `Git Bash` (the default shell that we use) is one of the options.
 
 [Read more](https://code.visualstudio.com/docs/terminal/basics#:~:text=To%20open%20the%20terminal%3A,the%20View%3A%20Toggle%20Terminal%20command.) about the terminal.

<p align="right"><a id="intellisense-in-vscode" href="#table-of-content">↩ Back To Top</a></p>

### **[Intelisense]()**

Intellisense provides suggestions as you type for javascript, typescript, json, html, css, scss and less out of the box. Pressing Tab or Enter will insert the selected member. 

Launch intelisense with `Ctrl + space`

Read how to [customize intellisense](https://code.visualstudio.com/docs/editor/intellisense#_customizing-intellisense) or read more [here](https://code.visualstudio.com/docs/editor/intellisense).


<p align="right"><a id="settings-and-formatting" href="#table-of-content">↩ Back To Top</a></p>

### **[Settings and Code Formatting]()**

For more heavy projects or personal preferences often some customization is needed. Customizing and getting all extensions, setting, formatters, linters to work together can be a time consuming task. 

### **Settings**  
VSCode settings visually in a GUI can be viewed and changed from `File > Preferences > Settings`. 

Settings are saved in 3 types of setting files and you can open those files by searching in command palette for them:

**User Settings (JSON)**
Personal settings added for each change to user specific file `..user/settings.json`. This file is possible to edit and its contend overwrites _defaultSettings.json_.

**Default Settings (JSON)** 
Global default settings as shipped with VSCode in a read only file named _defaultSettings.json_. Each installed extensions default settings are automatically added here to. This file is really good to look into and chech what the defalt setting was after making some changes.

**Workspace Settings (JSON)** 
Settings saved in `root/.vscode/settings.json` that are valid only in given workspace. This file is possible to edit and its contend overwrites _user/settings.json_ and _defaultSettings.json_.

The same apply to **Keyboard Shortcuts**. File **keybindings.json** can edited and modified though UI. The default shortcut definitions can be found in file `Default Keyboard Shortcuts(JSON)` from command palette (ctrl+shift+p).

### **Formatting**  
For HTML and JavaScript there are default formatters shipped with VSCode but at writing moment CSS do not have any formatter. An extension must be installed to format CSS.Same applies for Vue. There are popular extensions like **Prettier** (supporting formatting of pretty much all languages, including CSS) and **Volar** for Vue. Those extensions overwrite native VScode formatting by adding formatting with syntax highlighting and styles on their own. Note that prettier have their own opinionated configuration that can not be changed but there are some settings like line length, semicollon in ens of line or usage of double/single quotes.

By default shortcuts like `Ctrl+K Ctrl+F` formats only the selection and `Ctrl+Alt+F` whole document, but **by enabling** `Editor: Format on save` in VSCode settings the formater will be run for each save. Recommended to set it.

**Wrap HTML attributes?**  
In _Settings_ search for `HTML> Format: Wrap Attributes` and `HTML> Format: Wrap Line Length`. `Auto` is default and can be changed if you prefer different styles of how HTML attributes shall be wrapped. Our favorite is "preserve-aligned" that reserves user wraps but if line too long aligns everything.


<p align="right"><a id="diffrent-application-types" href="#table-of-content">↩ Back To Top</a></p>

## **[Web applications](#)**
---

### [**Different application types**](#)

**Web Applications** are web sites (accessible via a URL) built for the browser using web technologies such as HTML, JS, CSS and backend. 

**Progressive Web Apps** expands web applications to be “installed” onto a device directly from the browser. This includes mobile, tablets, and even your computer’s desktop. It then runs in a headless browser so it looks 100% like an app and even works in offline mode.   

**Native Apps** are apps that are built and compiled for a specific operating system, whether it is Android or iOS.   

**Hybrid Apps** are web apps that have been written using web technologies such as HTML, JS, and CSS and have been compiled into a native shell and can installed and downloaded natively like a native apps.   

<p align="right"><a id="typical-project-structure" href="#table-of-content">↩ Back To Top</a></p>

### [**Typical project structure**](#)
Structure of the projects vary depending on type of project. For example Nuxt have its own opinionated folder structure with predefined folder names. See Nuxt specific document.

Scruffolding a Vue project usually generates predefined structure of folders.

It is also  very common that tools for building and auto-generating source code are used. Tools like for building whole projects like Webpack, Vite or tools for building CSS only like TODO or tools for building javascript only like TODO.  

But there are some general structure that might look like following

```
/root
├── / dist
├── / public 
│    ├── favicon.ico
│    ├── index.html (main entry point, links to styles.css & main.js)
│    ├── styles.js  (usually autogenerated from /src/assets/styles/styles.css)
│    └── main.js    (usually autogenerated from /src/main.js) 
│
├── /src
│   ├── / assets
│   │    ├── / images 
│   │    ├── / styles
│   │    │     ├── / global
│   │    │     │    ├── _global-styles.css
│   │    │     │    ├── _colors.css
│   │    │     │    ├── _variables.css
│   │    │     │    └── ...
│   │    │     ├── / modules
│   │    │     │    ├── _base-button.css
│   │    │     │    └── ...
│   │    │     └──────────────────────── styles.css    (all application style, usually auto-generated)
│   │    │
│   │    └──── / scripts 
│   │           ├── / components
│   │           │    ├──  header.js
│   │           │    └── ...
│   │           └──────────────────────── main.js       (all scripts here, usually auto-generated)     
│   │
│   ├── / node_nodules     (auto-generated by "npm install")
│   ├── / router
│   ├── / store 
│   ├── / mixins
│   ├── / components 
│   ├── / pages            (entry points/views for routes)
│   └── app.js / main.js   (often entry point for apps build builders)
│
├── .gitignore
├──  package.json / package-lock.json
├──  webpack.config.js / vite.config.js / vue.config.js / nuxt.config.ts    (project dependent configuration)
├──  eslintrc.js     (configuration for ES Lint, can be defined in package.json)
├──  babel.config.js    (configuration for Balel that is used by webpack, can be defined in package.json)
└── ...
```

**dist** - Usually files that can be deployed to server are autogenerated and placed in this folder. Then a builder like Vite or Webpack do its magic and produces files that can be deployed. Note! Folders and files from `public` are normall just copied as they are. In case no project builder used then public is same as dist.

**public** - Files and folder placed here shall simply be copied in production build to dist folders as they are. Not go through webpack or any other builder. You must reference them in your code using absolute paths.

**src** - here we place are the source files that we modify manually to build up our project

**src/assets** — Folder where you put any assets like images, styles or scripts  that you link to in your. Fileshere are most often transfformed by building tools. Often files here are imported into the project.

TODO write more about project structure

<p align="right"><a id="node-and-npm" href="#table-of-content">↩ Back To Top</a></p>

## [**Node**](#) 
### **[Node.js & Nodemon & Npm & Npx](#)**

NodeJS is lightweight runtime environment for JavaScript. When installing node you also get **npm** client that you can use to download and manage packages. By default NodeJs do not understand typescript, only javascript.

**Execute .js file with node:**
```javascript
> node javascript.js
```

### Nodemon
The node command has to be re-executed each time we want to run a js file. To restart the file execution automatically use the [**nodemon**](https://nodemon.io/). You can install it globally with `npm i -g nodemon` but can also install nodemon as a development dependency:
 
**Execute .js file with nodemon**
```javascript
> nodemon javascript.js

// Now each change triggeer an execution. To abort listening to channges press Ctrl-C.
```

### Npm 
Npm is a package manager included in Node and makes is possible to download and store packages. Npm packages perform various tasks i.e. automate things or run server programs.  For example [**lodash**](https://lodash.com/) or [**normalize**](http://nicolasgallagher.com/about-normalize-css/) are packages used in web projects that contain functions that are used by code in our project. Those type of packages are so called **development dependant**. Packages that are not development dependant are those that just run and perform some task but do not contain functions accessed by our written code. Example are webpack, vite or various frameworks.

### Npx 
Npx comes with the npm. It is an npm package runner that can execute any package from the npm registry **without** installing the package locally. You can use npx in same way as npm commands but it might be a bit slower as it runs from the cloud.

**Package.json** 
This is the main file for our project where a list (name and version) of all downloaded nmp packages that our project use. The packages themself are stored in auto-created folder `node_modules` in project root. This folder is normally excluded in git becouse it can easially be recreated with all its content by running command `npm install`. In this file are also defined some script that can be run.
  
**Usefull npm commands**
```java
> npm init -y // creates new package.json file in new (empty) project

// list installed versions as defined in package.json 
> npm list 
> npm list -all // list all depth dependencies
> npm list -all --depth=1 // list packages installed by wrappers i.e nuxt includes vue
> npm list vue  // list all packages with vue in its name

// list installed global node js packages
> npm list -g

// install a package with dependencies, same as with --save
> npm install [package_name]
> npm i [package_name] 

// install a package with dev-dependencies
> npm install [package_name] --save-dev
> npm i [package_name] -D

// Installs latest official only for not yet installed modules as defined in package.json
// Does NOT update already installed modules to latest. Creates node_modules if needed.
// If a module removed from package.json then this will remove it from npde_modules to.
> npm install
> npm i

// Installs latest official for not yet installed modules as defined in package.json
// UPDATES already installed modules to latests. Creates node_modules if needed.
// If a module removed from package.json then this will remove it from npde_modules to.
> npm update  
> npm update -g

// this option to be added to save exact the version we download (x.y.z)
// Otherwise ^x.y.z will be saves and later
--save-exact

// list current, wanted and latest official version of 
> npm outdated  
> npm outdated -g

// uninstall a (global) package 
> npm uninstall [package-name]  
> npm uninstall -g [package-name])

// check status of all dependencies in the project
> npm audit
``` 


Extensive Node.js tutorial can be found [here](https://www.tutorialspoint.com/nodejs/nodejs_introduction.htm)  
Typescript tutorial can be found [here](https://medium.com/javascript-in-plain-english/typescript-with-node-and-express-js-why-when-and-how-eb6bc73edd5d).  
List of modules/packages that are by default build-in in node can be found [here](https://www.w3schools.com/nodejs/ref_modules.asp).

<p align="right"><a id="node-browser-modules" href="#table-of-content">↩ Back To Top</a></p>

## [**Node vs Browser vs Modules**](#)

Javascript can be run in Browser or in NodeJs enviroment. Code written for each of those differ and the code execution in NodeJs might generate errors in browser, and vice versa.

In order to run **import** statements (ES Modules) in NodeJs then file must be saved .mjs or row "type":"module" must be added in package.json when executing the file with node command.

To make http get request the browser have build Web API called **fetch**. But fetch do only work in browser, not in NodeJs. Npm package Axios is a similar package that work in same way both in browser as in NodeJs.

[Read more @mozilla](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules)
[Good explanation @youtube](https://www.youtube.com/watch?v=mK54Cn4ceac)

```javascript
// When in browser following line in <head> loads Axios from cdn
// <script src="https://unpkg.com/axios/dist/axios.min.js"></script>

if (typeof axios === 'undefined') {
   // Only on NodeJs
   axios = require('axios');
}
const apiUrl = 'https://dog.ceo/api/breeds/image/random';

// This runs both in browser and NodeJs
(async function () {
   try {
      const response = await axios.get(apiUrl);
      const data = response.data;
      console.log('Fetched with Axios: ', data.message);
   } catch (err) {
      console.log(`Axios http get failed. ${err.message}`);
   }
})();

// This runs only in browser (no axios needed)
(async function () {
   try {
      const response = await fetch(apiUrl);
      const data = await response.json();
      console.log('Fetched with Fetch:', data.message);
   } catch (err) {
      console.log(`Fetch http get failed. ${err.message}`);
   }
})();
```

``` js
// Run only in node
const fs = require('fs');

// Run only in node but...
// Files with an .mjs extension
// Files with a .js extension when the nearest (parent) package.json file
// contains a top-level value: "type": "module".
import fs from 'fs'
```

<p align="right"><a id="npm-packages" href="#table-of-content">↩ Back To Top</a></p>

### [**Npm packages & versioning**](#)

By default npm installs packages using `^`. You can switch this behavior by using `--save-exact`.

# **major.minor.patch**

Caret (**^**) — gives you the highest minor version & highest patch version.
Lamda (**~**) — gives you only the highest highest patch version.

```java
"vuetify": "^4.5.0", // Update 2 last digits
"vuetify": "~4.5.0", // Update 1 last digit
"vuetify": "4.5.0",  // npm install with option --save-exact. Will not update.
```
If you’ve got a lockfile, before npm installs your dependencies, it checks the versions on the lockfile and installs them. So, in the case above, if the new developer has the same lockfile as the first developer, then he’d have the same version. Which leads me to my next point — the lockfile should be pushed to git if you want to conserve consistency between all the teammates working on the same project.

In order to update your dependencies to their max version (according to the range specified), you’ll need to run a command called **npm update**. ”. This will also update the lockfile with the new installed version.

Read more [here](https://medium.com/att-israel/npm-versions-explained-60e4d6b9920f)

Some usefull npm packages that we frequently use.   

**Utilities**  
-  [normalize.css](https://ageek.dev/normalize-css) -  CSS reset library to deal with styling inconsistencies across browsers as it resets all browsers to same state.   
-  [lodash](https://lodash.com/) - Helper functions to work with arrays, numbers, objects, strings. Each funcion can be imported seperately i.e. `require('lodash/throttle'`) or `require('lodash/merge')`  
-  [sweetalert2](https://www.npmjs.com/package/sweetalert2) - Replacement for JavaScript's popup boxes with zero dependencies.  
```
npm i normalize.css && lodash && && sweetalert2
```

**Webpack**  
-  [webpack](https://www.npmjs.com/package/webpack) - For bundling & automated build of projects.  
-  [webpack-cli](https://www.npmjs.com/package/webpack-cli) - Webpack dependency needed for running command line scripts (in package.json file)  
-  [webpack-dev-server](https://www.npmjs.com/package/webpack-dev-server) - development server than can auto-injects js/css into chrome at runtime.  
```
npm i -D webpack && webpack-cli && webpack-dev-server 
```

**Vue (stand alone with webpack.config.json)**  
-  [vue](https://www.npmjs.com/package/vue) - Vue instance ann vue framework.  
-  [core-js](https://www.npmjs.com/package/core-js) - Latest ECMAScript: promises, collectionstyped arrays. Many UI frameworks are dependant on it.  
-  [css-loader](https://www.npmjs.com/package/css-loader) - For importing css to js files.  
-  [style-loader](https://www.npmjs.com/package/style-loader) - To inject javascript into browser and insert css in js in development mode.  
-  [vue-loader](https://www.npmjs.com/package/vue-loader) - For support of `<template>`, `<script>` and `<style>`. For Vue3 use vue-loader v16+.  
-  [@vue/compiler-sfc](https://www.npmjs.com/package/@vue/compiler-sfc) -  Compiles Vue Single File Components (SFCs) into JavaScript. Is strictly dependant to Vue 3 versions and shall always match Vue. Replaces `vue-template-compiler` in Vue2.  
-  [vuex](#) - Store functionality ([pinia](https://pinia.vuejs.org/) is an new lightweight alternative).    
-  [vue-router](#) - Routing functionality.  
-  [axios](#) -  Library for http communication & making http requests (instead for built-in [fetch api](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch)).  
```
npm i vue && core-js
npm i -D css-loader && style-loader && vue-loader & @vue/compiler-sfc
npm i -D vuex && vue-router && axios
```

**Vue (scraffold project)**  
-  [vue cli](https://www.npmjs.com/package/@vue/cli) - Autogenerates preconfigured vue projects with webpack (through `vue ui` or `vue create <project-name>`).  
Hides `webpack.config.json` but can be configured through `vue.config.js` - [read more here](https://cli.vuejs.org/config/). Installed globally.
```
npm install -g @vue/cli 
```   

**PostCSS with plugins**  
-  [postcss](https://www.npmjs.com/package/postcss) - A tool for transforming css styles
-  [postcss-loader](https://www.npmjs.com/package/postcss-loader) - Loader for various postCSS plugins
-  [autoprefixer](https://www.npmjs.com/package/autoprefixer) - Plugin. Adds special browser dependent CSS prefixes when needed  
-  [postcss-import](https://www.npmjs.com/package/postcss-import) - Plugin. replaces @import in CSS into referred code.  
-  [postcss-simple-vars](https://www.npmjs.com/package/postcss-simple-vars) - Plugin. for variables in CSS  
-  [postcss-nested](https://www.npmjs.com/package/postcss-nested) -  Plugin. for nesting in CSS  
-  [postcss-mixins](https://www.npmjs.com/package/postcss-mixins) -  Plugin. for defining function"macros" in CSS  

Read here how to configure for 

```
npm i -D postcss-loader postcss
npm i -D postcss-import postcss-simple-vars postcss-nested postcss-mixins autoprefixer
```

**Webpack production build**  
-  [clean-webpack-plugin](https://www.npmjs.com/package/clean-webpack-plugin) - Removes all files inside webpack's output `dist` directory when building for production.    
-  [css-minimizer-webpack-plugin](https://www.npmjs.com/package/css-minimizer-webpack-plugin) - Optimizes and minify CSS files in the project when building for production.  
-  [mini-css-extract-plugin](https://www.npmjs.com/package/mini-css-extract-plugin) - Bundles project CSS files into separate file(s) in `dist` when building for production.  
-  [html-webpack-plugin](https://www.npmjs.com/package/html-webpack-plugin) - Creates and extracts html from our project into `dist`.  
-  [fs-extra](https://www.npmjs.com/package/fs-extra) - Adds file system methods that aren't included in node native fs module.  
```
npm i -D clean-webpack-plugin && css-minimizer-webpack-plugin && mini-css-extract-plugin && html-webpack-plugin && fs-extra
```

**UI kit mdb/bootstrap**  
[mdb-ui-kit](#) - UI framwork based on bootstrap.  
[@popperjs/core](#) - Dependency in mdb needed for some elements like dropdowns to work.  
[@fortawesome/fontawesome-free](#) - Free icons for mdb. In documented exaples some few icons are used (i.e. toggler) but those are provided in css.  
[sass](#) - sass support.  
[sass-loader](#) - For transforming customized mdb scss to css when changing theme/colors
```
npm i -D mdb-ui-kit && @popperjs/core && @fortawesome/fontawesome-free
npm i -D sass && sass-loader
```

**prettier & eslint**  
-  [eslint-config-prettier](https://www.npmjs.com/package/eslint-config-prettier) - Turns off all rules that are unnecessary or might conflict with extension Prettier (use this if prettier is installed).


<br>
<p align="right"><a id="what-is-webpack" href="#table-of-content">↩ Back To Top</a></p>

## [**Webpack**](#)

### [**What is Webpack**](#)

Webpack is a bundler, code transpiler, dependencies manager and general automation tool that is used widely in web development. Webpack builds and transpiles javascript for node and generates new minimal html/css/js files files that are optimized to run in a browser. It can perform lots of automation stuff like converting pictures, combining and transforming files and executing scripts.  Webpack is instructed in _webpack.config.js_, in root of the running project, file where to start bundling (entry .js file). By default webpack only understands javascript, but with help of loader packages we can ninstruct webpack how to handle other languaages. Before Webpack gained popularity [Grunt](https://gruntjs.com/) or [Gulp](https://gulpjs.com/) were popular bundlers (task runners).

Good YouTube tutorial 'Webpack Crash Course' can be found [here](https://www.youtube.com/watch?v=lziuNMk_8eQ)  

<p align="right"><a id="webpack-dev-server-m" href="#table-of-content">↩ Back To Top</a></p>

### [**Webpack Dev Server**](#)

Webpack Dev Server is a npm package (named _webpack-dev-server_) that powers up a local server and serves compiled files from your project to it. It can automatically when a file withing a project is saved inject code to running browsers, hot module replacement. This injection is done is such a way that browser do not need to perform any 'hard refresh' and keeps its state which is very convenient when CSS styling as we keep the state of the UI. Content can also be reached from several browsers on the same wi-fy network at the same time. In order to get it work some lines need to be adde in _package.json_ and _webpack.config.js_ and some npm packages need to be installed.

To add Webpack-dev-server to project:

```javascript
> npm install -D webpack-dev-server
// or
> npm install webpack-dev-server --save-dev

```

In projects **package.json** add new script to run it:

```javascript
"serve": "webpack serve",
"build": "webpack"
```

Example of configuration for web **webpack.config.js**:

```javascript
...
DevServer: {
    before: (app, server) => { server._watch('./__/*.html') },
    contentBase: path.join(__dirname, 'app'),
    hot: true,
    stats: 'errors-only',
    noInfo: false,
    port: 3000,
    host: '0.0.0.0'
},
...
```

### [**Vue CLI**](#)
Vue Cli runs webpack inside and hides webpack.config.js file but it can be configure from vue.config.js file [read more here](https://cli.vuejs.org/config/).  

Vue CLI uses PostCSS internally. Read more [here](https://cli.vuejs.org/guide/css.html#automatic-imports).

Example how to add postCSS plugins to Vue cli project through **vue.config.js**:
```javascript
const { defineConfig } = require('@vue/cli-service');

module.exports = defineConfig({
   css: {
      loaderOptions: {
         postcss: {
            postcssOptions: {
               // options here will be passed to postcss-loader
               plugins: [
                  require('postcss-import'), // set first
                  require('postcss-nested'),
                  require('postcss-simple-vars')
               ]
            }
         }
      }
   }
});
```

<p align="right"><a id="what-is-postcss" href="#table-of-content">↩ Back To Top</a></p>

### [**PostCSS in webpack**](#)

**PostCSS** functionality can be added to your weback project. Note that postcss and postcss-cli are by default included by webpack!

Read more [here](https://github.com/postcss/postcss#webpack)

```javascript
// webpack specific plugins for postcss to work
> npm i -D postcss-loader style-loader css-loader
// postcss plugins
> npm i -D postcss-import postcss-mixins postcss-simple-vars postcss-nested

// Additionaly we need to add some configuration in Webpack.config.js to utilize the plugins
```

<p align="right"><a id="build-for-production" href="#table-of-content">↩ Back To Top</a></p>

### [**Build for production**](#)

A project development consists of two phases. One is coding and testing internally on local machine  and after all is done and tested to set up all files so that we can deploy them to a server to serve and run publicly.

The process of coding uses special syntax and tools that aim to help the developer to code as fast as possible. The code created in this state is normally not usable in normal browsers,as a browser would not understand the special syntax and file structure used. Here special tools like Webpack Dev Server or VSCode extension Live Server helps us to visualy test and see the progress under development.

In order to **deploy** we must build our code in the project to structure and format that is suitable for publishing to a server. Normally this code is generated and saved in a special directory in root of the project called "**dist**".

For webpack a buld process can persist of followin steps:

-   Run an npm script instructing webpack to start a buld for production. Webpack.config.js instructs to run special commands and use special plugins for this. Example [here](#webbpack-config-js)
-   Webpack creates "dist" for generated files, but first empties it in case soemething is already generaates inside it.
-   If the bundled file is becomming to big - chank it up in smaller files that can be loaded when needed (lazy loading)
-   Autogenerate one file transpiles css file contaning our css/postcss/scss code.
-   Minimize all files.
-   Copy all assets (like images) to "dist"
-   Autogenerate all dependencies and .html file and save in "dist"
-   Change reference to script/css files in `<script>` `<link>` elements in html file to refer to correct newly autogenerated .css and .js files.

There can be more steps needed depending on type of project and needs. All the steps are performed with help of npm plugins and customized a [webpack.config,js](#webbpack-config-js) file.

<p align="right"><a id="webbpack-config-js" href="#table-of-content">↩ Back To Top</a></p>

### [**Webpack.config.js file**](#)

_Exmaple of an `webpack.config.js` file_
```javascript
// recognizing what script is run - 'serve'/'dev'/'build'
const npmScript = process.env.npm_lifecycle_event; 

// PostCSS plugins that transform our written css to "browser-friendly"
const postCSSPlugins = [
   require('postcss-import'),
   require('postcss-mixins'),
   require('postcss-simple-vars'),
   require('postcss-nested')
];

module.exports = config = {
   entry: path.resolve(__dirname, 'entry.js'), // path to .js file to start bundling
   module: { rules: [] }, // populated later depending on compilation mode.
};

if (npmScript == 'dev') {
     config.mode = 'development';
     config.output = { 
                        path: '', 
                        filename: 'bundled.js'  // bundled javascript will be served from cache (not save to any location)
                     }; 
    config.module.rules = [
      {
         test: /\.css$/i,
         use: [
            'style-loader', // bundel css & as javascript in one file to browser
            {
               loader: 'css-loader', // bundle css into a js-file with import
               options: { url: false } // by default=true, css-loader handles images (e.g.background images). It can be disabled.
            },
            {
               loader: 'postcss-loader', // loads various postcss plugins to transform postcss to pure css
               options: {
                  postcssOptions: { plugins: postCSSPlugins }
               }
            },
            {
                test: /\.vue$/,
                loader: 'vue-loader' // parses parts of vue components
            }
         ]
      }
   ];
    
} else if (npmScript == 'build') {
     config.mode = 'production';
     config.output = {
                        path: path.resolve(__dirname, 'dist'),  
                        filename: '[name].[chunkhash].js', // filename with unique hash regenerated when changes applied.
                    };
                    
    ...
    
}

``` 

<p align="right"><a id="vitei" href="#table-of-content">↩ Back To Top</a></p>

## [Vite](#)

TODO write about vite

<p align="right"><a id="documenting-code" href="#table-of-content">↩ Back To Top</a></p>

## [**Documenting your code (JSDoc)**](#)

[JSDoc](https://jsdoc.app/) is a "markup language" for documentation aswell it is improving intellisense as it is build in VSCode. To instruct intellisense in VScode we can use JSDoc’s `@param`, `@type` and `@typedef` block tags in comments `/** */`.

Read more about jsdoc [here](https://jsdoc.app/tags-param.html#examples)

First we must enable type checkong:
```javascript
Add this to beginning of each js/ts file 
//@ts-check

To check skip one file
// @ts-nocheck

To disable one error
// @ts-ignore

or

/* Modify workspace setting */
/* Note! Is any js/tsconfig.jscon exists for the project */
/* then this have no affect and we must set in in config */
"js/ts.implicitProjectConfig.checkJs": true

or

/* Add to "jsconfig.json" */
"compilerOptions": {
   "checkJs": true
}
/* Add to "tsconfig.json"  */
"compilerOptions": {
    "allowJs": true,
    "checkJs": true
  }

```
Example
```javascript
/** @type {number | string | null} */
let foo;
foo = "hello" // 
foo = undefined //
foo = {}

// Here intellisense will then show correct type of foo as <Array>

/** Function description ...
 *  @param {string} fName - parameter description with type
 */
function fnc(fName) {... return true/false}

// Here intellisense will then show correct type of fName as <string>, decription texts. 

/** Assign the project to an employee. Destructing example.
 *  @param {Object} employee - The employee ocject
 *  @param {string} employee.name - Name of the employee
 *  @param {string} employee.department - Employee's department
 */
const fnc = function(employee) {... }
const fnc = function({ name, department }) {...}


/** Says hello. Several inputs.
 * @param {(string|string[])} somebody - Name, or an array of names
 */
function sayHello(somebody) {...}
   
```

<p align="right"><a id="frontend-ui" href="#table-of-content">↩ Back To Top</a></p>

## [Fonts & Icons](#)

HTML elements can be styled by various pre-written css classes.


<p align="right"><a id="postcss-in-webdev" href="#table-of-content">↩ Back To Top</a></p>

### [**Postcss**](#)
A tool for transforming custom css using javascript plugins. It is neither a post-processor nor a pre-processor, on its own simply an api that transforms special CSS syntax into vanilla CSS. It is used in many popular front-end tools, task runners and bundlers like _Nuxt_, _Next_, _Weback_, _Vite_. You can use only the plugins for features you need just for your application (opposite to including whole sass/less).

> Install  **PostCSS Intellisense and Highlighting** plugin if you are using **Visual Studio Code** editor, so that your editor can recognize any new postcss syntax and stop giving you errors.

- Postcss home [postcss.org](https://postcss.org/)
- How to configure npm scripts with [postcss-cli plugin](https://www.npmjs.com/package/postcss-cli).
- Good article explaining postcss [here](https://www.freecodecamp.org/news/what-is-postcss/)
- Good video about [getting started with postcss](https://www.youtube.com/watch?v=ohJcZW60br0)
- Good video about [postcss-preset-env](https://www.youtube.com/watch?v=Ek1JP3BzbhY)

#### Plugins:
-  [postcss](https://www.npmjs.com/package/postcss) - a tool for transforming css styles
-  [postcss-cli](https://www.npmjs.com/package/postcss) - command line interface to run from npm scripts.
-  [postcss-loader](https://www.npmjs.com/package/postcss-loader) - for webpack only! Loader for various postCSS plugins.
-  [postcss-import](https://www.npmjs.com/package/postcss-import) - lets us import CSS files into other files unsing @import (different than the _bad_ import in native CSS). Note, this shall be executed first (defined on top).
-  [postcss-mixins](https://www.npmjs.com/package/postcss-mixins) -  define styles that can be re-used and media queries mixins sass-style. Note! Set this plugin before postcss-simple-vars and postcss-nested. 
-  [postcss-simple-vars](https://www.npmjs.com/package/postcss-simple-vars) - for Sass-like variables i.e $color: red
-  [postcss-nested](https://www.npmjs.com/package/postcss-nested) -  for nesting in CSS 
-  [postcss-media-minmax](https://www.npmjs.com/package/postcss-media-minmax) -  media queries using more intuitive properties 
-  [autoprefixer](https://www.npmjs.com/package/autoprefixer) - Adds browser dependent CSS prefixes when needed (by default build in webpack, nuxt). Autoprefixer uses _browserslist_ i.e.  "browserslist": [ "defaults" ] in package.json
-  [postcss-normalize](https://www.npmjs.com/package/postcss-normalize) -   use parts of normalize.css or sanitize.css as defined by _browserslist_.
__________
-  [postcss-preset-env](https://www.npmjs.com/package/postcss-preset-env) -  convert modern CSS (features from CSSDB) into something most browsers can understand. Mixins, media, custom...  
-  [cssnano](https://cssnano.co/) -  takes your css and runs it through optimisations, to ensure that the final result is as small as possible for a production.


_________

```java
// First install the tool itself (postcss-cli is needed for npm scripts)
> npm i -D postcss postcss-cli

// install some plugins
> npm i -D postcss-import postcss-mixins postcss-simple-vars postcss-nested postcss-media-minmax autoprefixer postcss-normalize cssnano 

// npm script to execute, in package.json (add -w to watch for changes, add -u for used plugins)
> "build:css": "postcss input.css -o output.css -u postcss-import -u postcss-mixins -u postcss-simple-vars -u postcss-nested -u postcss-media-minmax -u autoprefixer -u postcss-normalize -u cssnano"

// Insted of using -u flag in script include in postcss.config.js 
module.exports  {
   plugins: [
      require('postcss-import'), 
      require('postcss-mixins'),
      require('postcss-simple-vars'),
      require('postcss-nested'), 
      require('postcss-media-minmax'), 
      require('autoprefixer'),
      require('postcss-normalize'), 
      require('cssnano'), 
   ],
}
```


<p align="right"><a id="vue-and-bootstrap" href="#table-of-content">↩ Back To Top</a></p>

### [**Bootstrap**](#)

Bootstrap 5 framework is an option to build responsive websites with a mobile-first approach. [Here](https://www.geeksforgeeks.org/difference-between-bootstrap-4-and-bootstrap-5/) are some diffrences between Boootstrap 4 and 5.

There are several ways to include bootstrap to your project. While Bootstrap doesn’t include extensive icons by default, they do have own small icon library that they provide. They have some classes drawing icons that they provide with their default components like `btn-clos`e or `navbar-toggler-icon`. But to install full package of scg bootstrap icons follow [this](https://icons.getbootstrap.com/).

-   **Bootstrap through CDN (add and load from html header)**

This option in worst case downloads all css and all javascript even though we might only use parts of it. It is fast and handy to set up and get started but... it is not optimal and will for sure not make our page load as fast as possible.

```html
<head>
    <!--  CSS (required) -->
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/3.4.1/css/bootstrap.min.css" />

     <!-- Icons (optional) -->
    <link  rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.1/css/all.min.css" />

    <!--  JavaScript (required) -->
    <script type="text/javascript" src="https://stackpath.bootstrapcdn.com/bootstrap/3.4.1/js/bootstrap.min.js" defer></script>
</head>
```

-   **Bootstrap as Npm package**

```html
___________________ add to packages.json _______________
<!-- bootstrap & dependency to get some componentsi.e dropdown to work -->
> npm i bootstrap @popperjs/core

<!-- Popular free nice icons (optional as bootstrap do not use them in their examples. 
Those they use they provide as vectors in css) -->
> npm i @fortawesome/fontawesome-free

<!-- in order to be able to change theme/colors those loaders will be needed -->
> npm i -D sass-loader sass
```

In your main styles.css you must import:

```javascript
______________________ main.js ___________________________
import 'bootstrap/dist/css/bootstrap.css';  // original css
import 'bootstrap'; // all javascript files


// note! you can import individual components also if you want. See documentation.
```

Now after import all the classes are **avaiable globally** in each coponent! Good to go!

In order to **change theme or color** definitions you need change the provided source scss files and rebuild then. Add following someehre to flow in yourmain styles.css file.

```javascript
// own theme/variable/color customization
$primary: blue;
$secondary: gray;

// import unbuild bootstrap styles as source code (dafult values will be owerwritten by our changed)
import '../../../../node_modules/bootstrap/scss/bootstrap.scss';

// Then webpack when building with help of our installed sass-loder and sass plugins
// will exchange our customized things in .scss files and generatre new css that will 
// be globally applied in our code, with our modifications.
```

<p align="right"><a id="vue-and-mdb" href="#table-of-content">↩ Back To Top</a></p>

### [**Mdb**](#)

Mbd encapsulates bootstrap and adds on some extra functionality and effects with Material Design tauch. It is enhenced bootstrap that they provide for free. Their documentation is better than bootstrap and a bit cooler featers.

-   **Install Mdb through CDN (add in html header)**

```html
_____________________ html head ________________________
     <!-- CSS -->
    <link  rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/mdb-ui-kit/3.10.2/mdb.min.css" />

    <!-- Icons (must be included for example to work) -->
    <link  rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.1/css/all.min.css" />

    <!-- Javascript -->
    <script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/mdb-ui-kit/3.10.2/mdb.min.js" defer></script>

    <!-- note! defer forces to load the page content first before executing js-script -->
</head>
```

This option in worst case downloads for every page ALL css and ALL javascript even though we might use only parts of it. It is fast and handy to set up but... it is not optimal and will for sure not make our page load as fast as possible.

-  **Mdb as Npm package (in Vue CLI project)**

In your Vue entry script (usually main.js or app.js) you need to import the css and javascript and icons:

```javascript
______________________ main.js ___________________________


import 'mdb-ui-kit/css/mdb.min.css'; // original css
import 'mdb-ui-kit'; // all javascript files

import 'bootstrap/dist/css/bootstrap.css';  // original css
import 'bootstrap'; // all javascript files

// note! you can import individual components also if you want. See documentation.
```

Now after import all the classes are avaiable globally in each coponent!

```html
___________________ add to packages.json _______________
<!-- mdb free files -->
> npm i mbd-ui-kit

<!-- popular free nice icons (used  in mdb examples) -->
> npm i @fortawesome/fontawesome-free

<!-- in order to be able to change theme/colors those loaders will be needed -->
> npm i -D sass-loader sass
```

Now after import all the classes are **avaiable globally** in each coponent! Good to go!

In order to **change theme or color** definitions you need change the provided source scss files and rebuild then. Add following someehre to flow in your main.js file.

```java
// own theme/variable/color customization
$primary: blue;
$secondary: gray;
...

// import unbuild mdb styles as source code (dafult values will be owerwritten by our changes)
@import '../../../../node_modules/mdb-ui-kit/src/scss/mdb.free.scss';

Then webpack when building with help of our installed sass-loder and sass plugins will exchange our customized things in .scss files and spot out new css that will be globally applied in our code, with our modifications!
```

<p align="right"><a id="vue-and-mdb" href="#table-of-content">↩ Back To Top</a></p>

### [**Fonte Awsome (FA) Icons**](#)

There are three methods how to include font awesome icons into you project: 
1. **[Seperate SVG Icons](https://fontawesome.com/docs/web/use-with/vue/)** - Recommended for production. This method allows you to slim down the build package
2. **[SVG + JS method](https://fontawesome.com/docs/web/setup/host-yourself/svg-js)**  - Nice clear icons, fast to get started, recommended for prototyping and testing out. Hard to choose seperate icons, big bundle size.
3. **[Web Fonts + CSS method](https://fontawesome.com/docs/web/setup/host-yourself/webfonts)** - Fastest to get started with, recommended for prototyping and testing out. Hard to choose seperate icons, big bundle size.

   
You can read about how they differ and what to choose - **[here](https://fontawesome.com/docs/web/dig-deeper/webfont-vs-svg)**. 

Those are free icons provided by fontawesome - [here](https://fontawesome.com/search?o=r&m=free&s=regular%2Csolid)

> Note! It's a handy to import **all** the icon styles for flexibility and to test out different styles as you develop (method 2 & 3). But if you're using just a couple of iconss and styles, we **don't recommend** it for production sites since loading all of the icons styles and fonts isn't great for performance. The bundle size increase and also css files sent from server may contain unnecessary unused styles.

> Note! There are three families of Font Awesome icons:  Classic, Sharp and Brands. Each of the filily contain diffrent styles: Solid, Regular, Light,This, Duotone, Brands. Some are free (Brands, Solid, Regular), some not. See [here](https://fontawesome.com/docs/web/add-icons/how-to).

Most easy to get started is with npm package that includedes all you need all icons and functionality you need.
```bash
> npm i @fortawesome/fontawesome-free
```

**Include with Web Fonts + CSS method**
In `node_modules/@fortawesome/fontawsome-free/` the `/css` folder contains css files for all icons and styles. The `/webfonts` folder contains all of the typeface files that our css styles depend on and link to.

You can eather **copy** `/webfonts` and `/css` into local folder like `/assets/fontawesome/` where you can modify its content by for example removing unwanted styles and icons. Or you can access files directly from node_modules.

```javascript
// Includes everything (big production bundle)
import "@fortawesome/fontawesome-free/css/all.css"  

or
// Include just styles you want
import "@/assets/fontawesome/css/fontawesome.css"  // icons and utilities
import '@/assets/fontawesome/css/solid.css';  // fas prefix
import '@/assets/fontawesome/css/regular.css'; // work with fas prefix too.
import '@/assets/fontawesome/css/brands.css';  

or
// Link from html
 <link href="/assets/fontawesome/css/all.css" ref="stylesheets" >
 <link href="/assets/fontawesome/css/fontawesome.css" ref="stylesheets" >
 <link href="/assets/fontawesome/css/brands.css" ref="stylesheets" >
```

**Include with SVG + JS method** (fastest to get start with)
Pretty much same as above but instead of files from `/css` folder, use files from `/js` folder.

> Note! When importing whole file `import '../js/all.js'` in vite project bundle gets bigger than when importing all from css. Also worth noting that main.js file produced for production gets over 1400 kB easialy!

Youo can also link directly from html header like `<script defer src="/your-path-to-fontawesome/js/all.js"></script>`.

**Seperate SVG Icons** (recommended for production, Vorks in Vue and Nuxt and Vite)

```javascript
// Install SVG core engine
npm i @fortawesome/fontawesome-svg-core

// Install free icons styles (solid, regular, brands)
npm i @fortawesome/free-solid-svg-icons @fortawesome/free-regular-svg-icons @fortawesome/free-brands-svg-icons

// Install special helper component for Vue 3
npm i @fortawesome/vue-fontawesome@latest-3
```

```javascript
Vue | Nuxt example
In the file main.je or plugins/fontawesome.ts
import { createApp } from 'vue';
import App from './App.vue';

// main css for this project
import './assets/main.css';

// icons
// import '@/assets/icons/fontawesome.js';

/* import the fontawesome core */
import { library } from '@fortawesome/fontawesome-svg-core';

/* import font awesome icon component */
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome';

/* import specific icons (here same from diffrent styles) */
import { faUser as fasUser } from '@fortawesome/free-solid-svg-icons';
import { faUser as farUser } from '@fortawesome/free-regular-svg-icons';
import { faFacebook } from '@fortawesome/free-brands-svg-icons';

library.add(fasUser, farUser, faFacebook);

createApp(App).component('fa-icon', FontAwesomeIcon).mount('#app');
```

```javascript
Vuetify example
In the file plugins/fontawesome.ts

import { createVuetify } from 'vuetify';
import 'vuetify/styles';

// import vuetify components and directives
import * as components from 'vuetify/components';
import * as directives from 'vuetify/directives';

// import build-in vuetify iconsets (fontawesome-svg and mdi icons)
import { aliases, fa } from 'vuetify/iconsets/fa-svg';
import { mdi } from 'vuetify/iconsets/mdi';

/* import fontawesome svg core */
import { library } from '@fortawesome/fontawesome-svg-core';

/* import fontawesome vue 3 helper component */
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome';

/* import ALL icons - for prototyping only as this produces huge production bundle */
import { fas } from '@fortawesome/free-solid-svg-icons';
import { far } from '@fortawesome/free-regular-svg-icons';
import { fab } from '@fortawesome/free-brands-svg-icons';
import '@mdi/font/css/materialdesignicons.css';

// Add all used icons here
const icons = [fas, far, fab];

// Add own customized aliases here
const allAliases = { ...aliases, myCustAlias: 'fas fa-circle' };

export default defineNuxtPlugin(nuxtApp => {


   // Creating vuetify with customization
   const vuetify = createVuetify({
      components,
      directives,
      icons: {
         defaultSet: 'fa',
         aliases: allAliases,
         sets: { fa, mdi },
      },
   });

   library.add(...icons); // Include needed icons
   nuxtApp.vueApp.component('font-awesome-icon', FontAwesomeIcon); // note! vuetify looks at hardcoded "font-awesome-icon". Use this name always.
   nuxtApp.vueApp.use(vuetify);
   
   console.log(`Registered plugin vuetify.client.ts. Aliases = `, allAliases);
});
```

**Add icons in your code like this**
_class="Font-Style-Or-Alias + Icon-Name"_

Read [here](https://fontawesome.com/docs/web/use-with/vue/style) how you can add styling in vue.

```html
// As in the first methods
<i class="fa-solid fa-user"></i> 
<i class="fas fa-user"></i> 
<i class="fa-brands fa-facebook fa-2x"></i>
<i class="fab fa-facebook fa-2x fa-spin" style='color: blue'></i>
// or 
<span class="fa-solid fa-user"></span>
<span class="fas fa-user"></span>

// or as in the last method
<fa-icon icon="fab fa-facebook" />
<fa-icon icon="far fa-user" />
```


<p align="right"><a id="error-handling" href="#table-of-content">↩ Back To Top</a></p>

## [**Error handling**](#)

Winston TODO finish this and put in correct place

```
console.log(` Object nbr ${i} is `, object)
console.debug
console.warning.
console.error

```

We want to have more levels, customized print style/coloring, printing to console/file/db/stream and controll if shall be part of production build.

You can try winston but not sure if it is ok to use in Vue frontend.

In order to remove completly logs from code build by vue CLI 4 add extension:  
npm install babel-plugin-transform-remove-console --save-dev

Then in babel.config.js add:  
plugins: [['transform-remove-console', { exclude: ['error', 'warn'] }]]

This will remove all logs except console.error and console.warn

### **Errorhandling**

The Error Object

Just what we can extract from it in an event of an error? The Error object in all browsers support the following two properties:

name: The name of the error, or more specifically, the name of the constructor function the error belongs to.

message: A description of the error, with this description varying depending on the browser.

Six possible values can be returned by the name property, which as mentioned correspond to the names of the error's constructors. They are:

Error Name Description

EvalError An error in the eval() function has occurred.

RangeError Out of range number value has occurred.

ReferenceError An illegal reference has occurred.

SyntaxError A syntax error within code inside the eval() function has occurred. All other syntax errors are not caught by try/catch/finally, and will trigger the default browser error message associated with the error. To catch actual syntax errors, you may use the onerror event.

TypeError An error in the expected variable type has occurred.

URIError An error when encoding or decoding the URI has occurred

throw will terminate the further execution & expose message string on catch the error.

```javascript
try {
    throw "I'm Evil";
    console.log("You'll never reach to me", 123465);
} catch (e) {
    console.log(e); // I'm Evil
}

try {
    throw Error("I'm Evil");
    console.log("You'll never reach to me", 123465);
} catch (e) {
    console.log(e.name, e.message); // Error I'm Evil
}

console.log(typeof new Error('hello')); // object
console.log(typeof Error); // function

Error(x) === new Error(x);
```

<p align="right"><a id="geo-locations" href="#table-of-content">↩ Back To Top</a></p>

## [**Geo locations**](#)

### **Autocomplete**

Here we describe how to get suggestions of city names from google API when typing in an `<input>` field. Suggestions will be show in a dropdown list and this drowdown list we populate and customize ourselfs. When one proposal in the dropdown list is chosen we get and save its: name, id, latittude and longitoude.

To start with:

1. An **object** (written by google) that handles retrieving of predictions must be downloaded and identified with you personal api_key, so that google can connect billing of your account. (How to enable and create such an api_key is described [here](todo).) Such a request in its simplest way can be done by addig a `<script>` tag in the header of your page, so when the page is loaded the needed object loads automatically.

```javascript
// header
<script src='https://maps.googleapis.com/maps/api/js?key=<YOUR_API_KEY>&libraries=places'></script>
```

Now in javascript code we can access the `object` with:

```javascript
let gService = window.google.maps.places.AutocompleteService();
```

2. As we can acces functions that our gService object provides we will use `getPlacePredictions(options, callback)` that takes some options as input and returns the suggestions in callback function that we provide as second parameter.

options described [here](https://developers.google.com/maps/documentation/javascript/reference/places-autocomplete-service#AutocompletionRequest)

```javascript
// tell google service how and what to suggest for
let options = {
    input: str, // mandatory, string that we suggest for i.e. "L", "Lo", "Lon", "Lond", "Londo", "London"
    types: ['(cities)'], // mandatory, restrict results to be cities only. not set returnes all types
    componentRestrictions: { country: ['au', 'us', 'br'] }, // optional, if desires restric to some countries
    location: { lat: -34, lng: 151 }, // optional, if first suggestions shall be close to special location
    radius: 2000, // with location, meters from location obove for prefered suggestions.
    sessionToken: XXX // nique reference used to bundle individual requests into sessions.
};

// tell google service where provide the suggestions
let callback = function (suggestions, status) {
    if ((status = 'OK')) {
        this.suggestionsToShow = suggestions;
    }
};
```



### [**Create a database**](#)

To create a local database with Python we first need create a virtual environment to be more explicit and limit packages to a specific project. Now we are free to go on and installing packages and dependensies for our python database project!

TODO...

<p align="right"><a id="seo-and-responsivness" href="#table-of-content">↩ Back To Top</a></p>

## [**Good to know**](#)

### [**Search Engine optimization**](#)

TODO

<p align="right"><a id="screen-resolutions" href="#table-of-content">↩ Back To Top</a></p>

### [**Screen Sizez**](#)

Most common desctop screen sizes
1366x768 (22.98%) (ratio: 1.75  100/56)
1920x1080 (20.7%) (ratio: 1.75 100/56  --> 1950/1500)
1536x864 (7.92%)  (ratio: 1.75 100/56)
1440x900 (7.23%)  (ratio: 1.6  100/62)
1280x720 (4.46%)  (ratio: 1.75 100/56)

Resolution refers to number of pixels that make up the image on a screen. A higher pixel count means that sharper picture and possibility to show big sharp images with good quality. Resolution is expressed using horizontal and vertical pixel counts.<br> 1366x768

Smartphone 360x640 (#1 popular) Smartphone 375xX (#2 popular)

`Notebooks/Pads - Wildly used, HD, 1366x768. (aka 720) (#3 popular)` <br> `Notebooks/Pads - FULL HD (aka 1080) is 1920x1080 (#4 popular)` <br> `Monitors/TVs - 3K is 3200×1800.`<br> `Monitors/TVs - 4K (UHD = ultra HD) is 3840×2160.` `TV's - 7680x4320`

The predominant display aspect ratio on 2020s PC market, including laptops,tablets, and monitors, is 16:9. Also referred to as widescreen aspect ratio. I.e FULL HD 1920x1080 have 16:9 aspect ratio.

<p align="right"><a id="responsivness-m" href="#table-of-content">↩ Back To Top</a></p>

### [**Responsiveness**](#)

TODO

<p align="right"><a id="other-frameworks" href="#table-of-content">↩ Back To Top</a></p>

## [**Other framewors & tools**](#)

<p align="right"><a id="markdown-syntax" href="#table-of-content">↩ Back To Top</a></p>

### [**Markdown**](#)

Markdown is a lightweight markup language (HTTP is a markup language too) to style text on the web in a fast way. The syntax is much simpler than HTML as it originally was created for non-programmers in order to write easy-to-read format that could be converted directly into HTML. Markdown files are saved with extension .md and only special readers can view them. GitHub for example use its own readme-file-viewer for all README.md files in the root of a project. Chrome with a special plug-in extension can view this files in nice way. Using markdown for styling text makes it possible to view text in a nicer way than just simple text. VSCode have Markdown preview build-in.

> Note! Each heading starting with `#` in background creates a class id based on name. In case of heading `## Node.js & Npm-files` the created id will be `#nodejs--npm-files`. In order to internally navigate to this heading use: `[PRESS HERE](#nodejs--npm-files)` and an internal link will be created.

**Recommended VSCode Extensions**

[Markdown Shortcuts](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one)<br> Adds a list of toggle commands/shortcuts shown in drop-down list when right-clicking in .md file. Very convenient to toggle a selection by choosing from a list. In settings \__ or _ can be chosen to use instead of \*_ and _. Also on title bas GUI icons are shown for .md files, can be customized in options.

[Markdown All in One](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one)<br> Exports to HTML. Export HTML to PDF with browser (e.g. Chrome) if you want.<br> Creates Table Of Content. Use <!-- omit in toc --> beside/above heading to ignore it.<br> Paste (CTRL-V) a link on selected text to create a markdown link.<br> Autocompletion of available assets with ./<br>

### [**Markdown syntax**](#)

**`GENERAL`**

Line spacing:

```
Hello (no space)
World

Result:
Hello World
```

```
Hello (two spaces)
World

Result:
Hello
World


*when 2 or more spaces are used then is means a new paragraph/new line.
```

<br>
Horizontal line:

```
---

Result:
___________________________________________
```

<br>
Special characters

```
\\      backslash
\`      backtick
\*      asterisk
\_      underscore
\{ \}   curly braces
\[ \]   square brackets
\( \)   parentheses
\#      hash
\+      plus
\-      minus
\.      dot
\!      exclamation
&nbsp;  space
```

**`MARKDOWN LISTS`**

1. Chapter one
2. Chapter two
    1. Subchapter one
    2. Subchapter two
3. Chapter three
4. Chapter four

  <br>

-   \- Chapter One
-   \- Chapter two
    -   \- Subchapter one
    -   \- Subchapter two
-   \- Chapter three
-   \- Chapter four

<br>

**`MARKDOWN TEXTS`**

|                    |                  |
| ------------------ | ---------------- |
| normal text        | normal text      |
| `_italic text_`    | _italic text_    |
| `__bold text__`    | **bold text**    |
| `~~striken text~~` | ~~striken text~~ |
| `$f(x)=x/5*2y$`    | $f(x)=x/5*2y$    |

```
#H1

##H2

###H3

####H4

#####H5
```

<br>

**`MARKDOWN LINKS`**

External link: [HERE](http://www.di.se) &nbsp;&nbsp;&nbsp; code=> &nbsp;&nbsp;&nbsp; \[HERE\]\(http://.www.di.se\)

Internal link: [HERE](#table-of-contents) &nbsp;&nbsp;&nbsp; code=> &nbsp;&nbsp;&nbsp; \[HERE\]\(#table-of-contents\)

<br>

**`MARKDOWN IMAGES`**

A nice picture: ![Forest](./app/CSS/assets/nature_251x201.jpg)

_Code:_ &nbsp;&nbsp; A nice picture: \!\[Forest\]\(./app/CSS/assets/nature_251x201.jpg\)

<br>

**`MARKDOWN TEXT BLOCKS`**

This text highlighted as surrounded by ' and not formatted:<br> `` `Unformatted highlighted <br> text <p>tHello!</p><br>` ``

````
.```
- Unformatted lines <br> of text ending with [Enter]
	[TAB] __Unformatted lines of text ending with__ [Enter]
- Unformatted lines of text ending with [Enter]
.```

````

````html
```html
<or javascript>
    <or python>
        Code block - HTML formatted, autocolored [Enter] [Enter]
        <div>
            [Enter] [TAB]
            <h1>Header</h1>
            [Enter] [TAB]
            <p>formatted as HTML - code with colors</p>
            [Enter]
        </div>
        [Enter] ``` .
    </or>
</or>
````

<br>

**`MARKDOWN TABLES`**

```
| Sex | City  | Name/Surname |
| --- | --- | --- |
| Bird  | Dallas <br> Malmö | Martin <br> __Linn__ <br> [Link](http://www.di.se)  |
| Woman <br> Man <br><br><br> | Lund <br> London <br>  Paris <br> Nice |  _Anna_ \<b>Carming\</b> <br> `<br> is 59 years` |
| Child | York | Adam |
```

<br>

**Result**

<br>

| Sex                         | City                                  | Name/Surname                                       |
| --------------------------- | ------------------------------------- | -------------------------------------------------- |
| Bird                        | Dallas <br> Malmö                     | Martin <br> **Linn** <br> [Link](http://www.di.se) |
| Woman <br> Man <br><br><br> | Lund <br> London <br> Paris <br> Nice | _Anna_ \<b>Carming\</b> <br> `<br> is 59 years`    |
| Child                       | York                                  | Adam                                               |

<p align="right"><a id="what-is-netlify" href="#table-of-content">↩ Back To Top</a></p>

### [**Netlify**](#)

TODO

<p align="right"><a id="emmet-snippets" href="#table-of-content">↩ Back To Top</a></p>

### **[EMMET Snippets]()**

EMMET snippets auto-generate full code blocks code from short text snippets. [Here](https://docs.emmet.io/cheat-sheet/) is a handy cheat-sheet with all EMMET commands. Read more about EMMET [here](https://docs.emmet.io/).

| HTML&nbsp;CODE | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |
| :-- | :-- |
| **New doc**<br>**`!`** | _`New HTML doc structure`_ |
| **Comment**<br>**`c`** | `<!-- -->` |
| **CSS from file**<br>**`link:css`** | `<link rel="stylesheet" href="./style.css">` |
| **JS from file**<br>**`script:src`** | `<script src="./app.js"></script>` |
| **Dummy texts**<br>**`lorem4`** | _`Four random lorem words`_ |
| **Paragraph**<br>**`p.hero**title--orange{Hi}`\_\_ | `<p class="hero__title--orange">Hi</p>` |
| **Div**<br>**`.nav**item#nav_item-1{Hi}`\_\_ | `<div class="nav__item" id="nav_item-1">Hi</div>` |
| **Menu**<br>**`ul.nav>(li.nav_row>a#nav_item-\${I\$})*2`** | `<ul class="nav">`<br>&nbsp;&nbsp;&nbsp;`<li class="nav__row"><a href="" id="nav_item-1">I1</a></li>`<br>&nbsp;&nbsp;&nbsp;`<li class="nav__row"><a href="" id="nav_item-2">I2</a></li>`<br>`</ul>` |
| **Form**<br>**`div>p+form:post>input:text+input:email+input:submit`** | `<div>`<br>&nbsp;&nbsp;&nbsp;&nbsp;`<p></p>`<br>&nbsp;&nbsp;&nbsp;&nbsp;`<form action="" method="post">`<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`<input type="text" id="" id="">`<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`<input type="email" id="" id="">`<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`<input type="submit" value="">`<br>&nbsp;&nbsp;&nbsp;&nbsp;`</form>`<br>`</div>` |
| **Article**<br>**`section.sect>(article.wrap>h1.s_t+p.s_d+button.s_b)*1`** | `<section class="sect">`<br>&nbsp;&nbsp;&nbsp;&nbsp;`<article class="wrap">`<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`<h1 class="s_t"></h1>`<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`<p class="s_d"></p>`<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`<button class="s_b"></button>`<br>&nbsp;&nbsp;&nbsp;&nbsp;`</article>`<br>`</section>` |
| <br>**CSS&nbsp;CODE**<br><br> |  |
| **`w100p`** | `width: 100%;` |
| **`h100e`** | `height: 100em;` |
| **`m10p20px10e20p`** | `margin: 10% 20px 10em 20%;` |
| **`p10-20-10-20`** | `padding: 10px 20px 10px 20px;` |
| **`pos`** | `position: relative;` |
| **`bg`** | `background: #000;` |
| **`bc`** | `background-color: #fff;` |
| **`bd`** | `border: 1px solid #000;` |
| **`bdrs8`** | `border-radius: 8px;` |
| **`ff+fw400+fs20`** | `font-family: serif;`<br>`font-weight: 400;`<br>`font-style: 20px;` |

    
    
## [__Screens and Content__](#)

<p align=right><a id="visual-studio-code" align=right href="#table-of-content">↩ Back To Top</a></p>

This setion is about screen sizes,  images, backgrounds and icons.

#### [Screen Resolution]()

Resolution refers to number of pixels that make up the image on a screen. A higher pixel count means that sharper picture and possibility to show big sharp images with good quality. Resolution is expressed using horizontal and vertical pixel counts.<br> 
1366x768

Smartphone 360x640 (#1 popular)
Smartphone 375xX (#2 popular)

`Notebooks/Pads - Wildly used, HD, 1366x768. (aka 720) (#3 popular)` <br>
`Notebooks/Pads - FULL HD (aka 1080) is 1920x1080 (#4 popular)` <br>
`Monitors/TVs - 3K is 3200×1800.`<br>
`Monitors/TVs - 4K (UHD = ultra HD) is 3840×2160.`
`TV's - 7680x4320`


#### [Aspect ratio]()

 ---
<p align=right><a id="visual-studio-code" align=right href="#table-of-content">↩ Back To Top</a></p>

The predominant display aspect ratio on 2020s PC market, including laptops,tablets, and monitors, is 16:9. Also referred to as widescreen aspect ratio. I.e FULL HD 1920x1080 have 16:9 aspect ratio.



# [**SEO**](#)

<p align="right"><a id="visual-studio-code" href="#table-of-content">↩ Back To Top</a></p>

When a ord that someone search for is in H1 and then later in desrtiptio h2 and then many times in text in same article then google might show prio it in SEO. H1 text is then shown in google search description

One of the most important features of HTML5 is its semantics. Semantic HTML refers to syntax that makes the HTML more comprehensible by better defining the different sections and layout of web pages. It makes web pages more informative and adaptable, allowing browsers and search engines to better interpret content. For example, instead of using div id="header" you can use a header tag.

Example. article h1 - what is babajaga? h2 - Many peapople wonder what babajaga is - here comes the answer.abs P - babajag is ... Often babajaga do... We se many babajagas in..

<p align="right"><a id="python" href="#table-of-content">↩ Back To Top</a></p>

## [**Python**](#)

Python is a clear and powerful object-oriented programming language, comparable to Perl, Ruby, Scheme, or Java.

Some of Python's notable features:

-   Uses an elegant syntax, making the programs you write easier to read.
-   Is an easy-to-use language ideal for prototype development without compromising maintainability.
-   Comes with a handy package manager `Pip` for installing python plugins (might be needed to install seperately for Ubuntu/Linux).
-   Comes with a collection of built-in functions and built-in packages.

Install Python globally on you local machine -> [www.python.org](https://www.python.org/downloads/)

> Note! When installing on Windows make sure to add to PATH (a checkbox to check in installation wizard), then it will be avaiable globally from command prompt.

```java
> python --version  // Check current installed version
> phyton  // runs phytom program command line
```

<p align="right"><a id="virtual-enviroments" href="#table-of-content">↩ Back To Top</a></p>

### [**Virtual Enviroments**](#)

[Virtual environments](https://realpython.com/python-virtual-environments-a-primer/#what-is-a-virtual-environment) are "folders" (in simple words) that are isolated and belong to you project and will contain all that packages that a python project use. This means that each project can have its own dependencies regardless of what dependencies every other project has. Then installed project packages and dependencies that you use inside this environment will be independent of your system interpreter.

One of build-in modules in Python 3 is [**venv**](https://docs.python.org/3/library/venv.html) library that provides support for creating **lightweight** “virtual environments”. [Virtualenv](https://pypi.org/project/virtualenv/) is an external python plugin (widly used) that extends python's support for virtual environments as the default [venv](https://docs.python.org/3/library/venv.html) library does not offer all posible features Virtualenv has.

From Python 3.4 you can use venv!

**Use `Venv`**

```java
// similar to virtualenv

> py -m venv x-venv  // creates a virtual environment named 'x-venv'

> x-venv/Scripts/activate.bat  // (windows) activate the 'x-venv' enviroment
> source x-venv/bin/activate  // (linux) activate the 'x-venv' enviroment
```

<br>

_Use `Virtualenv`_

```java
// FIRST OF ALL
// Navigate to root of your project!

// INSTALL PLUGIN
// installs extended virtual enviroment support
> pip install virtualenv

// Note!
// If 'virtualenv' is not a recognized command after installation then becouse its location is not in your system PATH. Easiest is to add its location to your system PATH. Otherwise you can add just run the module by adding "py -m ..." each time you run the command.

// CREATE PROJECT ENVIROMENT
// create a virtual environment named 'x-venv'
> virtualenv x-venv
// or
> py -m virtualenv x-venv

// Note!
// Now in the root of your project you will have a folder named "x-venv" where all kind of customization files and script were autogenerated and additions to your project will be stored. There shall also be a folder named Scripts or script where activation to run script can be found!

// ACTIVATE YOU ENVIROMENT
// When in your project root activate "x-venv" enviroment
> x-venv/Scripts/activate.bat  // (windows)
> source x-venv/bin/activate  // (linux)
```

<p align="right"><a id="pip" href="#table-of-content">↩ Back To Top</a></p>

### [**Pip**](#)

`Pip` is a standard package manager and for most operating systems comes out of the box with Phyton installation. It allows you to install and manage external packages that aren’t part of the Python standard library. Pip packages are automatically downloaded from [pypi.org](https://pypi.org/).

> _It is similar as npm (Node Package Manager) that comes with instalation of NodeJs. Npm packages are downloaded from [npmjs.com](https://www.npmjs.com/package/package)_

<br>

Pip has a variety of commands and option flags designed to manage python packages. Reade more about how Pip works [here](https://realpython.com/what-is-pip/).

> Important! To limit packages to a specific project we must run pip "inside" a virtual environment.

Usefull Pip **commands**

```java
// CHECK VERSION
> where pip
> pip --version
> pip3 --version //used by python 3

// INSTALL LATEST PACKAGE(S)
> py -m pip install package-1  package-2

// DISPLAY INSTALLED PACKAGES
> py -m pip list

// SAVE CURRENT PACKAGE VERSIONS
py -m pip freeze > requirements.txt

// INSTALL PACKAGES FROM LIST
> python -m pip install -r requirements.txt
```


<p align="right"><a id="connect-to-database" href="#table-of-content">↩ Back To Top</a></p>

### [**Connect to database**](#)

TODO...



