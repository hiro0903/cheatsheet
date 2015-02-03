Object
======

## Static

#### defineProperty

自定義指定物件中屬性的型態、setter、getter
```js
  var obj = { 'realRoot' : '/temp' };
  Object.defineProperty(obj, 'root', {
    enumerable: true,
    set : function(v) { if (v && v.length && v.length > 4) this.realRoot = v; }  
    //obj.root = '123'   => obj.realRoot: '/temp',  obj.root: undefined
    //obj.root = '12345' => obj.realRoot: '/12345', obj.root: undefined
  });
```

---

#### preventEntensions
不允許繼續增加object屬性, 但現有屬性可修改

---