# 利用FontFamily建立badge/icon

1. 導入base64字型:
```css
@font-face {
  font-family: 'ffn-icons';
  src: url(data:application/x-font-ttf;charset=utf-8;base64,AAE....==) format('truetype'),
       url(data:application/font-woff;charset=utf-8;base64,d09...AAA=) format('woff');
  font-weight: normal;
  font-style: normal;
}
```

2. 在關鍵class前貼上icon
```css
.ffn-icon { font-family: "ffn-icons"; speak: none; font-style: normal; font-weight: normal; font-variant: normal; text-transform: none; line-height: 1; }
.ffn-icon.home:before     { content : "\e600"; }
.ffn-icon.notice:before,
.ffn-icon.notices:before  { content : "\e601"; }
```

* 注意事項:
    1. 最好是獨立的.css file, @import或用css-loader在產品階段合併, 要不然base64字型會拖累很多online editor
    2. 最困難的部份是要請UI/UX製作乾淨的字型...
