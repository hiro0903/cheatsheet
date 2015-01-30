印出perl變數: {LOCAL}與{GLOBAL}{FORM}的pseudo code:

```html
[if $self->{GLOBAL}{ADMIN} eq '1']
<style>
  .perl { position: fixed; height: 80vh; width: 20vh; overflow: auto; top: 98vh; opacity: 0.3; transition: top 0.3s, opacity 0.5s, width 0.2s 0.3s; z-index: 10000; }
  .perl:hover { top: 20vh; width: 70vh; opacity: 0.8; }
  .perl.local { right: 1vh; background-color: #38b48b; }
  .perl.global{ right:26vh; background-color: #a0d8ef; }  
</style>
<pre class="perl local">
  <strong>LOCAL</strong>
[perl 
  use Data::Dumper; 
  Dumper($self->{LOCAL}); +]
</pre>
<pre class="perl global">
<strong>GLOBAL FORM</strong>
[perl
  Dumper($self->{GLOBAL}{FORM}); +]
</pre>

[endif]
```