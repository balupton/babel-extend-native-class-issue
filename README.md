# Babel Native Class Issue

Babel fails to create code that is able to extend native classes (which could be published as an external module and consumed by our module)

Issue: https://phabricator.babeljs.io/T7328

Reproduction instructions:

``` shell
git clone https://github.com/balupton/babel-extend-native-class-issue.git
cd babel-extend-native-class-issue

npm install

node ./extend-native-class.js
babel --presets es2015 ./extend-native-class.js > ./extend-native-class-via-babel.js
node ./extend-native-class-via-babel.js
```

Error:

```
$ node ./extend-native-class-via-babel.js
/Users/balupton/Projects/edition-stuff/babel-class-issue/extend-native-class-via-babel.js:17
    return _possibleConstructorReturn(this, Object.getPrototypeOf(Employee).apply(this, arguments));
                                                                            ^

TypeError: Class constructor Person cannot be invoked without 'new'
    at new Employee (/Users/balupton/Projects/edition-stuff/babel-class-issue/extend-native-class-via-babel.js:17:77)
    at Object.<anonymous> (/Users/balupton/Projects/edition-stuff/babel-class-issue/extend-native-class-via-babel.js:23:16)
    at Module._compile (module.js:541:32)
    at Object.Module._extensions..js (module.js:550:10)
    at Module.load (module.js:456:32)
    at tryModuleLoad (module.js:415:12)
    at Function.Module._load (module.js:407:3)
    at Function.Module.runMain (module.js:575:10)
    at startup (node.js:159:18)
    at node.js:444:3
```

Known affected versions:

```
"babel-cli": "6.7.7",
"babel-preset-es2015": "6.6.0"
```

[typechecker](https://github.com/bevry/typechecker) includes tests for native classes - [their code](https://github.com/bevry/typechecker/blob/b17d0762514718cead054b5f7908f4c537e9a2c8/source/index.js#L65-L73)
