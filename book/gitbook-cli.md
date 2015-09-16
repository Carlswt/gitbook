# GitBook 終端機指令

> 這章主要針對 `gitbook-cli` 在本地端的使用，一般讀者可以跳過。

不管使用雲端或本地的編輯器，或使用自己喜歡的文字編輯器（例如 Sublime Text）、再推送到遠端倉儲，都是使用 gitbook.com 的雲端「製書程序」。這有一個小問題：當你還在「草稿分支」的時候，就看不到最終成果了，哪一種格式都一樣。如果你想要在本地、在任何分支，都輕鬆的看到最終的網頁書籍呈現，或是製作 ePub, Mobi 與 PDF 預先測試，就得使用 GitBook 提供的終端機指令工具才行。

首先你必須已經安裝好 `Node`、`NPM` 以及 `Calibre`，在 Mac 上測試過的版本為：

- Node v0.10.40 （使用 NVM 安裝）
- NPM 2.14.3
- Calibre 2.38.0

> 製書使用 Calibre 內部的一支 `ebook-convert` 程式，請根據[安裝電子書轉製程式](../build/ebookconvert.md)這章的方式建立鏈結，如果你的 Calibre 不是安裝在個人家目錄下的 `Applications`，要改對應到 `/Applications/calibre.app/Contents/MacOS/ebook-convert` 這個位置。最後使用 `ebook-convert --version` 確認一下，必須跳出正確的版本號，GitBook 終端機指令才能順利執行。

### 安裝

```
$ npm install -g gitbook-cli
```

將終端機指令工具安裝到 npm 的全域位置，目前 GitBook CLI 只支援 `2.0.0` 以上的 GitBook 版本。

- `gitbook versions` 顯示本地目前可用的 GitBook 版本。
- `gitbook versions:available` 顯示有哪些可以安裝的版本。
- `gitbook versions:install latest` 安裝最新版。
- `gitbook versions:install 2.3.3` 安裝特定版本。
- `gitbook versions:uninstall 2.3.3` 移除特定版本。
- `gitbook --version` 顯示 GitBook CLI 的版本號。

本地系統上已經有了最新的 GitBook，Calibre 轉製程式也備妥，接下來就可以製書了。

### 製作網頁版本

在終端機介面切換到書籍專案目錄，先輸入 `gitbook install`，會自動安裝必要與專案指定的外掛。

輸入 `gitbook serve ./`，會在本地的 `http://localhost:4000` 開啟一個網站服務，用瀏覽器打開就是網頁版的電子書。你可以繼續編輯書稿，每次儲存後，網頁會自動重載，讓你看到最新的異動（因為有用到 Livereload）。

整個書籍靜態網站會擺放在 `_book` 目錄下，若是不需要即時檢視修正，也可以使用 `gitbook build` 建立。可以把整個目錄上傳到自己的網站空間，就連 GitHub Pages 空間都可以用。

### 製作電子書檔

從專案根目錄執行：

- `gitbook epub` 製作 ePub 電子書
- `gitbook mobi` 製作 Kindle 電子書
- `gitbook pdf` 製作 PDF 電子書

最簡指令就這樣，預設都是 `book` 加上副檔名，在專案的根目錄裡。

### 完整指令

你也可以從專案外部執行，完整的指令是：

```
gitbook epub [book] [output]
```

例如 `gitbook mobi ~/books/mynovel ~/Desktop/novel.mobi`。製作電子書指定 output 時需包含完整的路徑與檔案名稱，製作靜態網站版本就只需要路徑目錄。

輸入 `gitbook help` 可以看到說明訊息與指示。

### 結論

GitBook 真可說是未來出版的一個雛形建構，而且還在持續進化之中。

一般人可以下載桌面編輯器，或使用雲端進行編輯，只要注意草稿分支的使用技巧，完全不懂技術也能製作各種電子書。不怕終端機指令、略懂 Node 與 NPM 操作的人，搭配 `gitbook-cli` 與 Calibre 則可以完整使用 GitBook 的所有功能，離線自行製書或使用雲端服務，想怎麼用都行。

下一步的進階，就是「書籍呈現格式的調整」，以及「使用模板、外掛」等實驗性功能吧。


