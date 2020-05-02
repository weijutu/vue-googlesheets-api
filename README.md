# 使用 Vue 前端語法讀取 Google Sheets 試算表

[教學說明](http://weijutu.github.io/2019/03/06/vuejs/vuejs-googlesheets-api/)


## 修改 src/main.js

請前往 `src/main.js` 內容修改 apiKey, clientId 值

```
const apiConfig = {
  apiKey: "your apiKey",
  clientId: "{your clientId}.apps.googleusercontent.com",
  discoveryDocs: ["https://sheets.googleapis.com/$discovery/rest?version=v4"],
  scope: "https://www.googleapis.com/auth/spreadsheets" // See, edit, create, and delete your spreadsheets in Google Drive
  // see all available scopes here: https://developers.google.com/identity/protocols/googlescopes'
};
```

## 安裝方法

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```
