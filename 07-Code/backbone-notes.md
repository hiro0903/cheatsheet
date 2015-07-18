# Backbone練習+筆記comment

```js

/**
 * 練習各種Backbone function
 * 
 * Backbone核心: M(Model, Collection) - V(View) - C(通常建立在View.events跟render上，另外sync function也應該屬於controller)
 *
 * Router跟History應該 V與C都包括, 一定要搭配location的hash使用
 */
var init = function ($) {

  var Member = Backbone.Model.extend({ //基本Model物件繼承

      defaults: function() {  //default可以直接給物件, 但因為obj call by ref, 給obj ref會被共用
        return {
          pwsid: '',   //注意, 這裡的屬性是存到物件內attributes, i.e. 是在this.attributes.pwsid 而非 this.pwsid
          email: '',
          handle: '',
          level: 100
        };
      },

      idAttribute: 'pwsid',  //設定之後, this.id會等於this.attributes.pwsid, 用來和backend溝通用

      deny: function(str) {
        var reason = str || window.prompt('拒絕原因','看他不爽');
        if (reason) {
          this.set({
            deny_reason: reason    //也可用this.set('deny_reason',reason)
          });
          return true;
        } else {
          return false;
        }
      },

      setPWSID: function(pwsid) {
        if (!pwsid || !/^\d+_\d+$/.test(pwsid)) return false;
        this.set({pwsid: pwsid});
        return true;
      }

  });

  var GoldMember = Member.extend({  //繼承Member, 所以defaults, deny, setPWSID都有
      defaults: {     //可是如果要給初始值, 就要全部重新給, 也可用Member.prototype.defaults extend, 都不太漂亮
          pwsid: '',
          email: '',
          handle: '',
          level: 300
      }
      /**
        defaults: _.extend(
            ( typeof(Member.prototype.defaults) === typeof(Function) ) ? Member.prototype.defaults.call() : Member.prototype.defaults,
            { level: 300 })
      **/

      //因為js沒有super, 所以如果覆寫function也要使用類似作法
  });

  var VIP = Member.extend({  //用constructor做法來繼承
      constructor: function(i) {
         i = i || {};
         _.extend(i, {level: 300});
         Member.call(this, i);
      }
  });

/**
  查詢handle資料, 有些結尾是';'
  https://admin.friendfinderinc.com/cgi-bin/admin/emailtester.cgi?
      tester_action=lookuphandle;
      site=ffadult;
      handle=hirochu&
      rid=1412306160068&

  查詢pwsid資料
  https://admin.friendfinderinc.com/cgi-bin/admin/emailtester.cgi?
      tester_action=lookup;
      site=ffp;
      pwsid=2391822_81585&
      rid=1412305746089&

  兩個結果一樣
*/

  var MemberList = Backbone.Collection.extend({
      model: function(attrs, opts) {      //通常這邊直接指定model class即可, 如Member
          if (attrs.level === 300) {
              return new VIP(atrs, opts);
          } else {
              return new Member(attrs, opts);
          }
      },

  });


  var Search = Backbone.Router.extend({    //利用hash標籤提供不同的功能
      routes: {  //支援的#路徑
        "online/*info":                  "search_online",     //#online/id=05;pid=7-11/on      => ["id=05;pid=7-11/on", null]
        "hot/:type/:isOnline/page:page": "search",            //#hot/single-couple/1/page1     => ["single-couple", "1", "1", null] 
        "hot/:type/id=:id(/page:page)":  "search_id",         //#hot/any/id=A123456789         => ["any", "A123456789", null, null] 
        "hot(/:check1-:check2)" :        "search"             //#hot/123-99                    => ["123", "99", null]
                                                              //#hot/123-12-2-AA               => ["123-12-2", "AA", null]     regexp從最外層往內包
      },

      search:        function(type, online, page)   { console.log('search:       ', arguments); },
      search_id:     function(type, id, page)       { console.log('search_id:    ', arguments); },
      search_online: function(info)                 { console.log('search_online:', arguments); },

  });

  var router = new Search();  //需要new之後才會trigger
  router.on("help/:chapter", function(chapter) {
      console.warn('HELP!! #' + chapter);
  });
  Backbone.history.start();  //開始啟用history, 也可用Backbone.history.start({pushState: true})

};

$(document).ready(init);

```