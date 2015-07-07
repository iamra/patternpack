# Pattern Pack
PatternPack is designed to accelerate the creation of web application pattern libraries. When configured properly it will generate a static site pattern library.  The [patternpack-example-library] demonstrates exactly how to do this and is a good place to learn how to use PatternPack.

## Getting Started
This plugin requires Grunt `~0.4.0`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install patternpack --save-dev
```

Once the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('patternpack');
```

## PatternPack Task
_Run this task with the `grunt patternpack` command._

Task options may be specified according to the grunt [Configuring tasks](http://gruntjs.com/configuring-tasks) guide.  However the files and targets are not used at this time.

### Options

#### src
Type: `string`  
Default: `./src`

The path at which the patterns can be located.  This is base path to all the pattern in the pattern library.

#### build
Type: `string`  
Default: `./html`

The path at which the patterns library will be generated.  This is the base path where the working pattern library will be created, and can be reviewed during development.

#### release
Type: `string`  
Default: `./release`

The path at which the pattern library will published.  This is the base path where the released pattern library assets can be found by consuming applications.

#### theme
Type: `string`
Default: `./node_modules/patternpack-example-theme`

The path at which the patternpack theme can be located.  Custom themes can be npm modules or simply files that exist within a pattern library.  By default patternpack is configured to use the [patternpack-example-theme]

#### publish.library
Type: `boolean`
Default: `true`

Indicates whether a full pattern library will be generated.

#### publish.library
Type: `boolean`  
Defult: `false`

Indicates whether standalone patterns will be generated.  

_This option can be useful if you would like to integrate patterns directly into another application.  For example when the patterns includes components or interations that are only available in the context of the application (such as AngularJS directives)._

#### patternStructure
Type: `Array`  
Default:
```js
[
  { "name": "Atoms", "path": "atoms" },
  { "name": "Molecules", "path": "molecules" },
  { "name": "Pages", "path": "pages" }
]
```

Specifies the hierarchy used to organize patterns.  The default configuration represents the atomic design hierarch, but this can be overriden with any preferred structure.

>`name`: The friendly name that is displayed in the pattern library.  
>`path`: The location at which the patterns can be found.  This path is relative to the `src` path.

_The order of the items in the Array determines the order in which they will be displayed in the pattern library._


### Usage Examples

#### Basic usage
This is an example of the most minimal configuration possible for PatternPack.  If the default conventions are followed, minimal grunt configuration is required.

```js
patternpack: {
  options: {
    assets: './src/assets'
  },
  run: {},
  build: {
    task: 'build'
  },
  release: {
    task: 'release'
  }
}
```

#### Custom file locations
This example demonstrates how to configure PatternPack to point to different file locations for the patterns, and then output the resulting pattern library to a custom location.

```js
patternpack: {
  options: {
    src: './path/to/patterns',
    build: './path/to/pattern-library',
    release: './path/to/release'
  }
}
```

#### Custom pattern structure
This example illustrates how to configure PatternPack to understand a differnt style of pattern hierarchy.  In this case `components`, `modules`, `templates` and `pages`.

```js
[
  { "name": "Components", "path": "components" },
  { "name": "Modules", "path": "modules" },
  { "name": "Templates", "path": "tmpl" }
  { "name": "Pages", "path": "pages" }
]
```

In this configuration PatterPack would look for patterns in:
```
src/
  components
  modules
  tmpl
  pages
```

[patternpack-example-library]:(https://github.com/patternpack/patternpack-example-library)
[patternpack-example-theme]:(https://github.com/patternpack/patternpack-example-theme)
