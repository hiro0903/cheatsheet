使用ESLint撿查Coding Style並確保語法正確:

```
$ npm install -g eslint
```

project 中套用airbnb的規則方便使用
```
$ npm install --save-dev eslint-config-airbnb
```

在project root 中配置.eslintrc
```json
{
    "extends": "eslint-config-airbnb"
}
```



