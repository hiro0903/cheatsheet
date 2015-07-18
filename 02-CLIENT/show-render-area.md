顯示重繪區域
===
用來評估對DOM / style的操作是否造成瀏覽器負荷過高, 讓使用者感到操作不順

(主要是fps大幅掉落時可以開啟這功能檢視)

###Chrome
1. open "Developer Tools" (Ctrl+Shift+I)
2. show "drawer" (ESC)
3. switch to "Rendering" tab
4. check "Show paint rectangles"

###Firefox
1. open about:config
2. set 'nglayout.debug.paint_flashing' as true