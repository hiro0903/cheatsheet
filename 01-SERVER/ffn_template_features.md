### tempalte 查詢方式

* **showtemplates**.dev21.adultfriendfinder.com
* dev21.adultfriendfinder.com**.stmpl=1**
* pref table (footer 下方奇怪的區塊)

---

### 關掉 admin 的方法

 * debug_cookie=perf_off:0
 * &noadmin=1

---


### gsub & psub

```javascript
//製作form
[gsub form_link url='update.cgi' method='POST'] 

//無法用[var GLOBAL->PDF->xxxx]時使用
[gsub get_value pdf='CUPID_sex']

//取得某個pdf值並防單雙引號跳脫
[gsub get_value_js pdf='xxxxx']

//如果不想得到%22之類網址字元的
[gsub link url='...' args='...'  NO_URL_ENCODE='1']
```
---
### parse & inc

|      | parse                |  inc                      |
|:----:|:---------------------|:--------------------------|
|  受  |[parse tmp2 value='1']|[inc template type='A']    |
|  攻  |[var LOCAL->value]    |[var param->type]          |
| 順序 |攻先編譯好後才給受    |攻直接進入受, 一起編譯     |
| 互通 |[def]不可互通         |[def]可互通                |
| push |只推攻，受也會更新    |只推受，攻也會被推且沒log  |              |

(把內容插入到另外一個template中的叫作**攻**, 通常就是**被引用**的template)

---
### if

| 判斷式         | True  | False | 和js不同 |
|:---------------|:-----:|:-----:|:--------:|
|[if 0]          |       |   ✓   |          |
|[if '0']        |       |   ✓   |    ◎     |
|[if ""]         |       |   ✓   |          |
|                |       |       |          |
|[if "0" ne '']  |   ✓   |       |          |
|[if '' ne '']   |       |   ✓   |          |
|[if "" ne '']   |       |   ✓   |          |
|[if 0 ne '']    |   ✓   |       |          | |
---
### text & text_js

[text_js deftag] 可引入DefTag的內容, 並且會在單引號`'`跟雙引號`"`前面加上反斜線`\`.

所以text_js 的反跳脫只對js有效(html無效)


---
### initsub
用來呼叫GlobalLib中各式各樣的sub, 有些GLOBAL只有在某些template中出現, 而且backend一直抓不到哪時後載入這個GLOBAL就很可能是這邊產生, 如:

* **template:** footer_v3.0
* **call sub:** [initsub getLangLinkHash]
* **產生GLOBAL:** 
    * [var GLOBAL->UPDATE_LANG->english]
    * [var GLOBAL->UPDATE_LANG->spanish]
    * ... 