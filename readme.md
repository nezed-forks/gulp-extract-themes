Gulp Group Concat
-----------------

Concatenates and filters groups of files into a smaller number of files.

[![Build Status](https://travis-ci.org/TakenPilot/gulp-group-concat.svg?branch=master)](https://travis-ci.org/TakenPilot/gulp-group-concat)

[![Code Climate](https://codeclimate.com/github/TakenPilot/gulp-group-concat/badges/gpa.svg)](https://codeclimate.com/github/TakenPilot/gulp-group-concat)

[![Coverage Status](https://img.shields.io/coveralls/TakenPilot/gulp-group-concat.svg)](https://coveralls.io/r/TakenPilot/gulp-group-concat?branch=master)

[![Dependencies](https://david-dm.org/TakenPilot/gulp-group-concat.svg?style=flat)](https://david-dm.org/TakenPilot/gulp-group-concat.svg?style=flat)

[![NPM version](https://badge.fury.io/js/gulp-group-concat.svg)](http://badge.fury.io/js/gulp-group-concat)

##Concatenates files together that match minimatch-styled file globs.

###Example:

Groups all files into `final.inline.js` and `final.test.js`.

```JavaScript
var gulp = require('gulp'),
  groupConcat = require('group-concat');

gulp.src('**/*.js')
  .pipe(groupConcat({
    'final.inline.js': '**/*.inline.js',
    'final.test.js': '**/*.test.js'
  }))
  .pipe(gulp.dest('dest'));
```

##Duplicates files that match more than one file glob.

###Example:

Put components into `components.js` but everything into `all.js`.

```JavaScript
var gulp = require('gulp'),
  groupConcat = require('group-concat');

gulp.src('**/*.js')
  .pipe(groupConcat({
    'components.js': '**/*.component.js',
    'all.js': '**/*.js'
  }))
  .pipe(gulp.dest('dest'));
```

##Filters files that do not match any file globs.

###Example:

Include all files that are not tests into `no-tests.js`.

```JavaScript
var gulp = require('gulp'),
  groupConcat = require('group-concat');

gulp.src('**/*.js')
  .pipe(groupConcat({
    'no-tests.js': '!**/*.test.js'
  }))
  .pipe(gulp.dest('dest'));
```

##Supports source-maps

Source-maps are duplicated, filtered, and concatenated as expects.

###Example with CSS

```JavaScript
var gulp = require('gulp'),
  groupConcat = require('group-concat'),
  sourcemaps = require('gulp-sourcemaps'),
  please = require('gulp-pleeease');

gulp.src('./test/fixtures/*.css')
  .pipe(sourcemaps.init())
  .pipe(please()) //or anything else that supports gulp-sourcemaps
  .pipe(groupConcat({
    'final.inline.css': '**/*.inline.css',
    'final.css': '**/*.css'
  }))
  .pipe(sourcemaps.write('.'))
  .pipe(gulp.dest('dest'));
```

##Install

```Sh

npm install gulp-group-concat

```

##Running Tests

To run the basic tests, just run `mocha` normally.

This assumes you've already installed the local npm packages with `npm install`.