# Babel Native Class Issue

Babel fails to create code that is able to extend native classes (which could be published as an external module and consumed by our module)

``` shell
git clone https://github.com/balupton/babel-extend-native-class-issue.git
cd babel-extend-native-class-issue

npm install

node ./extend-native-class.js
babel --presets es2015 ./extend-native-class.js > ./extend-native-class-via-babel.js
node ./extend-native-class-via-babel.js
```

Known affected versions:

```
"babel-cli": "6.7.7",
"babel-preset-es2015": "6.6.0"
```

[typechecker](https://github.com/bevry/typechecker) includes tests for native classes - [their code](https://github.com/bevry/typechecker/blob/b17d0762514718cead054b5f7908f4c537e9a2c8/source/index.js#L65-L73)

Issue: https://phabricator.babeljs.io/T7328
