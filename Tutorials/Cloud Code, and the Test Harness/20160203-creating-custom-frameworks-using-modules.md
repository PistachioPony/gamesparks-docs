### Modules

Modules allow you to create your own libraries of JavaScript that can be included within other scripts. This allows you to separate common functionality that needs to be shared between scripts into a single module that can be included. To include a module within your script use the require method as follow :

```
    require("MODULE_SHORT_CODE");
```

Using require, you can load a module into the current execution context. This is not common.js require, but a more basic inclusion pattern, where the loaded module is inlined within the current script. If you have circular reference between modules, the require method will only load a single module once per require invocation. This is to protect from infinite loops and stack overflows. You can conditionally require modules based on input parameters etc to have a single script that can perform multiple tasks without having a large script:

```    
    if(something) {
        require("MODULE_SHORT_CODE_1");
    } else {
        require("MODULE_SHORT_CODE_2");
    }
```

To create a new module click the Create New Module button, then enter a short code to uniquely identify this module script.

![](img\CloudCode\4.jpg)
