### step 0

`npm install -g gulp`

以便可以手動執行gulp, 之後任意目錄都可以執行gulp, 會自動抓取當前位置的gulpfile


### step 1

建立新專案

`npm init`

```json
{
  "name": "practice",
  "version": "0.0.1",
  "description": "我要練習!!!!",
  "main": "src/index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [
    "practice"
  ],
  "author": "Chris Chu",
  "license": "MIT"
}
```
scripts中可以加入 `"start" : "gulp"`, 則執行npm start就會run gulp

### step 2

本地目錄裡面安裝一次, 方便寫入package.json

`npm install gulp --save`

```json
  "dependencies": {
    "gulp": "^3.9.0"
  }
```

