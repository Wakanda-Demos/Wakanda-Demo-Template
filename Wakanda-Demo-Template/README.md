# Wakanda Demo Template


## About

This Project template use a basic **Country / Company / Employee** Model and a fake **data generator** as used in [play.wakanda.org](http://play.wakanda.org) and [NG-Wakanda-Pack](ng-wakanda-pack.waktest.com)

## Model

The Model has been created using the **Model Designer** in **unified model mode**


## Startup

This template contains a **bootStraps** folder in which **initApp.js** is set as an **Active Bootstrap File** which is then executed automatically by default on project startup and:

* set a `PRODUCTION_MODE` flag into the memory `application.storage` (to false by default)
* execute **initApp-sharedWorker.js** in a `SharedWorker` (from the **Workers** folder)

The ShareWorker allows to execute more heavy actions without blocking the startup. What it does in this project is mainly:

* check if data related to the demo Model already exist in the database
* generate automatically some fake data if none exits based on a `COUNT_EMPLOYEES_TO_CREATE` default value
* make queries to load the fake data in memory cache


## Data Generator

### Manual generation

The easiest way to manually create fake data it to go to the **Tools** folder and **run** the **createFakeData.js** file from the **Wakanda Code editor**.

As in the init SharedWorker, you can easily change the `COUNT_EMPLOYEES_TO_CREATE` default value

### CommonJS module

As it can be seen in **Tools/createFakeData.js**, the fake data generator is a CommonJS module that can be called by `require()`

```javascript
var generator = require("fakedata/generator");
```

It's source code and fake data are in the **Modules/fakedata** folder

#### buildFakeData(nbEmployees, options)

It exposes a simple `buildFakeData(nbEmployees, options)` method

```javascript
generator.buildFakeData(nbEmployees, {log:false});```
##### options
the options can be:
* `remove` (default: true): remove already existing fake data. Set to false to append more fake data instead* `log` (default: false): log step details during data generation* `errorLog` (default: true): log errors even if the log option is not active
