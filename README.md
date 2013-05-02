# grunt-kissy-template

> html to kissy module

## Getting Started
This plugin requires Grunt `~0.4.1`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-kissy-template --save-dev
```

One the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-kissy-template');
```

## The "ktpl" task

### Overview
In your project's Gruntfile, add a section named `ktpl` to the data object passed into `grunt.initConfig()`.

```js
grunt.initConfig({
  ktpl: {
    options: {
      // Task-specific options go here.
    },
    your_target: {
      // Target-specific file lists and/or options go here.
    },
  },
})
```

### Options
- minify false 开启 HTML 压缩，请保证模板内容为合法HTML
- minifyOption.removeComments: true
- minifyOption.removeCommentsFromCDATA: true
- minifyOption.removeCDATASectionsFromCDATA: true
- minifyOption.collapseWhitespace: true
- minifyOption.collapseBooleanAttributes: true
- minifyOption.removeAttributeQuotes: true
- minifyOption.removeEmptyAttributes: true

### Usage Examples

#### dynamic mapping
```js
ktpl: {
        page: {
            files: [{
                expand: true,
                cwd: '<%= pageBase %>',
                dest: '<%= pageBase %>',
                src: '**/*-tpl.html',
                ext: '.js'
            }]
        }
    },
```

#### Simple
This config will convert all -tpl.html files in directory src to -tpl.js file

```js
grunt.initConfig({
  ktpl: {
    all: {
      src: 'src/**/*-tpl.html'
    },
  },
})
```


#### Config html mini options

```js
grunt.initConfig({
  ktpl: {
    options: {
      minify: {
        removeComments: true,
        removeCommentsFromCDATA: true,
        removeCDATASectionsFromCDATA: true,
        collapseWhitespace: true,
        collapseBooleanAttributes: true,
        removeAttributeQuotes: true,
        removeEmptyAttributes: true
      }
    },
    page: {
      src: 'foo-tpl.html',
      dest: 'foo-tpl.js'
    },
  },
})
```

## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality. Lint and test your code using [Grunt](http://gruntjs.com/).

## Release History
v0.1.2 add minify option and html minify was off by default
