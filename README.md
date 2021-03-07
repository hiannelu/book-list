# Book List


## Project setup
```
npm install
```

## Run server
```
npm run serve
```

## 專案架構
- 父元件：Book.vue (網址: `/books`)
- 子元件：BookDetail.vue (網址: `/books/:bookId`)


### Book.vue
- 使用 API GET 介接出所有卡片元素，`querySelectorAll` ＆ `forEach` 方式設定 `animationDuration` 變數
- 使用 `MouseEvent` 偵測拖曳動作，`translate` 設定列表左右移動功能
- 當螢幕寬度 <= 546px，列表中的元素會自動往下排列
- 被點擊卡片會以 `classList.add` 方式被標示，並顯示 `rotate`, `scale` 等特效
- 根據所點擊的卡片 ID，切換到網址 `/books/:bookId`
- 使用 `<router-link>` 方式讀取 BookDetail 並顯示在 Book 下方


### BookDetail.vue
- 使用 API PATCH 更新 server 資料，輸入值非正數則不動作，回傳 200 後以 `animation` 方式跳出訊息並消失


## 問題 & 解決方式
- `@keyframes` 在 `<style scoped>` 中因解析關係無法被使用，可移除 scoped  
- `<router-view>` 只會初始化一次，無法使用 `appendChild` 方式載入，使用 `v-if` 根據路徑不同而載入不同元件的位置
- `querySelector` API 介接的資料回傳 `null`，使用 `then`
- `forEach` 中的 `this` 回傳 `undefined`，可在迴圈外層宣告 `this`
- `mouseup` 事件被多次觸發，可用 `@click.once`


