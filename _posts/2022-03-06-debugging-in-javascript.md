---
title: Debugging JavaScript
author: Adithya Vijay
date: 2022-03-06 21:00:00 +0550
categories: [Blogging, programming]
tags: [development programming debugging javascript]     # TAG names should always be lowercase
---

### Introduction
We debug our code irrespective of the language it is written in, so that we can find and fix errors. Fixing bugs is a very good learning path to dive deep into something and figure out why it occurs and how things operate under the hood.

### Debugging in JavaScript
Test Code with error:
Expected output is 37.5

```
(function (app) {
    'use strict';
    app.divide = function (x, y) {
        return x / y;
    };
    app.complicatedFormula = function (x) {
        let result = x * 3 + 2;
        x += 4;
        result += this.divide(result, 2);
        return result;
    }
})(window.app = window.app || {});

console.log(app.complicatedFormula(23));
```

1. **Basic Debugging** - (Using console log, error, and warning)

```
console.error('This is an error');
console.warn('This is an warning');
```

We can use log statements and log the values at different steps and thereby find the issue. Using console log in the above test code is demonstrated below.

```
(function (app) {
    'use strict';
    app.divide = function (x, y) {
        console.log(x/y);
        return x / y;
    };
    app.complicatedFormula = function (x) {
        let result = x * 3 + 2;
        result += 4;
        console.log(result);
        result = this.divide(result, 2);
        console.log(result);
        return result;
    }
})(window.app = window.app || {});

console.log(app.complicatedFormula(23));
```

2. **Using chrome devtools**

We can use the source tab in google chrome dev tools to add breakpoints to the JavaScript file. If we add breakpoint at a certain line, the debugger will pause the website and allow us to inspect the code. We can go line by line and inspect the values of each variables and thereby find the issue/error.

3. **Debugging in VSCode**

To attach the debugger to VSCode:
- Goto the Run and Debug tab in VSCode
- Click on Create a launch.json file
- In environment select your browser (chrome in our case)
This will create a new folder .vscode in the root folder with a file named launch.json. The file will be in the following format

```
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "pwa-chrome",
            "request": "launch",
            "name": "Debug on Chrome",
            "url": "http://localhost:8080",
            "webRoot": "${workspaceFolder}"
        }
    ]
}
```

- Click on the run and debug option, this will pause the website and take you to point where we have added a breakpoint in vscode.
We can also use the debug console in vscode to observe the values similar to how it's seen in the chrome console tab.