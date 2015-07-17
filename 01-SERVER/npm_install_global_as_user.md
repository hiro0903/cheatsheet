# 不使用Root權限, 全域安裝node套件的方法

很多node套件會提供可執行script, 但是只有安裝在global的環境下才可直接執行,
像是: webpack, grunt, gulp...

有個簡單的方法讓`npm install -g`轉到個人目錄下:

1. `npm config set prefix '~/.npm_packages'`  把預設路徑轉到~/.npm_packages下

2. 在個人檔案, 例如~/.bashrc中加上新路徑: `export PATH="$PATH:$HOME/.npm_packages/bin"`,

3. done, 重新載入設定檔就好了(`source .bashrc`)