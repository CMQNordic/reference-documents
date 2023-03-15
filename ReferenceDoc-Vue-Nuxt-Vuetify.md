<h1 id="vue-nuxt-vuetify">Reference Guide - Vue & Nuxt & Vuetify</h1>
<p align=right><a align=right href="https://github.com/CMQNordic/reference-documents#reference-documents">↩ main menu</a></p>

This is a reference document with usefull information about Vue, Nuxt and Vuetify. 
Written while learning for educational purposes and for quick reference and look-up.
<br>
<br>
<p align=right>Written by Martin Czerwinski ®CMQ Nordic AB</p>

---
<p id="table-of-content"></p>

#### [**TABLE OF CONTENT**](#)

 [**►Comparison**: Vite - Vue - Nuxt - Vuetify](#comparison)
  [**🔶 VUE**](#vue)
  [Get started](#get-started-with-vue) ◦ [Rendering modes](#vue-rendering-modes) ◦ [Project structure](#vue-project-structure)  ◦ [Composition API](#vue-composition-api) ◦ [Variables and styling](#vue-style)
  **Syntax:** [Directives](#vue-directives) ◦ [Properties](#vue-properties) ◦ [Methods vs.Computed](#vue-methods-vs-computed) ◦ [$refs](#vue-refs) ◦ [Watchers](#vue-watch) ◦ [Emits](#vue-emits) ◦ [Events and modifiers](#events-and-modifiers) ◦ [Slots](#dynamind-components) ◦ [Binding Class or Style](#binding-class-or-style) ◦ [Provide/Inject](#vue-provide-inject-in-vue)
  **How it works:** [Components](#components-in-vue) ◦ [Lifecycle hooks](#vue-hooks) ◦ [Routes|Navigation|Nesting](#router-in-vue)  ◦ [Route validations](#vue-route-validation) ◦ [Store](#store-in-vue) ◦ [Global properties](#global-parameters) ◦ [Styling](#vue-styling) ◦ [Using plugins](#vue-using-plugins) ◦ [Adding modules](#vue-adding-modules) ◦ [Error handling](#error-handling)  
  **Deployment:** [Linting and formatting ](#linting-and-formatting)  ◦ [Optimize for production](#vue-optimize) ◦ [Minimalistic production code](#minimalistic-code)
  [**🔶 NUXT**](#nuxt)  
   **Basics:** [Get started](#get-started-with-nuxt) ◦ [Rendering modes](#nuxt-rendering-modes) ◦ [Project structure](#structure-of-nuxt-projects) ◦ [Styling](#nuxt-styling) ◦ [Nuxi commands](#nuxt-cli-nuxi) ◦ [Nuxt/Vue instance](#nuxt-vue-instance)
  **How it works:** [Lifecycle hooks](#vue-hooks) ◦ [Components](#components-in-nuxt) ◦ [Routes|Navigation|Nesting](#nuxt-routes-navigation) ◦ [Route validations](#nuxt-route-validation)  ◦ [Store](#store-in-nuxt) ◦ [Global properties](#global-properties-nuxt) ◦ [Adding plugins](#nuxt-using-plugins) ◦ [Adding modules & postcss](#nuxt-adding-modules) ◦ [Error handling](#error-handling-nuxt)
  **Deployment:** [Minimalistic production code](#minimalistic-code-nuxt) 
  [**►  BUILDING**](#building-projects)
  [Vite](#vite) ◦ [Types](#build-types) ◦ [Minimize](#build-minimize)
  [**►  UI FRAMEWORKS**](#ui-frameworks) 
 [Vuetify](#vuetify) ◦ [Tailwind](#tailwind) ◦ [Bootstrap-5/Vue-Bootstrap](#)
  
<br>

**RECOMMENDED to read, understand and apply in daily work:**

- [Coding in large projects](https://www.telerik.com/blogs/10-good-practices-building-maintaining-large-vuejs-projects)
- [Layouts with Vue](https://markus.oberlehner.net/blog/dynamic-vue-layout-components/)
- [ESLint and Prettier](https://vueschool.io/articles/vuejs-tutorials/eslint-and-prettier-with-vite-and-vue-js-3/)

</nav>

<br>

<p id="comparison"></p>

## **[Comparison: Vite - Vue - Nuxt - Vuetify](#comparison)**

**Vite** is a building tool used for faster development thanks to super fast Hot Module Reload (HMR), fast cold start times, and CSS + JSX + TypeScript + PostCSS support out of the box.

**Vue** is a JavaScript framework for building simple or complex user interfaces. It has small bundle and is fast and easy to learn. Used for front end development.

**Nuxt** is a server-side rendering framework built on Vue.js. It abstracts away most of the complex configuration of vue and add some extra functionality that makes building vue apps easier and faster.

**Vuetify** is a UI component framework for Vue. It provide clean, responsible and reusable ui components and predefined styles that make it possible to build UI fast. It can be customized to some extend. You can build whole app with it or just use certain components.

Minimalistic scaffolded project with javascript, store, 2 routes and simple text & button (ver 3)

| | entry.css (zipped) | entry.js (zipped)| dev start|
|--|--|--|--|
|vite|||
|vite+vue| 1kB (0.7kB) | 73kB (30kB) | 1.2 sek| 
|vite+vue+vuetify| 256kB (34kB) | 136kB (51kB) | 3 sek| 
|vite+vue+nuxt| 1kB (0.74kB) | 132kB (50kB) | 4 sek |
|vite+vue+nuxt+vuetify| 238kB (29kB) | 153kB (60kB )| 7 sek |
|vite+vue+nuxt+vuetify-all-elements| 408kB (418kB) | 392kB (401kB) | 10 sek |

Adding vuetify adds: 20k of js, 

<p id="vue"></p>

## **[VUE]()**

---
<p align=right><a id="vue-intro" href="#table-of-content"></a></p>

### [**Intro**]()
There is a significant difference between Vue 2 and Vue 3 (released in beginning of 2022). Here we concentrate on Vue 3 and component API.

<p align=right><a id="get-started-with-vue" href="#table-of-content">↩ Back To Top</a></p>

### [**Get started**]()
**`Vue CLI`** from vue 2 uses _webpack_, while **`Create-Vue`** is based on _vite_. Vite supports most of the conventions found in Vue CLI projects out of the box, and provides a significantly better development experience due to its extremely fast startup and hot-module replacement speed.

> Note that Vue 3 works both with both Vite and Webpack. Recommended IDE setup is Visual Studio Code & [Volar extension](https://marketplace.visualstudio.com/items?itemName=Vue.volar).

> Note! `PostCSS` & `Postcss-loader` (as well as sass and other pre-process loaders) are included by default in Vue, so just need to install desired postcss plugins and add them to you project.
 
> Node must be installed version 16.0 or higher (run `node -v`). If your project path contains &-characters you might experience strange errors. Do not use &-characters.

Official installing instructions - [here](https://vuejs.org/guide/quick-start.html#with-build-tools). 

**►Scruffold Vue 3 project with [Create-Vue](https://github.com/vuejs/create-vue) | [Vite](https://vitejs.dev/) | [Pinia](https://pinia.vuejs.org/)**
```java
> npm init vue
```

> Note! A minimal Vue 3 project have js client bundle (zipped) of approx 30 kB. It is very small!

**►Create Vue 2 or 3 projects based on [Webpack](https://vitejs.dev/) | [Vue CLI](https://cli.vuejs.org/#getting-started)** -> check [here](https://v2.vuejs.org/v2/guide/installation.html#CLI)
> Note! Vue CLI is now in maintenance mode. For new projects, please use create-vue to scaffold Vite-based projects.

In both cases we are presented with an installation wizard and need to pre-define some configuration such as:
- **Use Babel?**
  _(Vue CLI only)_ Babel is used by webpack and is a javascript transpiler that converts modern javascript to plain ES5 javascript that can be understood by older browsers. A babel preset must be installed and defined either in babel.config.js or package.json (examples [here](https://babeljs.io/docs/en/presets/))
- **JavaScript or TypeScript?**
- **Add JSX Support?**
- **Progressive Web App (PWA)?** 
  _(Vue CLI only, at the moment)_ PWA use progressive enhancement and new capabilities that are enabled in modern browsers. Apps can be installed (to work offline) and run in a standalone browser window instead of a browser, push notifications and work with the device’s hardware.
- **Include Router? Include Store - vuex or pinia?**
  Pinia is recommended for Vue 3 Vite projects. 
- **Add pre-processors?**
  _(Vue CLI only)_ Vite support most loaders like postcss, sass, scss by default. Postcss loader is supported by default in both webpack and vite. For processing other CSS preprocessors like Sass or Less in webpack you must choose them for the loaders to be added to the project.  
- **Add linter/prettier?**
  ESLint checks the syntax of your code and warns you or generate errors AND it additionally can format the code to (like prettier do). When setting up a project we may be asked what linter style to use (error prevention, prettier, airbnb or other style guides).
- **Add Unit Testing?** **Add E2E Testing?**

<p align=right><a id="vue-rendering-modes" href="#table-of-content">↩ Back To Top</a></p>

### [**Rendering modes**]()
Client-side rendered a Single Page Application (**SPA**) is the **default** rendering mode i Vue. Then client downloads empty initial html and all js scripts. After all is dowloaded (whole app with all routes) then HTML rendered in the client. 

Server Side Rendering (**SSR**) can be implemented with vue.js but it is difficult - read more [here](https://vuejs.org/guide/scaling-up/ssr.html#overview). Nuxt framework specializes in this and provides SSR out of the box without need for any configuration.

<p align=right><a id="vue-project-structure" href="#table-of-content">↩ Back To Top</a></p>

### [**Project structure**](#)
Everything that is within the **assets** folder will be handled by bundler while everything in the **public** folder is simply copied to /dist when building for production and but doesn't go through bundler (is never optimized). This folder is common for images/videos/fonts/svgs etc that we must import within vue files in order to be handled and end up in /dist folder as a file with a hash name ex: 5j2i35j.jpg.

To access images from **assets** folder in Vue we need to require or `import @/assets/...`

To access images from **public** folder in Vue we use its path `str="./images/myimage.jpg"`. We use it when we need a file with a specific name in the build output i.e favoicon.ico. Or have many already cropped and fixed  images and need to dynamically reference their paths.

Scaffolded Vite | Vue projects might have partly predefined folder structure like this

```
/root
├── / dist
├── / public 
│    ├── favicon.ico
│    └── index.html (webpack projects auto-injects here)
├── / src
│   ├── / assets
│   │    ├── / images 
│   │    └── / css
│   │         ├── postcss/mixins.css
│   │         ├── vuetify/settings.scss
│   │         ├── modules/_main-hero.css
│   │         ├── _base.css
│   │         ├── _colors.css
│   │         │   │ _variables.css
│   │         ├── ...
│   │         ├── main.css  (imports all partial css styles)
│   │         └── main.scss (imports all partial scss styles to transpile)
│   │    
│   ├── / node_nodules  (auto-generated by "npm install")
│   │
│   ├── / components 
│   │       ├── / ui       (AppButton, AppCard ..)
│   │       ├── / icons    (.vue svg icons ..)
│   │       ├── / layouts   (TheHeader, TheFooter ..)
│   │       └── ...
│   │   
│   ├── / common 
│   │        ├── / utilities
│   │        ├── / composables
│   │        ├── / mixins
│   │        └── ...
│   │       
│   ├── / translations 
│   ├── / layouts 
│   ├── / router
│   ├── / store 
│   ├── / views           (entry points for routes, sometimes named pages)
│   │
│   ├── main.js/main.ts   (main script importing everything including ~/assets/css/main.css)
│   └── App.vue           (entry component)
│
├── index.html (vite projects and links to /src/main.js & /favicon.ico)
│
├── .gitignore        (config for git)
├── .eslintrc.cjs     (config for esLint)
├── .prettierrc.json  (config for Prettier)
├──  tsconfig.json    (config for Typescript)
├──  babel.config.js  (webpack projects only)
│    ...
├──  package.json
└──  webpack.config.js or vite.config.js
```
- **dist** - Folder created by bundler (vite/webpack) when building files for production. Deploy files from here. 
- **public** - Any assets placed here will simply be copied in production build and not go through webpack/vite. We need to reference them using absolute paths. Note! Those are not minified nor bundled together. When referenced via absolute path, you need to take into account where your app will be deployed. Red more [here](https://cli.vuejs.org/guide/html-and-static-assets.html#the-public-folder).
- **assets** — Files that are **imported** into components and handled by the bundler, i.e images, css and scss files.
- **components** — All the components of the projects that are not pages (views).
- **utilities** — Files to use in all components, such as regex, constants or filters. 
- **composables** — Vue 3, reusable reactive blocks used by componets (like mixins but better)
- **mixins** — Mixins are javascript code that is reused in different components. In a mixin you can put any component’s methods from Vue.js they will be merged with the ones of the component that uses it. Use composable in Vue 3
- **translations** — Locales files i.e. Vue-i18n, and it works pretty good.
- **router** — All the routes of your projects (i.e. in index.js). 
- **store** — Store modules contaning global data.
- **views** — Components that are entry points for routs. Preferable only those components should comunicate with the store.

**Smart components** are also called containers, those components handle the state changes, they are responsible for how things work (logic). On the opposite, the **dumb components**, also called presentational, only handle the look and feel (pure ui).

To differentiate **dumb components** that are used in many places in UI we store those in a folder named `/components/ui/` and all the names start with i.e. App like AppButton, AppFrame, AppDivider. Those shall be build to be generic and suit the overall sites UI and can sometimes be customizable by calling component (by props).

**Smart component**s are grouped by feature they belong to and might have own folder in components for those belonging together. We always start to use feature as first part of the name i.e. products/ProductsList, products/ProductsFilters, products/ProductCard, products/ProductsCallToAction.

Only components in views/ (or pages/) (/layouts) can be **single worded** (Home, Contact, About) as they are always called by router and never from html, and do not risk to conflict with naming of default html elements that always are single-words.

**Components** that should only ever have a single active instance (used once per page) should begin with the prefix “The”, to denote that those are only used once in the entire page. For example TheNavbar, TheHeader, TheFooter, TheFooter, TheAppWrapper, TheMainHero. These components never accept any props, since they are specific to your app.

Child components should include their parent name as a prefix. For example if you would like a “Photo” component used in the “UserCard” you will name it “UserCardPhoto”.

**MVC pattern:**   
**Model** -> store 
**View** -> dumb components  
**Controller** -> mart components 

<p align=right><a id="vue-composition-api" href="#table-of-content">↩Back To Top</a></p>

### [**Composition API**]()

Composition API was introduced in Vue 3 and  built-in feature of Vue 3. The primary advantage of Composition API is that it enables clean, efficient logic reuse in the form of Composable functions. It solves all the drawbacks of mixins and introduces composables i.e from VueUse (collection of composable utilities).  Options API poses serious limitations when a single component's logic grows beyond a certain complexity threshold. It was also created with Typescript support in mind. Code written in Composition API and `<script setup>` is also more efficient and minimalistic.

`<script setup>` is a compile-time syntactic sugar for using Composition API and simplifies the syntax. Recommended always to use it due to many reasons (i.e better performance).

```html
<template>
  <div> {{ combinedName }}</div>
  <button  @click="increaseAge(1)"></button>
  <MyComponentA />
<template>
```

```html
<script setup>
    import {ref, toRef} from 'Vue'
    import ComponentA as MyComponentA from './components/ComponentA'
    
    const props = defineProps({
      name: String
    })
    const age = ref(30)
    const name = toRef(props, "name"); // let name = props.name; is wrong as it lose reactivity when accessed in <template>
    
    function increaseAge(val) {
       age.value += val;
       console.log(age.value);  // must always use .value for reactive variables accessed in <script>
    }

    let combinedName = `${name.value} ${age.value}`
    
</script>  
```

```html
<script>
import {ref, toRef} from 'Vue'
import ComponentA from './components/ComponentA'

export default {
  props: {
      name: String
  },
  components: {
      MyComponentA: ComponentA
  },
  
  setup(props, context) { // setup(props, {attrs, slots, emit})
    const age = ref(33)
    const name = toRef(props, "name"); // let name = props.name; is wrong as it loses reactivity when accessed in <template>
    
    console.log(name.value);  // must always use .value for reactive variables

    let combinedName = `${name.value} ${age.value}`

    // Anything returned will be available in <template>
    return {
      combinedName
    };
  },
};
</script>
```

**setup() or `<script setup>`** is only called once and before mounted() therefore `this` is not possible to be used in it as we do in options api.

**props** is an object always passed as first parameters to setup where each prop passed to the component is a property.

**context** is a normal an object with three component properties:  
attrs – Attributes (Non-Reactive) ??? TODO  
 slots – Slots (Non-Reactive) ??? TODO  
 emit – Method (Emit events) ??? TODO

<p align=right><a id="vue-style" href="#table-of-content">↩Back To Top</a></p>

### [**Variables and styling**](#)
**CSS**
There are 2 ways to add global css styling/variables to a vue project.
The aim is it to be to be accessible withing `<style></style>` in all components 
and in ` <template><p style="var(--RED)"></p></template>`.

Given we have a css file: `asstets/main.css`

```css
/* A css variable */
::root {
	--RED: red;
}

/* Two simple used styles */
body {
	background-color: lightblue;
	color: white;
}
.green-text {
	color: green;
}

/* unused style */
.unused-class {
	background-color: black;
}
```

We can **apply** this style in 2 both equal ways:
From **app.vue:**
```javascript
<style>
@import '@/assets/main.css';
</style>
```

From **main.js:** (bundler with css loader assumed - in Vite included by default)
```javascript
import { createApp } from 'vue';
...
import '@/assets/main.css';
...
</style>
```

Now... when we with Vite **build** the project and **preview** (`npm run preview`) then we can observe following:
 - link to generated css file is added in html head for every loaded page for both cases. 
 - This generated css file is minimized (whitespaces removed by vite) and contain ALL styles from our `assets/main.css`. Evethe those unused.
 - If we add styles in both ways at same time, in dev we get duplicates but in production vite removes duplicates.

**Conclusion**: 
Best to add styles from main.js as global js script are added there too so we have everything in same place. But it really dows not matter for performance if asses in <styles> in app.vue instead. Also if imported twice by misstake in seversl places, then in production duplicates will be removed. That's good news.

But if importing big frameworks styles and do not use all classes (i.e Vuetify) then unfortunately we end up with all the styles (even unused ones) in production. Plugin like **PurgeCss** can be used for help with that.

<p align=right><a id="vue-directives" href="#table-of-content">↩ Back To Top</a></p>

## **Vue syntax**

#### [Directives](#vue-directives)
 Vue directives are HTML attributes prefixed with `v-` indicating they are special HTML attributes executed by Vue only. 

 
- **Interpolation**  `{{ name }}`
  ```html
  <p>Name is {{ name }}</p>
  <p>Name is {{ name ? name : 'name is unset' }}</p>
  ```

- **One way binding**  `:href="value"` | `v-bind:href="value"` | `v-bind(value)`
  One way binding between `<script>` and `<template>` or `<style>`
  ```html
  <script setup>
    const url = 'www.image.dev'
    const txtColor = 'red';
  </script>

  <template>
    <!-- binding from script to template -->
    <img b-bind:src="url">
    <p :style="{ color: txtColor }">I'm' red</p>
  </template>
    
  <style>
    // binding from script to style 
    .red {
      color: v-bind(txtColor)
    }
  </style>
  ```

- **inner-html** `v-html="some-html"`
  ```html
  <div v-html="<p>text</p>"></div>
  ```

| | | | |
|--|--|--|--|
|`v-model="value"`<br> or<br> `v-model.title="value"`| Two way binding - script value to template and back. For `<input>`, by default it syncs each char press but with `v-model.lazy` use "change". When using with custom components then custom component must implement prop `:modelValue` and emit `@update:modelValue` but this can be customized. Read more [here](https://vuejs.org/guide/components/events.html#usage-with-v-model). Also in vue 3 we can to other parameters, read more [here](https://vanoneang.github.io/article/v-model-in-vue3.html#turn-it-into-a-composable).| `<input v-model="name" />` <br> v-model.lazy<br> v-model.number/trim/ <br> `<MyComponent v-model:title="bookTitle" />` <br> In child: props: ['title'], emits: ['update:title'] |
|`@click="fnc()"` <br> `v-on:click="fnc"`| Handles an event with correcponding Vue method. Note that if method name without params is used (@click="`handleEvent`") then  this will trigger method with a param - handleEvent(`event`) where event.target is the calling element. If params are used then `$event` must be explicitly defined as input| `<button @click ="addNumber($event, 5)">Add</button>`|
|`@<event>.stop`| Stops propagation/bubbling of an event to parent elements as in js `elem.stopPropagation()`. | `<button @click.stop="add(2)">Add</button>`|
|`@<event>.prevent`| Prevents the default handling of event as in js `elem.preventDefault()`. Used in html `<form>` case when by default HTTP Post is done as submit that refreshes the page.| `<form @submit.prevent="handleSubmit()"><input type=text" /><input type="submit" /></form>` |
|`@<event>.enter.space`| Trigger event function only for `enter` & `space` keys. | `<input @keyup.enter.space="fnc()" />`|
|`v-if="true/false"` <br> or <br> `v-show="true/false"`| HTML elem invisible if false in both cases. With 'v-if' the object is totally removed from DOM and cannot be interacted through DOM. With 'v-show' it is just hidden but not element not removed from DOM. in both cases the element do not take up any space (opposite to css property `visibility:hidden`). Use `v-show` when toggling visibility often for performance as adding/removing elem from DOM cost.<br> `v-else` and `v-else-if` can be used together with `v-if` but must follow directly in block after.<br>But what if we want to toggle more than one element? In this case we can use v-if on a `<template>` element, which serves as an invisible wrapper. | `<span v-if="bVisible">hey</span>` <br> or <br> `<div v-show="bVisible">hey</div>` |
|`v-for="(elem, index) in <array>" :key="unique-id"` <br> or <br> `v-for="(value, name) in <object>" :key="unique-id"`| Renders elements based on data in Array or Object. Note! Each element must be marked with unique Key value in order for Vue to identify elements correctly when removing. Note! Index in the array is not unique as elem nbr 1 gets index 0 when elem nbr 0 is removed. This must be something unique for each elem that never changes. | `<ul><li v-for="obj in array :key="text">{{ obj.text }}</li></ul>` |

Events can be modified to do different things when cached. Here for example execute vanila js `event.stopPropagation()` by simply adding `stop` after event as below in `<span @mousemove.stop="">text</span>` or vanilla js elem.preventDefault() as `<input @submit.prevent="submitForm()">` that prevents the default behavious of sending a HTTP request and refreshing the page. For key-events we can bind certain keys to react for example execute alert function only when `enter key` was pressed `<input @keyup.enter="submitForm()">`

<br><p align=right><a id="vue-properties" href="#table-of-content">↩ Back To Top</a></p>

#### [Component properties](#vue-component-data)

Declaration of properties to use within a vue component is done within `<script>` section with syntax that depends on the used vue version. Dynamical properties can also be passes into the component as **props**.  Properties set in as **props** are always reactive, meaning change in calling parent is reflected in the child.

> **Mutations** of **props** in children are possible but are **not recommended**!

> You can **pass in functions** as a **prop** a but it is **not recommended** pattern of comunication to call functions references from child components (unlike React where children communincate with parent is thought sent functions)

**Vue 3 - Composition Setup API**
```javascript
<scrip setup>
  TODO
</script>
```

**Vue 3 - Composition API**
```javascript
<script>
  TODO
</script>
```

**Vue 2 - Option API**
```javascript
<script>
data() {
  return {
    name: 'Anna',
    age: 32,
    person: {name: 'anna', age: 32},
    fullName: `${this.name} Smith` // Bad! Error! This is not possible!
        
    fncDoSomthing() { ... },
    
    // shortest definition of props
    props: ['name', 'age']

    // longer definition of props
    props: {
      name: String,
      age: Number,
    }
    
    // descriptive definition of props
    props: {
      name: {
        type: String,
        default: ''
      },
      age: {
        type: Number,
        required: true,
        validator(value) {
          return value >= 0 ? true : false;
        }
      }
    }
},
<script>
```

<p align=right><a id="vue-methods-vs-computed" href="#table-of-content">↩ Back To Top</a></p>

#### [Methods vs. Computed](#vue-methods-vs-computed)

**Methods** are normal functions defied in a component ad are executed at componet initialization. Every time they are called from `<template>` then the function evaluated (executed). Methods are usually used only as event handlers.

 **Computed**, similar to methods computed are executed at componet initialization, but then the value they return is evaluated (executed) **only** when an reactive property within it (that its returned value depends on) changes. Computed properties are cached.

>  Note! If several input parameters are used then $event must be explicitly defined as one of them.

>  Note! Technically computed accept parameters BUT the you loose of benefits of using  .computed with cashing. If you need input parameters then use a method!
 
**Vue 3 - Composition Setup API**
```javascript
<script setup>
  const age = ref(0)
  
  const fncIncreaseAge = (event, value = 1) => { ... }
  const age = computed(() => age.value)
</script>
    
<template>
  <button @click="fncIncreaseAge($event, 2 )">
  <button @click="fncIncreaseAge"> // $event is passed automatically, 2nd param undefined
  
  <div> Age is {{ age }} </div>
</template>
```

**Vue 2 - Options API**
```javascript
<script>
  methods: {
    fncIncreaseAge(event, value = 1) {...}
  }
</script>
    
<template>
  <button @click="fncIncreaseAge($event, 2 )">
  <button @click="fncIncreaseAge"> // $event is passed automatically, 2nd param undefined
</template>
```

<p align=right><a id="vue-computed" href="#table-of-content">↩ Back To Top</a></p>



```javascript
<script>
  <template>
  <p>Current score is {{ score }}</p>
</template>

----------
// Vue 3
TODO

----------
// Vue 2
<script>
computed: {
  score() {
    return this.score + 1;
  }
}
</script>
```

<p align=right><a id="vue-refs" href="#table-of-content">↩ Back To Top</a></p>

#### [$refs](#vue-refs)

Easily reach (reference to) certain HTML elements with `ref`.

> Note that you can only access HTML element that a `ref` put too **after** the component is mounted.  This is because the element doesn't exist until after the first render! Before mounted the ref has value undefined.
 
**Vue 3 - Composition Setup API**
 ```javascript
 <script setup>
  import { ref, onMounted } from 'vue';
  
  // To access $refs from <template> we must "redefine" them here
  const thisInput = ref(null);
  const thisButton = ref(null);
  
 const handle = (elem) => alert(elem.Value)  // Hello world
  
  console.log(text, input) //  null null
  
  onMounted(() => {
    const text = thisButton.value.InnerText 
    const input = thisInput.value.Value  
    console.log(text, input) // SUBMIT 123
  })
</script>


<template>
  <button ref="thisButton">SUBMIT</button>
  <input ref="thisInput" value="123"/>
  
  {/* ref accessed only within <template> */}
  <input ref="input" value="Hello world"/>
  <button @click="handle($refs.input)" >Alert input</button>
  
</template>
```

**Vue 3 - Composition API**
```javascript
<template>
  <button ref="coolButton">Press me</button>
  <input ref="someInput" value="123"/>
</template>

// composition setup api (vue3)
<script setup>
  import { ref, onMounted } from 'vue';
  
  const someInput = ref(null);
  const coolButton = ref(null);
  let text, input, fnc;
  
  onMounted(() => {
    text = coolButton.value.InnerText // 'Press me'
    input = someInput.value.Value  // '123'
    fnc = someInput.value.focus()  // 'event onFocus'
  })
</script>

// option api (vue2)
<script>
  ...
  text = this.$refs.coolButton.InnerText // 'Press me'
  input = this.$refs.someInput.Value  // '123'
  fnc = this.$refs.someInput.focus()  // 'event onFocus'
</script>
```

**Vue 2 - ption API**
```javascript
<script>
  ...
  text = this.$refs.coolButton.InnerText // 'Press me'
  input = this.$refs.someInput.Value  // '123'
  fnc = this.$refs.someInput.focus()  // 'event onFocus'
</script>
```

<p align=right><a id="vue-watch" href="#table-of-content">↩ Back To Top</a></p>

#### [Watchers](#vue-watch)

Listener for changes in corresponding properties. Executed only if value in corresponding property changes. Used to execute something  when a change happens. Also used to bind class objects to dynamically bind classes.

```javascript

------------
// Vue 3

------------
// Vue 2
</script>
watch: {
  name: function (newValue, oldValue) {
    console.log("The name changed: New is: %s, old was: %s", newValue, oldValue);
    this.doSomething();
  }
}
</script>
```

<p align=right><a id="vue-components" href="#table-of-content">↩ Back To Top</a></p>

**▸ Components**  
Declaration of components to within an vue instance.

```javascript
<template>
  <CompA />   // PascalCase  strongly recommended for consistency
  <comp-a />  // this works too
  <CompB />  
  <comp-b />  // this works too
</template>

// Vue 3
------------
<script setup>
import CompA from "@/CompA"; // Imports are exposed by default
import {B as CompB} from "@/CompB";
</script>

// Vue 2 (option api)
--------------
import CompA from "@/CompA";
import B from "@/B";

<script>
export default {
  components: {
    CompA,
    'comp-b': B
  },
};
</script>
```

<p align=right><a id="vue-emits" href="#table-of-content">↩ Back To Top</a></p>

#### [Emits](#vue-emits)

Used to send custom events with or without data from a component.  
If you emit an event from a child named in `camelCase`, you will be able to listen in parent for `kebab-cased`. It is recommended to **define** all emitted events with `emits: {...}` in order to better document the component api aswell as not forgetting to implement some emmits (otherwise build error).

Can custom emit event pass more than one value?  
Yes. But as custom events in Vue by design **only accept** two parameters (name and "eventData") then you must encapsulate your values in an object. Note that our "eventData" from child in parent inline listener can be referenced as **`$event`**. If we redirect the event directly to a function with paramaaters then the value object will be splitted in seeral parameters.

Example :

```javascript
______________________ parent _________________________
// different ways of receivin same emmited custom events
<component-x  @doSomething="onDoSomething"  @click="onClick"  @modify-data="onModifyData_1" />
<component-x  @doSomething="onDoSomething"  @click="onClick"  @modify-data="onModifyData_2($event)" />
<component-x  @doSomtehing="onDoSomething"  @click="onClick"  @modify-data="onModifyData_3($event.action, $event.id)" />

// where

methods: {
  onModifyData_1(event) {
    // event.id is '1'
    // event.action is 'delete'
    ...
  },
  onModifyData_2(event) {
    // event.id is '1'
    // event.action is 'delete'
    ...
  },
  onModifyData_3(id, action) {
    // id is '1'
    // action is 'delete'
    ...
  },
  onDoSomething() {
    ...
  },
  onClick(event, id) {
    // do something with element with is
    ...
  }
}
```

```javascript
___________________child (ComponentX.vue)_______________________
<template>
  // only onModifyData_x() method in parent is called (.stop modifier stops the native click-event)
  <button @click.stop="$emit('modifyData', {action: 'delete', id: 1})">Send custom event</button>

  // both onDoSoething() and onClick() methods in parent are called (becouse components tunnel native events)
  <button @click="$emit('do-something')">One more custom event</button>

  // only onClick() method is called
  <button>Send native event</button>
</template>


<script>
export default {
  // Short definition of events this child sends
  emits: ['modifyData', 'do-something']

  or

  // more descriptive way of event this child sends
  emits: {
  modifyData: function(action, id) {
    if (action != null && id != null)
    {
      return true
    }
  },
  'do-something': null,   // No validation
  }

  // Note! We do not define click as it is native event alwats tunneld
}
</script>
```

```javascript
<script setup>const emit = defineEmits(['change', 'delete'])</script>
```

<p align=right><a id="vue-provide-inject-in-vue" href="#table-of-content">↩ Back To Top</a></p>

**▸ Provide/inject**

Used in Vue 2 to pass data to components. Provided data can be a **primitive type** (`String`, `Number`, `Boolean`, `Date`, `Symbol`) or a **reference types** (`Array`, `Object`, `Function`). Provided **primitive** data is **NOT REACTIVE**, meaning if data change in parent it is not reflected in child. Data can be mutaded by child **only for a reference type** as then child have a a pointer to the memory (opposite to primitive type where child has only a copy of the data). But is is **NOT RECOMENDED** as it is hard to follow in larger code base and difficult to debug. Insted send a function that child can call that do modifications on the data. **Only component holding the data shall modify the data!**

Example:

```javascript
export default {
  ________________________ parent ____________________________
...

data() {
  return {
    resources: [
        { name:'Anna', id: 1 },
        { name:'Sara', id: 2 },
    ],
  }
},
methods: {
    deleteResourceMethod(id) {
      // This works in parent but overwites pointer sent to children = no reaction in children!
      // this.resources = this.resources.filter((res) => res.id != id)
      // Use splice instead as it do not modify pointer on resources:
      const i = this.resources.findIndex((res) => res.id === id)
      this.resources.splice(i, 1)
    }
}
provide() {
    return {
        // Any children can inject and use resources.
        providedResources: this.resources,
        // Any children can inject and call this to delete resources
        providedDeleteResourceMethod: this.deleteResourceMethod,
    }
}

...
}
```

```html
____________________________ child x ______________________________
<template>
  <ul>
    <li v-for="res in providedResources" :key="res.id">
      <button @click="providedDeleteResourceMethod(res.id)">
        Remove {{ res.name }}
      </button>
    </li>
  </ul>
</template>

export default { ... inject: ["providedResources",
"providedDeleteResourceMethod"], ... }
```


<p align=right><a id="first-vue-app" href="#table-of-content">↩ Back To Top</a></p>

### [**Create first Vue app**]()

---

A Vue instance is connected with html with `mount('#[id]')` command in a .js file (usually named main.js). After that we can use Vue directives and defined parameters in that part of HTML code.

```html
__________________index.htm______________________
<html lang="en">
  <head>
    <!-- Import Vue 3 package -->
    <script src="https://unpkg.com/vue@next"></script>
  </head>
  <body>
    <h1>Basic Vue example</h1>

    <div id="app">
      <!-- template defined in vue configuration will be added here -->
      <!-- template can also be added here. We choose to demo adding it through javascript as string -->
    </div>

    <!-- link html with vue instance -->
    <script src="./main.js"></script>
  </body>
</html>
```

```javascript
__________________main.js______________________;
var app = Vue.createApp({
  // main template of this app
  // note! normally this template is defined in html or in single file component
  template: `
    <div>
      Name:<input v-model='name' />
      <button @click="increaseAge()">Increase age</button>
      <p>Name is {{ name }} and age is {{ currentAge }}</p>
    </div>
  `,
  // parameters to access in the app
  data() {
    return {
      name: null,
      age: 0,
    };
  },
  // "functions" executed only when used parameters change value
  computed: {
    currentAge() {
      return this.age;
    },
  },
  // methods that usually handle evens triggers from HTML
  methods: {
    increaseAge() {
      return this.age++;
    },
  },
});

// Connect our app instance with HTML
app.mount("#app");
```

<br>
Same as above but as Single Page Application (SPA).

```html
__________________index.html______________________

<html lang="en">
  <head></head>
  <body>
    <div id="app"></div>
    <!-- built files will be auto injected -->
  </body>
</html>
```

```javascript
___________________main.js________________________;
// Entry point for webpack bundler
import { createApp } from "vue";
import App from "./App.vue";
createApp(App).mount("#app");
```

```html
___________________App.vue________________________
<template>
  <div>
    Name:<input v-model="name" />
    <button @click="increaseAge()">Increase age</button>
    <p>Name is {{ name }} and age is {{ currentAge }}</p>
  </div>
</template>

<script>
  export default {
    // parameters to access in the app
    data() {
      return {
        name: null,
        age: 0,
      };
    },
    // "functions" executed only when used parameters 
    computed: {
      currentAge() {
        return this.age;
      },
    },
    // methods that usually handle evens triggers from HTML
    methods: {
      increaseAge() {
        return this.age++;
      },
    },
  };
</script>
```

<p align=right><a id="components-in-vue" href="#table-of-content">↩ Back To Top</a></p>

#### [**Components**](#)

Main building blocks. There are several ways to create a components. Usually `properties`, `methods`, `computed`, `props` ad `emmits` are defined on a components.

Can be an textual attribute like `template: '<p>Hello world</p>'` added manually to vue instance  with `Vue.template(...)` (unusal). Most useful and powerful method is usage of _single-file components_  separate .vue files (SFC files).

Can be reached in code by **kebab-case** `my-component-name` or **PascalCase** `MyComponentName`. Vue files shall be named PascalCase `MyComponentName` and always contain of minimum 2 words. Components that are used only once in a page  are usually named `TheHeader` or `TheFooter`.

Below is an **example** of parent using child component and child and sends some data to it. Child component on other hand is emmiting an event to parent when a button is pressed within the child.

We can global components. Global are registers in `main.js` directly on Vue instance and can be accessed by all components. Otherwise components must be imported. 

Dummy UI companents like `BaseButton` or `BaseCard` are usualy global as they are used in many places in the code. **TODO!** What is he negative things abouot having all global. How are those loaded in production?

Example of an easy component:
```html
<template>
  <div>
     <p>The name is {{ name }}</p>
     <button @click.stop="this.$emit('submit', '1')">send</button>
  </div>
</template>

<script>
  export default {
    props: ['name'],
    emits: ['submit']
  }
</script>
```

<p align=right><a id="vue-hooks" href="#table-of-content">↩ Back To Top</a></p>

#### [**Lifecycle hooks** ](#)

 Functions called at diffrent "states" of s component. Read more  [here](https://www.digitalocean.com/community/tutorials/vuejs-component-lifecycle).

```javascript
created() {
  // Component initialized. Nothing shown on the screen.
  // Template is not compiled (nor verified) yet.
},
mounted() {
  // Component was parsed. DOM is drawn to the screen.
  // Interpolation values exchanged to shown values. 'ref' are avaiable.
},
updated() {
  // Changes to DOM were processed. 
  // The updated change is visible on the screen.
}

beforeUnmount() {
  // called just before the app is unmounted() and dead.
  // Good place to execute any clean up code such as sending 
  // HTTP request informing about shutdown. Can we access $refs here?
}
```

<p align=right><a id="store-in-vue" href="#table-of-content">↩ Back To Top</a></p>

### [**Store** ](#)

**Pinia store**
New store delivered to used with Vue 3. Enhenced. TODO

**Vuex store**

Used mostly in Vue 2

Central local database to read/write data to. Never acces state directly from components (only from getters/mutations). Declare Store like this:

```javascript
import { createStore } from 'vuex';
import InstructorsModule from './InstructorsModule.js';

export default createStore({
    state: {
      uid: null,
      isAuthorized: false
    },
    mutations: {},
    getters: {},
    actions: {},
    modules: {
        instructors: InstructorsModule,
    }
})

// while module declared like this with seperate files for actions/getters/mutations

import mutations from './mutations.js';
import actions from './actions.js';
import getters from './getters.js';

export default {
    namespaced: true, // name: instructors
    state() {
        return {
            instructors: []
        };
    },
    mutations,
    actions,
    getters
};
```

**Actions**  
Perform async actions like HTTP Requests and calling other getters/mutations/actions

```javascript
export default {

    async actionA({dispatch, commit, getters}, payload) {

        // Call mutation from action
        commit('[mutation-name]', payload);

        // Call getter from action
        let result = getters.[getter-name](payload);

        // Call action from action
        let result = await dispatch('[async-action-name]', payload);

        return 'success'
    }

    // Call action from component <template>
    $store.dispatch('[module-name]/[action-name]', {data});

    // Call action from component <script>
    this.$store.dispatch('[module-name]/[action-name]', {this.data});
}
```

**Getters**  
Call state to receive data or call other getters.

```javascript
export default {
    getter_getOne => (state) => (id) {
        // Return one
        return state.users.find((elem) => elem.uid == id);
    }

    getter_getAll(state) {
        // Return one
        return state.users
    }

    getter_getFiltered => (state, getters) => (filters) {
        // Return filterd only or all if no filter
        if (filters) {
            return state.users.filter((elem) => elem.loacation == filters.loacation);
        } else {
            // Call a getter from getter
            return getters.getAll;

        }
    }

    getterA: (state, getters) => (payload) => {
        // Call state from getter - filter on location
        return state.users.filter((elem) => user.loacation == payload.loacation);


    }

    // Call getter from component <template>
    $store.getters.[getter-name]({data})

    // Call getter from component <script>
    this.$store.getters.[getter-name]({this.data})
}
```

**Mutation**  
Call state to modify data and call other mutations.

```javascript
export default {
    mutation_setA: (state, payload) {
        // Call state from mutation. Replace (set) A
        state.A = payload.A;
    }

    mutation_addA: (state, payload) {
        // Call state from mutation. Append (add) A
        state.A = [...state.A, ...payload.A];
    }

    // Call getter from component <template>
     $store.commit('[mutation-name]', data)

    // Call mutation from component <script>
    this.$store.commit('[mutation-name]', this.data)
}
```

<p align=right><a id="events-and-modifiers" href="#table-of-content">↩ Back To Top</a></p>

#### [**Events and modifiers**](#)

Events can be sent from chil to parent and be native or custom. Native events are sent by default by various HTML eleemts. I.e Button sends `click` event and input `submit` when a charactes changes within it. Those events are tunneled to parent from chhild componets always by default. Thos do not need to be emmited.

Custom events are those that we emit. See emits section for that [here](#attribute-emits).

Event carry always `$event` data. For native events it is an object descripting eleemnt that emmited the event `$event.target`. For custom events it might be one single value or object with data depending on design.

**Modifiers**

To prevent default behaviour of an native event vue can modify it when catched.

```
<component-x  @click.stop="doSomething" />
```

**click.stop**: Prevents native event from beeing tunnel to further components.  
**click.prevent**: Prevents default action i.e the submit on form will no longer http post and reload the page

Key events like `keyup` can also be modified.

For example:  
`@keypp.enter="dosomething()"` only triggers for `enter` key.

Read mmore [here](https://vuejs.org/v2/guide/events.html)


<p align=right><a id="dynamind-components" href="#table-of-content">↩ Back To Top</a></p>

#### [**Slots**](#)

Distribute code from one component into other components. Like functions passing parameters into onother function. We have default, named and scoped slots demonstrated below. All provided slots can be reached in object `$slots`.

Child component with slots:
```html
<template>
  
  <!-- named slot -->
  <h1 v-if="$slots.title"> <!-- invisible if nothing provided -->
    <slot name="title" />
  </h1> 
  
  <!-- default slot -->
  <div>
    <slot>
      I'm shown if nothing provided
    <slot />
  </div> 
  
  <!-- scoped slot -->
  <ul>
    <li v-for="(post, i) in posts">
        <slot name="post-item" :title="post.title" :post-index="i" />
    </li>
  </ul>
  
<template>
```
Called from parent as:
```html
<child-with-slots>
  
  <template #title>
    I'm title
  <template>
    
  I'm content provided to default slot
    
  <template #post-item="slotProps">
    <!-- 'slotProps' object has props coming FROM child  -->
    <h2>
      I'm item {{ slotProps['post-index'] }} with title: {{ slotProps.title }}  
    <h2>
  <template>
    
</child-with-slots> 
```

<p align=right><a id="binding-class-or-style" href="#table-of-content">↩ Back To Top</a></p>

**<a >Binding Class or Style</a>**  
There are two ways to bind **class** attribute to Vue component.

- As an array of strings with classes: `['classA', 'class-b']`
- As an object with key/valye pairs: `{classA: true, 'class-b': true}`

Use second option to dynamically enable/disable a selector.

```html
<div class="btn" :class="{'btn-wide': isWide, active: isActive}">
<!-- Same as above -->
<div :class="{btn: true, 'btn-wide': isWide, active: isActive}">

<div class="btn" :class="['btn-wide', 'active']">
<!-- Same as above -->
<div class="btn btn-wide active">

<!-- A mix -->
<div :class="['btn', {'btn-wide': isWide}, objectWithClasses]"></div>
```

**Binding** to **style** is also possible but normally not recommended as inline styling shall be avoided in modern web development.

```html
<p :style="{color: 'black', backgroundColor: coloor, 'font-size': font  + 'px'}" >
 
<div :style="[baseStyles, overridingStyles]"></div>

<!-- where 
const overridingStyles = () => 
  {
    backgroundColor: definedColor, 
    'font-size': '20px' 
  }
-->
```
<p align=right><a id="global-parameters" href="#table-of-content">↩Back To Top</a></p>

### [**Global properties**]()

In main entry script in Vue 3 app (usually main.js or app.js) we ofte do create our app, router, store, global components, global styles etc. Here we can also set global properties to be reached in all .vue files in the project. A global propery provided this way might be marked with `$` to be easialy distinguished in code for better readability. Example:

```javascript
------------------- main.js -------------------------------
// Set global properties on app object
...
import { something } from './some-file.js';
app.config.globalProperties.$something = something;


------------------ any-component.vue ----------------------
// Our something can now be accessed in 3 diffrent places in .vue files
// In template (html), options api (js) and composition api (js).
<template>
    <p>This is {{ $something }}</p>
    <p>This is {{ getSomething }} too</p>
</template>

<sript>
import { getCurrentInstance } from 'vue';
export default {
  computed: {
        getSomething() {
            return this.$something
        }
  },
  setup(props, context) {
    ...
    let $something = getCurrentInstance().appContext.config.globalProperties.$something;
    console.log('something = ' +  $something)
  }
</sript>



--------------------  any-js-file.js --------------------------
// To reach the global propery in .js file (like actions.js) you must import it like in main
import { something as $something } from './some-file.js';
...
console.log('something = ' + $something)
```

_Note:_ Evan You (Vue creator) says: "config.globalProperties are meant as an escape hatch for replicating the behavior of Vue.prototype in Vue 2. In setup functions (composition API), simply import what you need or explicitly use provide/inject to expose properties to app."

<br><p align=right><a id="minimalistic-code" href="#table-of-content">↩ Back To Top</a></p>

### [**Minimalistic code**]()

Webpack and bable transform our javascript code. An web app witteb with javascript framework as Vue can contain a lot of javascript needed to be downloaded to the client at initial HTTP request or subseqient request (lazy loading). Webpack by default minimilizes our code when buildng for production. We can write javascrit in a certain way to help webpack to minimalize amount of javascript code sent to client.  
Look at the example below:

```javascript
delete(state, id) {
    DEBUG ? console.log(`${module}/delete()`) : '';

    const index = state.resources.findIndex((elem) => elem[idKey] == id);
    if (index >= 0) {
        // found -> delete
        state.resources.splice(index, 1);
        state.loadStatus.current = state.resources.length;
    } else if (DEBUG) {
        // this should never happen
        console.error('Error. Resource to delete not found.');
        throw 'Error. Resource to delete not found';
    }
}
```

357 characters  
**transforms to**  
293 characters

```javascript
delete: function (e, t) {
b && console.log(''.concat(h, '/delete()'));
var n = e.resources.findIndex(function (e) {
    return e[p] == t;
});
if (n >= 0) e.resources.splice(n, 1), (e.loadStatus.current = e.resources.length);
else if (b)
    throw (
      (console.error('Error. Resource to delete not found.'),
      'Error. Resource to delete not found')
  );
}
```

or

```javascript
delete(state, id) {
    DEBUG ? console.log(`${module}/delete()`) : '';

    let resources = state.resources;
    let loadStatus = state.loadStatus;

    const index = resources.findIndex((elem) => elem[idKey] == id);
    if (index >= 0) {
        // found -> delete
        resources.splice(index, 1);
        loadStatus.current = resources.length;
    } else if (DEBUG) {
        // this should never happen
        console.error('Error. Resource to delete not found.');
        throw 'Error. Resource to delete not found';
    }
}
```

393 charactes  
**trasforms to**  
281 characters

```javascript
delete: function (e, t) {
  b && console.log(''.concat(h, '/delete()'));
  var n = e.resources,
      r = e.loadStatus,
      o = n.findIndex(function (e) {
          return e[p] == t;
      });
  if (o >= 0) n.splice(o, 1), (r.current = n.length);
  else if (b)
      throw (
          (console.error('Error. Resource to delete not found.'),
          'Error. Resource to delete not found')
      );
}
```

Additionalyy we can instruct babel/webpack to remove console.log in production with

then ony **240 characters**

```javascript
delete: function (e, t) {
    var n = e.resources,
        r = e.loadStatus,
        a = n.findIndex(function (e) {
            return e[h] == t;
        });
    if (a >= 0) n.splice(a, 1), (r.current = n.length);
    else if (f)
        throw (
            (console.error('Error. Resource to delete not found.'),
            'Error. Resource to delete not found')
        );
}
```

It can be seen that changes increasing size of code in dev decreased size of code after webpack minimalization for in production.  
It is good to understand and write code in a way that it is easy to follw/read for developers and as minimilazed as possible in production.

- Use logger plugin (like winston) or remove unwanted console.logs in production (transform-remove-console extension)
- Use short minimalistic texts in your logs.
- Use as short function names as possible without loosing readability.
- Use short properties names.
- Fore repeftive access to object/array properties with long names define those as variables in beggining of functions instead and use those. Minimizer will then change those local names but it can not change names of properties.

<br><p align=right><a id="error-handling" href="#table-of-content">↩ Back To Top</a></p>

### [**Error handling**](#)

- Create a ErrorService class in a js file
- Use swal
- Create a Vues State action that get

<br><p align=right><a id="linting-and-formatting" href="#table-of-content">↩ Back To Top</a></p>

### [**Linting anf formatting**](#)

EsLint detects syntax errors and have diffrent rules and warns/error when not followed. ESLint is not only able to detect errors in your code, but in many cases, can even automatically correct them for you.

Followin can be used for Vue 3 project:

```
'eslint:recommended',
'plugin:vue/base',
'plugin:vue/vue3-essential',
'plugin:vue vue3-strongly-recommended',
'plugin:vue vue3-recommended'
```

Eslint plugin auto fix (format) some fixable proposed warings/errors by running npm script lint with --fix option or set followin in vsc for save actions:

```
"editor.codeActionsOnSave": { "source.fixAll.eslint": true }
```

Installing eslink-plugin-vue to get access to these rules that are defined in .eslintrc.js.

While eslint plugin warns and gives you error whn you are building if you want live warning and visual aid (like red line on error in editor without building, whilte saving) then you need to install and enable eslint extension for vscode to enable vscode integration for eslint.

**Prettier** is a populat formatter. You install it as an extension to vsc and there are very few (almost none) setting. It just runs and formats out of the box. It can format automatically on save when set in setting: "editor.formatOnSave": true

**Important!**  
You must turn off ESLint's formatting rules that would conflict with Prettier. Without this those two will always mismatch and fight in formatting you code and warning in a never ending mess.

> Install: npm install eslint-config-prettier --save-dev

Then add LAST in .eslintrc.js file:

```
extends: [ 'eslint:recommended', ... "prettier" ],
```

<p align=right><a id="vue-optimize" href="#table-of-content">↩ Back To Top</a></p>

### [**Optimize for production**](#)
Vue 3 comes with Vite and we cover it here. For webpack read around and google.

Vite minimizes the produced css file by removing white-space but it do not remove styles that were not used anywhere.

<p id="nuxt"></p>

## [**Nuxt**]()

---
<p align=right><a id="nuxt-intro" href="#table-of-content">↩ Back To Top</a></p>

### [**Intro**]()

Nuxt provides a bunch of features that allow you to create well-structure autogenerated templates in a reduced amount of time. It works on top of Vue and automates several frequent tasks that would take a bit of work to set up with Vue. It sets up [routing](https://vuejs.org/guide/scaling-up/routing.html), [server side rendering](https://vuejs.org/v2/guide/ssr.html) and [static site generation](https://medium.com/javascript-in-plain-english/generate-static-websites-with-nuxt-4fd0491340e) out-of-the-box without any required customization. Most of functionality that nuxt provides can be done in "pure" vue.js but nuxt additionaly minimizes bundle and highly optimizes the files. It save us a lot of overhead work and customization of Vue. It speeds up the development process of a Vue application.

A cool feature of Nuxt is that it can generate a static version of your application. This means that you can host your application in servers like Netlify or GitHub Pages which are actually free even when you have a ton of traffic. Single Page Apps can be deployed on static/JAMstack hosting such as [Netlify](https://www.netlify.com/), [Firebase](https://firebase.google.com/docs/hosting) och Github hosting.

Onother cool feature is that Nuxt by default does a lot of smart optmization such as with `<NuxtLink>` (wrapper of `<a href>`) it prefeteches the links as we scroll through the page. That is one of many optomizations Nuxt is implementin out-of-the-box under the hood for us.

There is Nuxt version 2 and newer version 3 released in end of 2022. 
See this Youtube vide about main features in vue 3 [here](https://youtu.be/gycjMQo7SAI) or read a good article [here](https://vueschool.io/articles/news/nuxt-3-stable-launch-all-the-details-from-nuxt-nation-2022/).

Main diffrences are:
**Nuxt 2:**
- Vue 2
- Webpack
- Webpack Dev Server
- JavaScript only


**Nuxt 3:**
- Vue 3
- Vite (and Webpack)
- Nitro Server (and Webpack Dev Server)
- Nuxi CLI
- JavaScript and TypeScript
- Much smaller server deployments and client bundles (thanks to Vue 3).
- Much faster project creation (thanks to Vue 3)

Nuxt 3 **auto-imports** a lot. 
For example: ref(), composables, components from layouts/pages/component folders. You can add own folder from whith Nuxt shall auto-import from in _`nuxt.config.ts`_. Read more about import configuration [here](https://nuxt.com/docs/api/configuration/nuxt-config/#imports). 

<p align=right><a id="get-started-with-nuxt" href="#table-of-content">↩ Back To Top</a></p>

### [**Get started**](#)

Official get started with new project - [here](https://nuxt.com/docs/getting-started/installation#new-project)

**Sraffold Nuxt 3 + Vue 3 & Vite**
```javascript
// Using Nuxi CLI
> npx nuxi init nuxt-nuxi-generated

// Scruffold a component component 
> npx nuxi add component MyFirstComponent 

// Some usefull commands...
> npm outdated // What's' not up to date?
> npm list -all --depth=5 // list whole project
> npm list vue // list all named *vue*
```

A minimal Nuxt3 project creates a  **js bundle of size 125kB** (**zipped 47kB**). It is very little for both Vue and Nuxt!

Note! By default Vite automatically **treeshakes** all unused javascript from production budndle. Example
```javascript
import * as allLogs from 'module.js'; // unnecessary big module imported
function unused() {alert('unused')};  // never used

logs.oneUsedLogOnly();  

/* In final bundle only oneUsedLogOnly() exist, nothing else. */
```



Unfortunately unused css is not removed by Vite and to **remove unused css** from final bundle we need to use a third party package such as **`nuxt-purgecss`**.
```javascript
// install
> npm i -D nuxt-purgecss

// in nuxt.config.ts add:
modules: [
  ...
  /* Remove unused css from final bundle  */
  ['nuxt-purgecss', {content: ['dist/**/*.html']}],
],
```
We use static generated html as content to scan but you can read how to configure purgecss [here](https://purgecss.com/configuration.html).


A wizard with options is avaiable when scraffolding a **Nuxt2** project:
> _Note! At writing moment nuxt 3 projects created with nuxi cli do not provide this wizard but use a predefined preset templaten to scruffold pretty much empty minimalistic project._

Wizard with following configuration options is avaiable for Nuxt 2:

```
> Define project name
> Use JavaScript or TypeScript (def javascript)
> Default package manager yarn or npm (def npm)
> Add an UI framework? I.e Vuetify., BootstrapVue, Bulma (def none) 
> Add additional modules? I.e. PWA (Progressive Web App), Axios (for HTTP request) (default none)
> Add linting tools? i.e. ESLint, Prettier (def none)
> Add test framework? I.e Jest, WebdriverIO (default none)
> Define rendering mode! Universal (SSR/SSG) or Single Page App (SPA)(def universal)
> Define deployment target! NodeJs (node server), or Static/Jamstack hosting
> Additional settings. Create jsconfig.json? 
> Use github? (def none)

// Note! You can always at later stage change the configuration of your project.
```

<p align=right><a id="nuxt-rendering-modes" href="#table-of-content">↩ Back To Top</a></p>

### [**Rendering and modes**](#)
Browser needs HTML to view the pages. Vue framework creates javascript that generates DOM and subsequently HTML. Both browser and server can render JavaScript into HTML elements. 

So how do we decide if server or client should generated the HTML?

Nuxt comes with preinstalled several rendering modes- read about them [here](https://nuxt.com/docs/guide/concepts/rendering/).

**To handle minifications** of produced js|css|html files use following `config.nuxt.ts`
```javascript
export default defineNuxtConfig({
  
  vite: {
    build: {
      /* Used js minifier when transpiling */
      /* Def "esbuild", false = disable    */
      minify: false,
    },
  },

  postcss: {
    plugins: {
      /* Turn on/off css minification (def true) */
      cssnano: false,
    },
  },

  ...
});
```

◦ **Client Side Rendered (SPA)**
```
Nuxt3: 'ssr: false' & 'npm run generate' =>
=> static html(empty)&js&css for each route  in .output/public.
Client requests only one first page per session, nothing more afterwards.
Hosted for free on static server.
```

Used by Vue by default. Creates projects that are client client side rendered. They are called SPA (Single Page Application) becouse only one single page (empty HTML) is served for every route, and the whole site is generated internally in client after a bunch of necessary scripts are downloaded. Nuxt with this mode generates static html (empty shell), js and css files that can be served from a static server (free). Application might initially load slowly and not be optimized for SEO but the whole site/app is super fast when started. 

◦ **Static Site Rendered**
```
Nuxt3: 'ssr: true' & 'npm run generate' 
=> static html(full)&js&css for each route in .output/public. 
Client request every page (new html) when user click around.
Hosted for free on static server.
```

Static site generation (SSG) pre-renders all pages of the site when you build the application. Nuxt simply crawls your project and build html and payload files for every route. Each page (route) in the application is an own html file with corresponding css and js files. 

> Note! For staticly generated sites with nuxt as on ec 2022 the styles that are placed in `<scripts>` part of app.vue will be add to head of each generated .html file. While styles imported through main.js are added into seperate file that in turn is linked to in html head.

Therefore think twice what you add in app.vue `<styles>` section.


Note! You can also select whitch routes to build ony with. Read more [here](https://nuxt.com/docs/getting-started/deployment#manual-pre-rendering).

◦ **Universal Rendering**
With universal renderng mode (introduces in nuxt 2 as default mode) javascript is rendered both on client-side and server-side. The first route request instead of an almost empty html file, returns fully rendered html page. This html is generated by the server. As the already rendered HTML content is returned to client then browser can imidiately show the content to user, BUT in background all necessary javascript files for WHOLE site are fetched to client. Then the application switch to bahave as a Single Page App and never requests the server. This switch in client to SPA is called **hibernation**. This type of apps have quick initial page load (asuming server cashe or generation HTML content fast) and are better for SEO as crowlers can index those routes easialy. At same time the app preserves the interactivity of a single web application after hybernation. We get the best of both worlds.

```
Nuxt3: 'ssr: false' & 'npm run generate' =>
=> static html(empty)&js&css for each route  in .output/public.
Client requests only one first page per session, nothing more afterwards.
Hosted for free on static server.
```


◦ **Hybrid Rendering**
Nuxt 3 takes universal rendering a step further by introducing hybrid rendering and edge-side rendering.

Previously every route/page of a Nuxt application and server must use the same rendering mode. But hybrid rendering mode allows different caching rules per route to decides how the Server should respond to a new request on a given URL. Then some pages (or all in case of **Statis Site Generation SSG**) could be generated at build time, while others should be client-side rendered. Using route rules you can define rules for a group of nuxt routes, change rendering mode or assign a cache strategy based on route.

<p align=right><a id="structure-of-nuxt-projects" href="#table-of-content">↩ Back To Top</a></p>

### [**Project structure**](#)

Nuxt uses conventions and an **opinionated** directory structure to automate repetitive tasks by default. The configuration file can still customize and override its default behaviors - TODO here link how to customize.

Code is organized into predefined files. Read here about [Nuxt 3 project structure.](https://v3.nuxtjs.org/guide/directory-structure/nuxt

- **main.js** (main vue entry)
  Is hidden and handled automatically in nuxt. Customizable by ... TODO
  
  <br>
- **nuxt.config.ts**
```javascript
export default defineNuxtConfig({
   ssr: true
})
```

  <br>
- **app.vue**
  It is a starting point of the nuxt 3 app.
  
  <br>
- **error.vue**
  You can customize an error page automaticall run by adding `error.vue` in the source directory of your application, alongside app.vue. This page has a single prop `error` which contains an error to handle. _This differ a bit from nuxt 3 where error.vue was placed in layout folder._
  
  <br>
- **components**
  The **`components/`** directory is where you put all you vue components which can then be imported inside your pages, layouts or other components (nuxt 3 automaticall import those). For example `TheHeader.vue`, `TheFooter.vue`, `base`/`Button.vue` will be imported as `<TheHeader>` `<BaseButton>`. Component registered as `MyComponent` can be referenced in the template via both `<MyComponent>` and `<my-component>`.
  
  <br>
- **pages**
  Components in **pages/** are the **first entry points** for the routes. Components in this folder have some extra functinality such as validation added by nuxt. Pages must have a single root element to allow route transitions between pages `<template><div>.. content here..</div></template>`.
  
  Pages are the heart of our application and a lot of customization can be added [read more here](https://v3.nuxtjs.org/guide/directory-structure/pages).
  
  To navigate between pages of your app, you should use the **`<NuxtLink>`** component.

  ```javascript
  
  index.vue     // main default entry point - www.xxx.com
  contacts.vue  // static route - www.xxx.com/contact
    
  // Anything within brackets [id] (in nuxt 2 _id) will be turned into a dynamic route with parameter id. 
  // Double square brackets [[id]] means that id is optional.
  users/
     index.vue  // static route - www.xxx.com/users/
     [id]/
         index.vue   // dynamic route - www.xxx.com/users/123
         /details
            index.vue  // dynamic nested route - www.xxx.com/users/123/details
               
   // access the parameter from url with: {{  $route.params.id }}
  ```

  <br>
 - **layouts**
    If folder **`layouts/`** it shall contain predefined "frames" used by several components. The `default.vue` layout is read by default and accessed by adding **`<NuxtLayout>`** to your **app.vue**.  Content in the layout will be loaded in the `<slot />`, rather than using a special component (`<nuxt />` as in Nuxt 2).

    We can add several the layouts in the `layouts` folder. This differs a bit in Nuxt 3, as here the other layout i.e `layouts/custm.vue` can be easialy assesed as a prop to  **`<NuxtLayout : name="'custm'">`**

    _If only one layout used than app.vue can be used for this purpose._   
    
    > TODO unsure this apply to Nuxt 3. The style in a layout defined in its <style></style> is unusually the main default style for the whole application (similar to css: [] in nuxt.config.js).
    
    <br>
- **plugins**       
    Topo level files in `plugin/` direcory are loaded at the creation of the vue application. You can use `.server` or `.client` suffix in the file name to load a plugin only on the server or client side. The only argument passed to a plugin is `nuxtApp`. Add a prefixing a number to the file names to decide order of execution i.e `1.my-plugin.ts`.
    >   Plugins are .js programms making it possible to insert functionality that can be used globally in the app such ass global components, filters, event-busses, variables etc
  
  <br>
- **assets**
    The **`assets/`** directory is used to add all the website's assets that the build tool (webpack or Vite) will process. For example `assets/images`, `assets/styles/global` & `assets/styles/modules`. Reached from code with `~` or `@` character `~/assets/images/fav-icon.png` or `@/assets/styles/styles.css`.
    Access those from code TODO
    
<p align=right><a id="nuxt-styling" href="#table-of-content">↩ Back To Top</a></p>

### [**Styling**](#)

Styling in Nuxt works in similar manner as in Vue but with some minor diffences as we do not have any `~/main.js` file accessible into whitch we usually import our global style file `~/assets/global-css/main.css`. In Nuxt this is done through _nuxt.config.js_

Adding global styling:
```java
// nuxt.config.js
----------------
{
  ...
  // adding global CSS for this project
  css: ['@/assets/global-css/main.css'],
  ...
}
```

_Note that `~/assets/global-css/main.css` in turn reptadely `@imports "./_partial_files.css"` to build up one main.js file with all styles that are applied in the whole application._

 `<style scoped>` in **components** have their local isolated styles. 
 
 Non-scoped `<style>` in **`app.vue`** might be used as a place to put global styles used throughout the whole application but its **most common** to handle bundler to build up main.js from assets.
 
 **Each layout** may have its own `<styles>` but then those styles (even though non-scoped) apply only to this particular layout. Therefore for app with multiple layout the method of including global main style from config file is recommended to apply styles that will apply over several layouts.
    
<p align=right><a id="nuxt-cli-nuxi" href="#table-of-content">↩ Back To Top</a></p>

### [**Nuxi commands**](#)
The new CLI for Nuxt 3 is called Nuxi and can be run externally using `npx nuxi <command>`. Can also be installed globally locally  to run faster with **`npm istall nuxi -g`**.

By default a Nuxt 3 project comes without folders like pages/components/composable/layouts/plugins, but Nuxi CLI provides some usefull commands to easialy scraffold those files and folders.

```javascript
> npx nuxi add component TheHeader // generates components/TheHeader.vue
> npx nuxi add composable useData // generates composables/useData.ts
> npx nuxi add layout default // generates layouts/default.vue
> npx nuxi add plugin vuetify.client // generates plugins/vuetify.client.ts
> npx nuxi add api hello // generates server/api/hello.ts
> npx nuxi upgrade -f // upgrades Nuxt 3 to latest vesrsion and removes node_modules and lock files before upgrade.
> nuxi generate // generates folder .output/public/...
```
Read more about nuxi commands [here](https://v3.nuxtjs.org/api/commands/add).


<p align=right><a id="nuxt-vue-instance" href="#table-of-content">↩ Back To Top</a></p>

### [**Nuxt/Vue instances**](#)

We can get access to  instance of nuxtApp with `useRuntimeConfig()` function.
The nuxt instance in turn contain Vua instance context.

 `useRuntimeConfig()` function must be called in certain places.
 You can access runtime config inside a composable like this
```javascript
// ⛔ BAD
const config = useRuntimeConfig()

export const useMyComposable = () => {
  // ✅ GOOD
  // accessing runtime config here
  const config = useRuntimeConfig()
  
  return (
    ...
  )
}
```
<br>

## How things work
<p align=right><a id="nuxt-routes-navigation" href="#table-of-content">↩ Back To Top</a></p>

### [**Routes, Navigation and Nesting**](#)
 
Routes are autogenerated in Nuxt from folders and file structure in **`pages/`** folder. 


  If folder/file name is wrapped in brackets [] then Nuxt creates a dynamic route with a parameter name as stated between brackets. Doublebrackets `[[ ]]` makes the parameter optional. 
  
 [ good link](https://masteringnuxt.com/blog/dynamic-pages-in-nuxt-3)
  
  In runtime route path and parametaers can be accessed:
```
  <template>
    <h1>The to path is: {{ }}</h1>
    <h1>The param is is: {{ }}
  </template>

```  the parameter can be accessed from the template by **`$route.params.id`** or from script with `useRoute().params.id`. Note that Nuxt 3 auto-imports composables and the build in useRoute is autoimported.
  
  **Dynamic routes** 
  In Nuxt 3 we can also mix static and dynamic parts. For example. 
  By naming a folder `pages/user-[id]/index.vue` where `id` is the parameter 123 in url `www.xxx.com/user-123`.  Or `pages/chapter-[slug]/index.vue` where slug is A in url` www.xx.com/chapter-A` 

**Navigation with `<NuxtLink>` or `navigateTo()`**
  Normally in html when navigating we use something like `<a href="/page">load page</a>` and this trigger a new HTTP Get Request to external server to fetch the page. In a Vue app with a router we most of the time don't want to trigger any requests to server, therfore nuxt wraps `<a>` (and `<RouterLink>`) in **`<NuxtLink to="/page">load page</NuxtLink>`**. Due to this nuxt can optimizes loading of links, meaning that each time a `<NuxtLink>` is to be scrolled into browser view then the link conten is prefeteched.
  
   To **navigate programatically** to a route from `<script>` use **`navigateTo(route)`**  (same as `useNuxtApp().$router.push(route)`). Or  from `<template>` just use `$router.push(route)`.

**Nesting**
  Normally when we navigate to a new route it is by default loaded fullscreen in `<NuxtPage>` component. In Nuxt we can nest a _child_ frame in a **nesting parent** component. By doing so the nested child is loaded in `<NuxtPage />` that **must** be defined in nesting parent. To define nesting me must create **both** a nesting parent i.e. i.e. `parent.vue` and a folder `parent/index.vue` (nested child). Frame `<NuxtPage />` in parent then it's where the nested childs content will be loaded.
  Note that if parent do not contain `<NuxtPage />` then no child content will ever be displayed, but parent it still can access nested dynamical paremeters from all nested children!

**Example #1. Standard dynamic routes and navigation**
```javascript
  /pages
   - index.vue     // www.xxx.com
   /products
      - index.vue   // www.xxx.com/users (all products page) 
      /[id]  
        - index.vue  // www.xxx.com/products/123  (one product 123 page)
        - details.vue  //  www.xxx.com/products/123/details  (one product 123 details page)
```

```html
app.vue
--------
<script setup>
  const id = ref('123');
  
  function load(path) {
    navigateTo(path); // same as useNuxtApp().$router.push(path)
  }
</script>

<template>
  <!-- This header is show in for all routes -->
  <header>
    <div>
      <p>Declarative navigation: </p>
      <NuxtLink to="/">Home</NuxtLink>
      <NuxtLink to="/products">All Products</NuxtLink>
      <NuxtLink :to="`/products/${id}`">One Product XXX</NuxtLink>
      <NuxtLink :to="`/products/${id}/details`">One Product XXX Details</NuxtLink>
    </div>
    <div>
      <p>Programmatic navigation: </p>
      <button @click="navigateTo(`/`)">Home</button>
      <button @click="navigateTo(`/products`)">All Products</button>
      <button @click="load(`/products/${id}`)">One Product XXX</button>
      <button @click="$router.push(`/products/${id}/details`)">One Product XXX Details</button>
    </div>
  </header>
  
  <NuxtPage />  <!-- All routes are loaded in this frame -->
   
</template>
```

```html
pages/index.vue <!-- www.xxx.com -->
------------------------------------
<template>
  <h1>Home</h1>
</template>
```

```html
pages/products/index.vue <!-- www.xxx.com/products -->
------------------------------------------------------
<template>
  <h1>All Products</h1>
</template>
```

```html
pages/products/[id]/index.vue <!-- www.xxx.com/products/123 -->
---------------------------------------------------------------
<template>
  <h1>One Product {{ $route.params.id }}</h1>
</template>
```

```html
pages/users/[id]/details.vue <!-- www.xxx.com/users/123/details -->
---------------------------------------------------------------------
<template>
  <h1>One Product {{ $route.params.id }} Details</h1>
</template>
```

**Example #2: Nested pages**
```javascript
  /pages
   ...
   -blogs.vue  // www.xxx.com/blogs (Parent. Same filename as folder name!)
   /blogs
     /[id]
       -index.vue  //  www.xxx.com/blogs/123  (Child)
```

```html
app.vue
--------
<template>
  <h1>Frame loading parent:</h1>
  <NuxtPage /> <!-- loads parent -->
</template>
```

```html
pages/blogs.vue (parent) <!-- www.xxx.com/blogs -->
----------------------------------------------------
<template>
	<!-- Always shown for blog and its children -->
	<header>
		<h1>All blogs</h1>
		<p>id = {{ $route.params.id ?? 'undefined' }}</p>
		<!-- for www.xxx.com/blogs => id = undefined -->
		<!-- for www.xxx.com/blog-123 => id = 123 -->
		<br />
		<p>This page contain nested frame to display nested content.</p>
		<div>Child loads HERE:</div>
	</header>

	<NuxtPage />  <!-- loads child -->
</template>
```

```html
pages/blogs/[id]/index.vue (child) <!-- www.xxx.com/blogs/123 -->
-----------------------------------------------------------------
<template>
   <div style="margin: 20px; border: 1px dotted gray">
      <p>One Blog {{ $route.params.id }} that is displayed in child frame.</p>
   </div>
</template>
```

**Example #3. Mixing dynaminc and static paths**
```javascript
  /pages
   -chapter-[cid]-lesson-[lId].vue  // www.xxx.com/chapter-1-lesson-2 (Parent)
   /chapter-[cid]-lesson-[lId]
      - index.vue   // www.xxx.com/chapter-1-lesson-2  (Child)
```
```html
app.vue
--------
<template>
  <h1>Frame loading parent:</h1>
  <NuxtPage /> <!-- loads parent -->
</template>
```

```html
pages/chapter-[cId]-lesson-[lId].vue (parent) <!-- www.xxx.com/chapter-1-lesson-2 -->
-------------------------------------------------------------------------------------
<template>
	<section>
      <h3>Chapters & Lessons Parent</h3>
      <!-- Defined when route syntax matches exactly -->
      <div>cId = {{ $route.params.cId ?? 'undefined' }}</div>
      <div>lId = {{ $route.params.lId ?? 'undefined' }}</div>
      <!-- For:www.xxx.con/chapter-1-lesson-2 -->
      <!-- cId = 1 --> 
      <!-- lId = 2 -->
    
      <p>Nested child loads in this frame:</p>
	</section>
  
	<NuxtPage /> <!-- loads child -->
</template>
```

```html
pages/[chapter-1-lesson-2]/index.vue (child) <!-- www.xxx.com/chapter-1-lesson-2 -->
------------------------------------------------------------------------------------
<template>
   <div style="border: 1px dotted gray; margin: 20px">
      <p>Child details:</p>
      <div>cId = {{ $route.params.cId ?? 'undefined' }}</div>
      <div>lId = {{ $route.params.lId ?? 'undefined' }}</div>
   </div>
</template>
```

<p align=right><a id="nuxt-route-validation" href="#table-of-content">↩ Back To Top</a></p>

### [**Route validation**](#)

Nuxt offers route validation for components in folder `pages/`. It is executed each time we navigate to a new route and it accepts `route` as an argument. If you return false, and another match can't be found, this will cause a 404 error.

> Note! On server-side it will be called only once (on the first request to the app) and on client-side each time we navigating to this route.
```javascript
<script setup>
  definePageMeta({
    validate: async (route) => { return routeOk(route) ? true : false }
  })
</script>
```
Example of page validation in Nuxt 3
```javascript
<script setup>
  ...
  definePageMeta({
    validate: async (route) => {
      return /^\d+$/.test(route.params.id) // true if id is made up of digits
    }
  });
  ...
</script>
```

<p align=right><a id="nuxt-using-plugins" href="#table-of-content">↩ Back To Top</a></p>

### [**Adding plugins**](#)
Use plugins to add tasks executed at start up that affect your whole project. Nuxt 3 and Nuxt 2 differ in handling plugins. 

Nuxt 3
Create folder `plugins/` and all files there are are executed at creation of vue app,right after main.js internally is run. Vue component can be reached by `nuxtApp.vueApp`.

>  Note! Prefix 1. 2. 3. tells the order to run. Sufix .server/.cliend tell where to run (no sufix run on both).

Nuxt 3. Register plugin just by adding file `plugins/vuetify.ts` :
```javascript
import { createVuetify } from 'vuetify';

export default defineNuxtPlugin((nuxtApp) => {
   const vuetify = createVuetify();
   
   nuxtApp.vueApp.use(vuetify);
   
   console.log(`Registered plugin: vuetify`);
})
```

Nuxt 2. Adding global component by file `plugins/core-components.js`:
```javascript
import Vue from "vue"
import AppButton from "@components/ui/AppButton"

Vue.component('AppButton', AppButton)
```
Nuxt 2. Additionally plugin must be added in `nuxt.config.ts` file
```
...
plugins: [
  '~plugins/core-components.js'
]
```

<p align=right><a id="nuxt-adding-modules" href="#table-of-content">↩ Back To Top</a></p>

### [**Adding modules & postcss**](#)

We can extend nuxt framework's core functionality by adding modues created by others. Once you have _installed_ the module you shall then add it to **module section** of your **`nuxt.config.ts`**.

Here you can find a list of Nuxt 3 compitable **[modules](https://modules.nuxtjs.org/?version=3.x)**.

> Note! If you wish you could add local modules into a folder named `modules/` but it is recommended to access installed modules from **node_modules** directory by using the module package name.

Install modules
```javascript
npm i -D  @nuxtjs/axios  @nuxtjs/tailwindcss  postcss-nested 
```
Add it to `nuxt.config.js` modules section
```javascript
...
  modules: [ 
    '@nuxtjs/axios',  // Using package name from node_modules (recommended)
    ['@nuxtjs/tailwindcss', { ..settings.. }] // Package module with options
    './modules/myModule',  // Load local module (if any)
    ['./modules/myModule', { token: '123' }]   // Local module with options
  ]

  // Postcs plugins are added this way
  postcss: {
    plugins: {
    'postcss-nested': {},
    }
  }

// Now you can use functionality globally in the app
```

**Some usefull modules**
 @pinia/nuxt -  Store for Vue 3
 @vueuse/nuxt - Collection of Vue Composition Utilities for Vue 2 & 3
 @nuxt/image - Image optimizer for Nuxt
 nuxt-lodash - Auto-import lodash modules for Nuxt
 @nuxtjs/axios - http requests support
 @nuxtjs/tailwindcss - styling framwork

<p align=right><a id="building-projects" href="#table-of-content">↩ Back To Top</a></p>

## **Building**
---
Vite is the default builder for Vue 3. Its fast and easy to customize.

## **[Vite](#)**
Vite is the default builder for Vue 3. Its fast and easy to customize.

## **[Minimalistic code](#)**
<p align=right><a id="minimalistic-code" href="#table-of-content">↩ Back To Top</a></p>


To minimize code in Vite use:

```javascript
	vite: {
		build: {
			minify: true /* js minification e (default true, "esbuild" default) */,
			cssMinify: true /* css minification e (default true) */,
		},

		esbuild: {
			/* removes ALL console.xxx() including ALL parameters */
			drop: ["debugger", "console"],
      
      /* Note! With pure we can remove only console log. But it do not remove all parameters if they have logical function */
      // pure: ["console.log"]
		},
	}
```

<br>
<p align=right><a id="ui-frameworks" href="#table-of-content">↩ Back To Top</a></p>

## **UI Frameworks**
---
We can simplify implementing front-end by using predefined UI elements and frameworks with predefined css classes. Using a UI framework with Vue is a great combination, because it enables developers to abstract common components providing a maintainable and productive development process. Most of these components have well written tests and are consistently optimized to be reactive to provide the best performance available.

Here are some popular frameworks to use in a Vue project:

- [Vuetify](https://vuetifyjs.com/en/) (450k [weekly downloads](https://www.npmjs.com/package/vuetify)). Utilise all API in VUE, Material Design and customizable.
- [Bootstrap-Vue](https://bootstrap-vue.org/docs) (350k [weekly downloads](https://www.npmjs.com/package/bootstrap-vue)). Build on popular Bootstrap with javascript/jquery replaced by reactive vue code.
- [Quasar](https://quasar.dev/) (62k [weekly downloads](https://www.npmjs.com/package/quasar)). Build Vue user interfaces for SPA, PWA, SSR, mobile, and desktop. Packs in Cordova, Capacitor, and Electron, which can help you build desktop and mobile experiences without having to learn them individually.
- [Element Plus](https://element-plus.org/en-US/) (31k [weekly downloads](https://www.npmjs.com/package/element-plus)). Brings to Vue 3 a large array of unobtrusive components. Most of what we need to create a very complex application is already made and ready for use.


<p id="vtoc"></p>
<p align=right><a id="vuetify" href="#table-of-content">↩Back To Top</a></p>

## **[Vuetify](#)**
Sektions: [intro](#intro) | [what is vuetify](#what-is-vuetify) | [get started](#get-started) | [about optimization](#about-optimization-and-customization-of-vuetify-3) | [minimize bundle](#minimize-vuetify-3-bundle) | [conclusion](#conclusion)

_[@repo](https://github.com/CMQNordic/vuetify-3-nuxt-3-minimal-optimized-starter) | [Netlify live demo)](https://magical-peony-07c1dc.netlify.app/)._

### [**Intro**](#intro)

In this article I share my knowledge and thoughts about minifing production bundle in a **Nuxt 3 Vuetify 3** projects by purging unused code.  First part is about what Vuetify 3 is and how to add Vuetify to an existing Nuxt 3 project. Then I'll go into some optimization and minification of js, css and html with practical examples. 

_Feel free to check out the final [conslusion](#conclusion)._

### [**What is Vuetify**](#what-is-vuetify)

Vuetify is Vue component library providing pre-made components and **directives** to use in front-end projects. A directive is a reusable chunk of code that can be used within a html element. An example is `v-ripple` directive that animates background. For example `<button v-ripple>click me</button>` adds a background animation when it's pressed. Vuetify comes with many smaller **components** to be used as building blocks of layouts. I.e `<v-app>` (wrapping whole application and applying themes), or `<v-navigation-drawer>` that is a frame sliding in from the side often used as navigation menu on small devices. Some components i.e.`v-date-picker` or `v-data-table` are more complicated.  Designing and coding those components by ourselfs in Vue (or even worse vanilla javascript) would be a difficult and a time consuming task. Additionally Vutify 3 delivers css features similar to Tailwind. You can use utility classes to control the padding (_pa-5_), margin (_mb-10_), text color (_text-red-lighten-2_), background (_bg-orange_), font (_text-body-1_), elevation (_elevation-3_) and more. Many of them with mobile first variations for displays: `xs` (_< 600px_), `sm` (_600px > < 960px_), `md` (_960px > < 1264px_) and `lg` (_1264px > < 1904px_). For example class `text-md-body-1` applies `body-1` font for medium size displays and up.

Vuetify tegether with Nuxt gained a lot of popularity as they significantly speed up building Vue based applications and prototyping. You can build your whole UI with those predefined components and directives, or just add cherry-picked ones to your project as widgets.

**The main concerns** when adding a library like Vuetify to your project is how it affects the size of code delivered from server to then client (a.k.a the **final bundle**).

### [**Get started**](#get-started)

_[@repo](https://github.com/CMQNordic/vuetify-3-nuxt-3-minimal-optimized-starter) | [Netlify live demo (generate)](https://magical-peony-07c1dc.netlify.app/)._

► Use following simple step to create **new Vuetify 3** project on top of **Vue 3**. 
_Official instructions [here](https://next.vuetifyjs.com/en/getting-started/installation/#installation)._

```
npm create vuetify 
```

► Use following 4 steps to **add Vuetify 3** to an **existing Nuxt 3** project: 

**1.** First (if needed) create a new Nuxt 3 project. _Official instructions [here](https://nuxt.com/docs/getting-started/installation#new-project)._
```bash
npx nuxi init  nuxt-3-vuetify-3-minimal-project-starter
```

**2.** Add Vuetify 3 to existing project. _Official instructions [here](https://next.vuetifyjs.com/en/getting-started/installation/#manual-steps)._
```javascript
npm add vuetify@next

// additionally scraffold new /plugins/vuetify.ts file 
npx nuxi add plugin vuetify 
```

**3** Utilize Vuetify by adding following to `plugins/vuetify.ts`
```javascript
import { createVuetify } from 'vuetify';
import 'vuetify/styles'; // pre-build css styles

/* Add all components and directives, for dev & prototyping only. */
import * as components from 'vuetify/components';
import * as directives from 'vuetify/directives';

/* Add build-in icon used internally in various components */
/* Described in https://next.vuetifyjs.com/en/features/icon-fonts/ */
import { mdi, aliases as allAliases } from 'vuetify/iconsets/mdi-svg';
const aliases = allAliases;

export default defineNuxtPlugin((nuxtApp) => {
  
  const vuetify = createVuetify({
    components,
    directives,
    icons: {
      defaultSet: 'mdi',
      aliases,
      sets: { mdi }
    }
  });

  nuxtApp.vueApp.use(vuetify);

  if (!process.server) console.log('❤️ Initialized Vuetify 3', vuetify);
});
```

**4** Instruct Nuxt 3 to transpile Vuetify when building by modifying file `nuxt.config.ts`
```javascript
export default defineNuxtConfig({  
    build: {
        transpile: ['vuetify'],
    }
});
```

**Finally** as an additional step in order to have something visual to test with please add following code (basic vuetify components and styling) to `app.vue` file.
```html
<template>
<div>
  <v-app>
    <v-navigation-drawer temporary v-model="showDrawer" location="right">
      <div class="w-100 text-right">
        <v-btn flat icon="$close" size="x-large" @click="toggle" />
      </div>
      <p class="text-center"><b>I'm the drawer</b></p>
    </v-navigation-drawer>

    <v-app-bar>
      <v-app-bar-nav-icon @click="toggle" />
      <v-toolbar-title>I'm the header</v-toolbar-title>
    </v-app-bar>

    <v-main class="d-flex align-center">
      <v-container>
        <v-sheet elevation="5" class="py-4 text-center">
          <h1 class="text-h5">Built and styled with Vuetify 3</h1>
          <p>Minimized production bundle (70kB in tot)</p>
          <v-btn class="mt-4">press me to ripple</v-btn>
        </v-sheet>
      </v-container>
    </v-main>

    <v-footer app elevation="5">
      <v-row no-gutters justify="center" 
             class="text-overline font-weight-black">
        <p class="my-auto">I'm the footer</p>
        <v-spacer />
<p class="my-auto">See how I was built</p>
        <v-btn icon variant="plain">
          <v-icon icon="$info" color="green-accent-4" />
        </v-btn>
      </v-row>
    </v-footer>
  </v-app>
</div>
</template>

<script setup>
  const showDrawer = ref(false);
  
  const toggle= () => {
		console.log('usedToggle()');
		showDrawer.value = !showDrawer.value;
	};

  /* Redundant unused code to test treeshaking */
  const unusedFunction = () => console.log('unusedFunction');
</script>

<style>
  /* Redundant unused code to test treeshaking */
  .unused-selector-app {
    color: orange;
  }
</style>
```
Now run `npm run dev` and verify the page looks like in the live demo [here](https://magical-peony-07c1dc.netlify.app/).

Now run `npm run generate` followed by `npm run preview`. _Because we have SSR set to true by default, Nuxt 3 will generate a static project in `.output/public/`._
 
🩻**Analazing generated bundle:**
`.output/public/index.html`  14kB (3kB gzipped)
`.output/public/_nuxt/enter.xxx.js`  408kB  (125kB gzipped)
`.output/public/_nuxt/enter.xxx.css` 371kB (51kB gzipped)

The production bundle is **"huge"** for the simplicity of this project 👎

Read further why and what we can do about it.

### [**About optimization and customization of Vuetify 3**](#about-optimization-and-customization-of-vuetify-3)

In initial setup, in file `vuetify.ts`, we add ALL components and directives, import ALL pre-build css style selectors and ALL default icon aliases. It is ok for prototyping but it's not very optimal for production as generated bundle contains too much unused code.

Becouse we here for test purposes impoement whole site in one single file `app.vue` (without any routes) then our statically generated bundle consists of 3 main, easy to analyze parts:

- `.output/public/index.html` (refered to as **html bundle**)

- `.output/public/_nuxt/enter.xxx.js` (refered to as **js bundle**)

- `.output/public/_nuxt/enter.xxx.css` (refered to as **css bundle**)

**What happens to unused js code?**
Search js bundle for phrase: _'unusedFunction'_  -> not found 👍
Search js bundle for phrase: _'toggle'_ -> found 👍
Both of those are defined in the bottom of `app.vue`, one is used the other not. We verify here that Vite by default removes all unused imported or defined javascript when bundling. That's good. 👍  

**What happens to unused icons aliases?**
Search js bundle for phrase: _'mdi-info'_  -> found 👍
Search js bundle for phrase: _'mdi-minus'_ -> found 👎
We find out that all icons are found despite the fact we use only icon aliases: menu ("hamburger" used internally by `<v-app-bar-nav-icon />`), close_ and info icons. That's less good. 👎

**What happens to unused css selectors?**
Search css bundle for phrase: _'unused-selector-app'_  -> found 👎
Search css bundle for phrase: _'bg-red-lighten-4'_  -> found 👎
Search css bundle for phrase: _'my-sm-9'_ -> found 👎
None of the selecors above (first one defined by us in `app.vue` and two other ones added by vuetify) is used nowhere but in the bundle we find ALL selectors from imported `vuetify/styles` and everything from `<styles>` part of `app.vue` file. This despite the fact that our simple project only use some few of those. 👎

> As on dec 2022 Nuxt staticaly generates bundle (npm run generate) and injects `<styles>` part from `app.vue` (scoped or not) into **html head** for **each** generated page. Keep this in mind when you introduce lots of global styles in `app.vue` file, as all those styles will be part of html code for each requested page.

It must be mentioned that removal of unused css is a major issue in many projects and a topic of many discussions. There does not exist any perfect tool for it at the writing moment. In order not to remove too much we must have knowledge of how removal works and we must have good knowledge about the code whe want to purge. 

**Most important to remember** here is that there  might me a lot of unused css code both in html head and subsequently loaded css files. 

So.. how do we securly remove all this unused code? Keep on reading.

Vuetify 3 provides functionality called **treeshaking** that removes unused components from final bundle, or more correctly adds only used ones. You can read official documentation [here](https://next.vuetifyjs.com/en/features/treeshaking/#treeshaking). Unfortunately this treeshaking  optimization aim for javascript bundle. It **does not remove** all unused **css selectors**!

At writing moment I found a plugin named **nuxt-purgecss** to be the best option (still not optimal) to remove unused CSS code from final build bundle.

_I recommend to read this good article on the topic - [How Do You Remove Unused CSS From a Site?](https://css-tricks.com/how-do-you-remove-unused-css-from-a-site/)._

**Finally shortly about customization of Vuetify 3 project**
Vuetify 3 uses SASS to craft all styles for the framework. By default it delivers pre-compiled CSS for all styles, including themes `light` and `dark`. Sometimes it's desired to re-build to manipulate the sass variables to get a feel-and-look for our needs. Some variables in vuetify are used for general styles and themes but unfortunately others are nested and used inside the components (aka. component specific variables).

>  We can customize many SASS variables in Vuetify 3 and rebuild framework styles at build time. Read more about how to do it [here](https://next.vuetifyjs.com/en/features/sass-variables/). By my opinion if possible this **deep variable customisation** should be **avoided**. I do not recommend it as it works right now. There are other more simple and faster ways to overwrite themes, colors, backgrounds, font styles for body and heading etc.

> Note! Enabling **deep variable customisation** will have major impact on dev and build strt-up duratin and might slow down the development significantly if your project uses more than some few components.

_Customization of icons, fonts, styles and themes is a big topic on its own. You can give it a read in my other article just about this topic - [How to customize icons, fonts, styles and themes in Vuetify 3 project](https://github.com/CMQNordic/vuetify-3-nuxt-3-minimal-optimized-starter)._
 
### [**Minimize Vuetify 3 bundle**](#minimize-vuetify-3-bundle)

Let's get our hands dirty.

#### 1. [Vuetify treeshaking](#vuetify-treeshaking)
To auto inculde only used vuetify components and directives (a.k.a [automatic treeshaking](https://next.vuetifyjs.com/en/features/treeshaking/#treeshaking)) we must install required dependency.  
```
npm i -D vite-plugin-vuetify
```

Then we need to modify following in our project:

Remove imports of ALL components and directives from `plugins/vuetify.ts`
```javascript
 ...

/* Add all components and directives, test & prototyping only. */
// REMOVE! import * as components from 'vuetify/components';
// REMOVE! import * as directives from 'vuetify/directives';

...

export default defineNuxtPlugin((nuxtApp) => {
  
  const vuetify = createVuetify({
      // REMOVE! components,  
      // REMOVE! directives,   
      icons: {
          defaultSet: 'mdi',
          aliases,
          sets: { mdi }
      }
  });
  
  ...
});
```   

Add treeshaking istructions for Vite in `nuxt.config.ts`   
```javascript

/* ADD! */
import vuetify from 'vite-plugin-vuetify';

export default defineNuxtConfig({
  ...

  /* ADD! */
  modules: [
    /* Treeshaking: https://next.vuetifyjs.com/en/features/treeshaking/ */
    async (options, nuxt) => {
        nuxt.hooks.hook('vite:extendConfig', (config) => {
          config?.plugins?.push(vuetify());
       });
    }
  ],

  ...
});
```

Thats all. When running the project with `npm run generate` followed by `npm run preview` you will generate static files in `.output/public/` folder. 


🩻**Analazing generated bundle after treeshaking:**
`.output/public/index.html`  14kB (3kB gzipped)
`.output/public/_nuxt/enter.xxx.js` 184kB (67kB gzipped) 
`.output/public/_nuxt/enter.xxx.css` 277kB  (34kB gzipped)

Our bundle is now **smaller** as js bundle was before 408kB (125kB gzipped). Treeshaking did a good job. 👍

#### 2. [Theme and icons Optimization](#theme-and-icons-optimization)
Ee only use 3 icons aliases: _menu_, _close_ and _info_. Loading only the used ones will minimize internal vuetify object in browser (on heap). Have this in mind when you later add more external icons to your project.

**Add only used icons** by changing in `plugins/vuetify.ts`
```javascript
...
import { mdi, aliases as allAliases } from 'vuetify/iconsets/mdi-svg';
/* REMOVE */ // const aliases = allAliases; 

/* ADD */ 
const aliases = {
	/* Only used icon aliases here */
	menu: allAliases.menu,
	close: allAliases.close,
	info: allAliases.info,
};

...
const vuetify = createVuetify({
  icons: {
      defaultSet: 'mdi',
      aliases,
      sets: { mdi },
    },
  }); 
```
Generally we shall always add only used icons to the project and now whole libraries..

What about themes? 
When we analyze the created html bundle notice a large section `<style id="vuetify-theme-stylesheet">`  in the html head. Read more about it in official documentation [here](https://next.vuetifyjs.com/en/features/theme/#implementation). It contains whole configuration for _v-theme--light_, _v-theme--dark_ and lots of generated selectors for each color configuration.

We did not specify any theme to use but by default theme _light_ was applied to everything within the `v-app` block. Therfore in generated `index.html` we can see that many elements use selectors `v-theme--light`. But what if we disable themes in Vuetify totally? Will this section with unnecessary unused theme selectors and variables disapear? Lets try..

We can try to **disable themes** as described [here](https://next.vuetifyjs.com/en/features/theme/#disable-theme) in `plugins/vuetify.ts`: 

```javascript
export default createVuetify({
  /* ADD */ theme: false, 
  ...
})
```

After re-generating no theme selectors are applied anymore on any html elements, good, disabling of themes worked as expected. But... the `<style id="vuetify-theme-stylesheet">` section with unused selectors still remains as before in the head of generated index.html file. 👎

Consider this a bug? Why does Vuetify add thise "disabled" code? Is there any way to remove all this redundand code, or only enable `light` theme and not `dark` to reduce amout of added code in html head? _To be updated when I know, but feel free to comment this in comments!_

##### 3. [Clean out unused CSS](#clean-out-unused-css)


Purge-css is a "dummy" tool. It scans files (html, vue, js ) on locations that we provide to it, and creates a list with selectors it marks as used. Then it analyzes the final generated css code created by our bundler and removes all selectors from it that are not part of its "found-used-selectors" list. For example: In file x.html with `<p class="bg-red">` it will find `bg-red`. In file y.vue with `<v-btn class="elevation-6" elevation='1'>` it find `elevation-6` but NOT `elevation-1` becouse the latter is created with help of a prop. Subsequently `bg-red` and `elevation-6` will not be removed, while `elevation-1` will not exist in the final bundle!

It is essential to instruct purgecss to look in all locations of project where source code used by bundler is located. For Nuxt framework it is predefined by the nuxt-purgecss plugin (default nuxt-purgecss settings [here](https://github.com/Developmint/nuxt-purgecss/blob/main/src/config.ts)) but it becomes tricky with third party librarys like Vuetify where the components and selectors are created by render functions defined deep down in `node_modules/vuetify` folder and some classes might even sometimes be rendered at run time in client. Additionally Vuetify 3 generates some of its its style selectors based on props whic does not help us here.

We need to configure **purgecss** to be sure it **only remove** unused code. So how can we handle it?

I like using Vuetify with Nuxt and it is often for the possibilty of **following little trick**.

First **build a static site** as nuxt provides this in an easy way (css: true + npm run generate). Then ALL html shall be generated with all classes and selectors in `dist` folder.

After first build **provide the content** of the `dist` folder (**copy of it**) to purgecss as a input option "content: <copy-of-dist-path>" and do your final production build. Then purge will have all class names and selector it needs to keep.

First install the nuxt-purgecss plugin 
```bash
npm i -D nuxt-purgecss 
```

Add purgecss module and with settings in `nuxt.config.ts`:
```javascript
...
export default defineNuxtConfig({
  modules: [
    ...

    /* ADD */ 
    /* Remove unused CSS */
    [
      'nuxt-purgecss',
      {
        content: [
          /* Copy of 'dist' from first npm run generate */
          'modules/purgecss/static-generated-html/**/*.html',
        ],
        greedy: [
          /* Generated as runtime, keep all related selectors */
          /v-ripple/,
        ],
      },
    ]
  ]
  
  ...
});
```

After all those modifications run now 'npm run generate', copy content of 'dist' to new folder 'modules/purgecss/static-generated-html', run 'npm run generate' again followed by 'npm run preview'. 
This generate static files in '.output/public/' folder. 

🩻**Analazing generated file after treeshaking and csspurge:**
`.output/public/index.html`  14kB (3kB gzipped)
`.output/public/_nuxt/enter.xxx.js`  184kB  (67kB gzipped)
`.output/public/_nuxt/enter.xxx.css` 14kB  (3.4kB gzipped)

The css is much much smaller than from beggining.👍 
We started with css bundle of **371kB** and ended up with **14kB** (unzipped). Thats a pretty awsome reduction. 😀

### [**CONCLUSION**](#conclusion)
We created an educational project starter using Vuetify 3 on top of Nuxt 3. We did some optimization to remove unused code from js,css and html in the production bundle. Them we deployed the project.

_[@repo](https://github.com/CMQNordic/vuetify-3-nuxt-3-minimal-optimized-starter) | [Netlify live demo (generate)](https://magical-peony-07c1dc.netlify.app/)._

BEFORE OPTIMIZATION
`.output/public/index.html`  14kB (3kB gzipped)
`.output/public/_nuxt/enter.xxx.js`  408kB  (125kB gzipped)
`.output/public/_nuxt/enter.xxx.css` 371kB (51kB gzipped)

AFTER OPTIMIZATION
`.output/public/index.html`  14kB (3kB gzipped)
`.output/public/_nuxt/enter.xxx.js`  184kB  (67kB gzipped)
`.output/public/_nuxt/enter.xxx.css` 14kB  (3.4kB gzipped)

IWe reduced the totla bundle size approx **795kB** to **212kB** (zipped from **179kB** to **73kB**). Around 50kb of the zipped size is pure default and always-included Vue+Nuxt base functionality!
Total reduction of almost 80%.

> I know that index.html contains some more unused theme code. At writing moment I have no solution for that but will update here asap I know.

Additionaly we learned that when building site statically with nuxt and adding styles in `app.vue` file, then those styles are always added to head section of all generted html pages. This is something to have in mind when adding styles there and build static site.

Do you have any comment what more can be done to minimize bundle for this starter even more?

I really hope you did learn something usefull in this article.

✌️

CUSTOMIZATIOIN TO DO
________________________________________


For example file vuetify-overwrite-styles.css
```javascript
/* Overwrite some Vuetify specific styles */
/* Note! Make sure this is imported by bundler after 'vuetify/styles' */

body {
	/* Those styles shall overwrite Vuetify root styles */
	font-family: var(--app-root-font-family);
	font-weight: var(--app-root-font-weight);
	line-height: var(--app-root-line-height);
	font-size: var(--app-root-font-size);

	/* Those colors are overwritten by Vuetify theme and components. */
	background-color: var(--app-root-background-color);
	color: var(--app-root-text-color);
}

h1,
h2,
h3,
h4,
h5,
h6 {
	/* We might desire diffrent font on for headings */
	font-family: var(--app-heading-font-family) !important;
}

/* Overwite following becouse...*/
/* ... internally all typography variabels use font-family roboto and it sucks.*/
.text-h1,
.text-h2,
.text-h3,
.text-h4,
.text-h5,
.text-h6 {
	font-family: var(--app-heading-font-family) !important;
}
.text-subtitle-1,
.text-subtitle-2,
.text-body-1,
.text-body-2,
.text-button,
.text-caption,
.text-overline {
	font-family: inherit !important;
}
```

**[Rebuild sass variables](#)**
In order to overwite vuetify sass setting nested deeply in node_modute/vuetify somwhere, just create an `assets/css/vuetify/settings.scss` file and update `nuxt.config.js` as below:
```javascript
...
  async (options, nuxt) => {
    nuxt.hooks.hook('vite:extendConfig', (config) => {
      config?.plugins?.push(
        vuetify(
          
          {
            /* Use customized scss rules defined in settings.scss */
            styles: { configFile: 'assets/css/vuetify/settings.scss' },
          }
        
        ),
      );
    });
  },
  ...
```

And in file `assets/css/vuetify/settings.scss` add

```javascript
/* 
 * Vuetify variables to modify and rebuild 
 */
@use 'vuetify/settings' with (
	$font-size-root: var(--app-root-font-size),
	$line-height-root: var(--app-root-line-height),
	$body-font-family: var(--app-root-font-family),
	$heading-font-family: var(--app-heading-font-family)
);

```


**►[ Add icons](#)**
Internally, by default, Vuetify 3 supports several free icon-sets such as:
- [Material Design Icons](https://materialdesignicons.com/) 
- [Font Awsome 5](https://fontawesome.com/v5/search) 
  
> Note! it is **recommended** to use **mdi-svg** but internally without any configuration Vuetify 3 by default uses `mdi` icon set!? That is same as `import { mdi, aliases } from 'vuetify/iconsets/mdi'`.

First install icons and necessary helpers to be able pick desired icons only later on from those:
As described on Fontawesome site - [here](https://fontawesome.com/docs/web/use-with/vue/)
See free avaiable Fontawesome icons - [here](https://fontawesome.com/search?o=r&m=free&s=regular%2Csolid)
As descriped on Vuetify site - [here](https://next.vuetifyjs.com/en/features/icon-fonts/).

Install free fontawesome svg icons:
```javascript
// Install free fontawesome svg icons to choose from (solid, regular, brands)
npm i -D @fortawesome/free-solid-svg-icons 
npm i -D @fortawesome/free-brands-svg-icons
npm i -D @fortawesome/free-regular-svg-icons 

// Install SVG core engine for adding selected icons to a library
npm i -D @fortawesome/fontawesome-svg-core

// Install special helper component for Vue 3
npm i -D @fortawesome/vue-fontawesome@latest-3
```

Install free mdi svg icons:
```javascript
npm i -D @mdi/js
```

Changes neede to be done in `plugins/vuetify.ts`:
```javascript
TODO
```
### Done. Now..**use desired icons in your components** 😀
```html
<!-- Prefered way of defining a bouncing Font Awsome icon  -->
<v-icon 
  icon="fas:fas fa-info-circle" 
  size="x-small"
  color='blue' 
  class="fa-bounce"
/>

<v-btn 
  flat 
  icon="mdi:mdi-cursor-default-click" 
  size="large" 
  color="transparent"
/>
```

<p align=right><a id="vuetify-layouts" href="#vtoc">↩Back To Top</a></p>

## **▶ [Layouts](#)**
Read more about layouts: [Nuxt 3 layouts](https://next.vuetifyjs.com/en/features/application-layout/) and [Nuxt 2 layouts](https://vuetifyjs.com/en/features/layouts/)

Order of layout components reserve space in order that they appear in your markup (import for i.e. `v-app-bar` <-> `v-navigation-drawer`). 
 
Following components are compatible with the layout system:

- **[v-app](https://next.vuetifyjs.com/en/components/app-bars/) / v-layout**
  Root layout application wrapper, replacement for the default vue entrypoint `<div id="app">`, defaults to a minimum height of 100vh. V-layout is an alternative root layout wrapper, replacement for the default vue entrypoint, defaults to size of parent. Theming can not be allplied but it works similar as v-app.
  
- **[v-app-bar](https://next.vuetifyjs.com/en/components/app-bars/) / [v-system-bar](https://next.vuetifyjs.com/en/components/system-bars/) / [v-toolbar](https://next.vuetifyjs.com/en/components/toolbars/)**
  v-app-bar is an replacement for the `<header>` html element and is the primary source of your applications navigation. [v-system-bar](https://next.vuetifyjs.com/en/components/system-bars/) looks like the Android system bar, small for icons and small text. `V-toolbar` is a slimmer version of app-bar aimed to use in navigation/top bar for various GUI elements. Are are resizing icons automaticall, adding scroll functionality as well apply thems to all children elements.
  
- **[v-navigation-drawer](https://next.vuetifyjs.com/en/components/navigation-drawers/)**
  Replacement for the `<nav>` html element. When `temporary` it is overlating other layouts and visibilty can be controlled by `v-model="true/false"`. Can be located with `location="left/right"`. If defineed before `<v-app-bar>` then overlays it, otherwise if defined after itsis under it.
  
- v-footer / **[v-bottom-navigation](https://next.vuetifyjs.com/en/components/bottom-navigation/#bottom-navigation)**
-  Replacement for the `<footer>` html element and is the root of your applications footer. 

- **[v-main](https://next.vuetifyjs.com/en/api/v-main/)** 
  Replacement for the `<main>` html element and is the root of your applications content. Resizes to (fills out) remaning space when used in `v-app`.

Here `v-layout` can be exchanged for `v-app`
```html
<v-container class="bg-blue">
    <v-layout class="bg-grey">
      
      <!-- Set first to overlap bar -->
      <v-navigation-drawer location="left" color="white" temporary v-model="drawer">
          <!-- buttons here must be styled -->
          <v-btn block variant="text">Link 1</v-btn>
          <v-btn block variant="text">Link 2</v-btn>
          <v-btn block variant="text">Link 3</v-btn>
      </v-navigation-drawer>

      <v-app-bar density="compact" color="transparent">
        
          <v-toolbar-title> Toolbar title </v-toolbar-title>

          <v-toolbar-items class="d-none d-md-flex">
            <!-- buttons here get predefined styling -->
            <v-btn>Link 1</v-btn>
            <v-btn>Link 2</v-btn>
            <v-btn @click.stop="drawer = !drawer">
                MORE 
                <v-icon icon="fas fa-angle-double-right" size="small" class="pt-1" />
            </v-btn>
          </v-toolbar-items>

          <v-app-bar-nav-icon class="d-md-none" @click.stop="drawer = !drawer" />
      </v-app-bar>

      <v-main>
          <v-card color="transparent" height="200px" class="d-flex align-center text-center">
            <v-card-text>About page </v-card-text>
          </v-card>
      </v-main>
    </v-layout>
</v-container>
```
<p align=right><a id="vuetify-layouts" href="#vtoc">↩Back To Top</a></p>

#### **► [Screens](#)**

## _0_ <- `xs` -> _600_ <- `sm` -> _960_ <- `md` -> _1264_ <- `lg` -> _1904_ <- `xl`

<p align=right><a id="vuetify" href="#table-of-content">↩Back To Top</a></p>

### **[Vuetify](#)**

How to get install tailwind with nuxt 3 - [here](https://stackoverflow.com/questions/70302520/nuxtjs-v3-and-tailwindcss-v3-postcss8-not-compatible).

<br><p align=right><a id="bootstrap" href="#table-of-content">↩Back To Top</a></p>

### [**Bootstrap**]()

> Note! Bootstrap 5 no longer uses jQuery and no longer requires a library like `bootstrap-vue` therfore in Vue 3 we can integrate Bootstrap 5 directly. Install bootstrap as you would any other module in the Vue project. Next, add the Bootstrap CSS and JS components to the Vue projects entrypoint (usually `main.js`).

```java
> npm install bootstrap

____________________________ main.js ___________________________
import "bootstrap/dist/css/bootstrap.min.css"
import "bootstrap"
```

But bootstrap-vue add extra functionality as it wraps the elemants in vue components and it easier to distinguish parts of code. Still it is totally ok to use Boostrap 5 directly in vue.

**Navigation bar**

```html
<!-- Navigation flex row with items -->
<nav class="navbar">
  <!-- Brand Icon & Text -->
  <!-- First flex item: Max to left -->
  <a class="navbar-brand"><img />Branding Text</a>

  <!-- Toggler hamburger button -->
  <!-- Second flex item: Max to right  -->
  <button class="navbar-toggler" />

  <!-- Top/Mobile navigation (controlled by toggler) -->
  <!-- This gets "flex-basis: 100%" - why it's always on new row!!! -->
  <ul class="navbar-nav">
    <li class="nav-item" />
    <li class="nav-item" />
  </ul>
</nav>
```

<br><p id="nuxt"></p>






