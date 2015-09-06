---
  layout: skill
  title: 未解之谜
---

## window.onload 以后通过手动创建script标签插入的script会200 from cache

<pre><code data-language="javascript">window.onload = function(){
    setTimeout(function(){
        var s = document.createElement('script');
        document.getElementsByTagName('head')[0].appendChild(s);
        s.setAttribute('src',"cache_aysn.js")
    }, 2000);
}

</code></pre>
这里的cache_aysn.js不会被304，而是200 from cache，这样导致异步加载的js无法保证最新。目前不知道为啥会这样，解决办法是加后缀