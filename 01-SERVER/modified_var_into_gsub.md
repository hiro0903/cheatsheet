### Example

把contest/64/ 的 64放入gsub 參數中
```html
[if $ENV{HTTP_REFERER} =~ /contest\/(\d+)/ && ($self->{GLOBAL}{CONTEST_ID} = $1)]
<a href="[gsub link url='contest' args='contest=$self->{GLOBAL}{CONTEST_ID}']">EXAMPLE</a>
[endif]
```

結果:
```html
<a href="/p/contest?contest=66">EXAMPLE</a>
```

解說
```js
$ENV{HTTP_REFERER} =~ /contest\/(\d+)/   //利用perl Regex 把(數字)部份存入$1
&& 
($self->{GLOBAL}{CONTEST_ID} = $1)       //把$1 assign進 自己創的變數中

//最後把自創的變數放入gsub param中
args='contest=$self->{GLOBAL}{CONTEST_ID}'  //這邊一定要用$self->xxxx  用[var xxxx]會比[if ]先處理而得到空值
```

以上完全是剛好!! 例如把變數放入url中就不會轉換, 這做法僅能做為特殊解.