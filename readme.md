# docxtemplater v1

[![Build Status](https://travis-ci.org/edi9999/docxtemplater.svg?branch=master&style=flat)](https://travis-ci.org/edi9999/docxtemplater)
[![Download count](http://img.shields.io/npm/dm/docxtemplater.svg?style=flat)](https://www.npmjs.org/package/docxtemplater)
[![Current tag](http://img.shields.io/npm/v/docxtemplater.svg?style=flat)](https://www.npmjs.org/package/docxtemplater)
[![Issues closed](http://issuestats.com/github/edi9999/docxtemplater/badge/issue?style=flat)](http://issuestats.com/github/edi9999/docxtemplater)

![docxtemplater logo](https://raw.githubusercontent.com/edi9999/docxtemplater/master/logo_small.png)

**docxtemplater** is a library to generate docx documents from a docx template.
It can replace tags by their values and replace images with other images. It is very user oriented as users can without a lot of programming knowledge create their first template and automatically change variables in it.

## Features

[Demo Site](http://javascript-ninja.fr/docxtemplater/v1/examples/demo.html)

- <a href="http://javascript-ninja.fr/docxtemplater/v1/examples/demo.html#variables">Replace a {placeholder} by a value</a>
- <a href="http://javascript-ninja.fr/docxtemplater/v1/examples/demo.html#loops">Use loops: {#users} {name} {/users} </a>
- <a href="http://javascript-ninja.fr/docxtemplater/v1/examples/demo.html#tables">Use loops in tables to generate columns</a>
- Use loops in tables to generate columns
- <a href="http://javascript-ninja.fr/docxtemplater/v1/examples/demo.html#parsing">Use expressions {product.unit_price*product.count} with angular Parsing</a>
- <a href="http://javascript-ninja.fr/docxtemplater/v1/examples/demo.html#images">Replace {%images}</a>
- <a href="http://javascript-ninja.fr/docxtemplater/v1/examples/demo.html#rawxml">Insert custom XML {@rawXml} (for formatted text for example)</a>


## Quickstart

Installation: `npm install docxtemplater`

    fs=require(‘fs’)
    Docxtemplater=require('docxtemplater');

    //Load the docx file as a binary
    content=fs
        .readFileSync(__dirname+"/input.docx","binary")

    doc=new Docxtemplater(content);

    //set the templateVariables
    doc.setData({
        "first_name":"Hipp",
        "last_name":"Edgar",
        "phone":"0652455478",
        "description":"New Website"
    });

    //apply them (replace all occurences of {first_name} by Hipp, ...)
    doc.render();

    var buf = doc.getZip()
                 .generate({type:"nodebuffer"});

    fs.writeFileSync(__dirname+"/output.docx",buf);

You can download [input.docx](https://github.com/edi9999/docxtemplater/raw/master/examples/tagExample.docx) and put it in the same folder than your script.

## Documentation

The full documentation of v1 can be found on [read the docs](http://docxtemplater.readthedocs.org/en/latest/).

See [upgrade.md](upgrade.md) for information about how to migrate from 0.7

docxtemplater@1.0.0 can be installed with: `npm install docxtemplater`

## Similar libraries

They are a few similar libraries that work with docx, here’s a list of those I know a bit about:

 * docx4j :JAVA, this is probably the biggest docx library out there. They is no built in templating engine, but you can generate your docx yourself programmatically
 * docx.js: Javascript in the browser, you can create (not modify) your docx from scratch, but only do very simple things such as adding non formatted text

# Modules

Functionality can be added with modules. They is yet no doc for the modules because it is not completely mature yet, but you can open an issue if you have any question about it.
I have already created one module that can add images using the syntax: `{%image}`, which is documented here: https://github.com/edi9999/docxtemplater-image-module
