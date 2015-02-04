COLOR
=====
1. 編輯各站色票:
    * 編輯畫面: [Admin tool](https://admin.friendfinderinc.com/cgi-bin/admin/index.cgi) => [Tools and Reports](https://admin.friendfinderinc.com/cgi-bin/admin/index.cgi?tab=tools) => [Color Editor](https://admin.friendfinderinc.com/cgi-bin/admin/coloredit.cgi)
    * 一進入是在Cobrand Color的畫面, 建議使用**DB Cobrand**的**Lookup PID**功能, pid可以在網站的footer上找到, 類似: `(ADMIN ONLY) PID:p63693 | lfrom:fp (ADMIN ONLY)`
    * 找到站台之後選擇**edit**開始編輯
2. 編輯流程:
    * **建議先找UI/UX Design確認過顏色再改**
    * 先記錄下修改前色碼
    * 改上新的色碼, 選**Save Preview**, 這時候根據_GINO大神_說法, 可在dev環境用`preview=1`看到效果!
    * 確認無誤後, **Publish Live**
    * 最後, **Republish Template**才看得到效果
3. 注意事項:
    * COLOR修改沒有history可看, 千萬記得自己記錄, 可以的話也在JIRA/PB留一份, 可以參考這個格式:
      ```
fix to dev, per [~dorian.huang.tw]'s suggestion, update the colors below:
|| name || origin || new ||
| COLOR_NAVBAR_LINK_HOVER | #000000 | #FFFFFF |
| COLOR_NAVBAR_BACKGROUND_HOVER | #E8E8E8 | #000000 |
      ```
      這邊可以看到效果: [CD-26884](https://jira.friendfinderinc.com/browse/CD-26884)
    * 改完顏色千萬小心被誤推template!!
    
---
歡迎補充