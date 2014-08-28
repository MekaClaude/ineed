![logo](https://raw.github.com/inikulin/iwant/master/logo.png)  

[![Build Status](http://img.shields.io/travis/inikulin/iwant.svg?style=flat-square)](https://travis-ci.org/inikulin/iwant)

HTML-page scraping and reprocessing. The easy way.

`iwant` allows you collect useful data from web pages using simple and fancy API. Let's collect all images, hyperlinks, script and stylesheet URLs from www.google.com:

```js

var iwant = require('iwant');

iwant.collect
    .images
    .scripts
    .stylesheets
    .hyperlinks
    .from('http://www.google.com', function(err, response, results) {
        console.log(results);
    });

```

Also, it can be used to build HTML-reprocessing pipelines with elegance. Let's render all `<style>` tags with [stylus](https://github.com/learnboost/stylus) and convert all texts from Markdown to HTML using [marked](https://github.com/chjj/marked) then assemble results back to HTML: 

```js
var iwant = require('iwant'),
    stylus = require('stylus'),
    marked = require('marked'),
    html = '!!!TODO!!!';
  
var resultHtml = iwant.reprocess.cssCode(stylus).texts(marked).fromHtml(html);

console.log(processedHtml);
```

`iwant` provides a wide variety of built-in collectors and reprocessors which covers most common use cases. However, if you feel that something is missing, then you can easily extend it with custom plugins.   
