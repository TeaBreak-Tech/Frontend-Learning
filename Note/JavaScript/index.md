# JavaScript 笔记索引
## Usage
> JavaScript代码可以直接嵌在网页的任何地方(通常在head中)
> >`<script>...</script>`包含的代码就是JavaScript代码

> JavaScript代码放入.js文件，在HTML中<script src="..."></script>引入。

## Basic
1. `==` , change the data type and compare;
2. `===`, if data type is different, return false
3. `NaN` is not equal with any others.
4. `array` \\ can contain any data types (different);

## function
1. `arguments` \\ determine how many arguments have been passed;
2. `f(a [, b], c)` \\ b is optional;

## 箭头函数
`var fn = x => x * x` 
## Promise
执行代码和处理结果的代码清晰分离 => 异步任务


+ *串行* `job1.then(job2).then(job3).catch(handleError);`

+ *并行* 

> + `Promise.all()`  页面聊天系统从两个不同的URL分别获得用户的个人信息和好友列表


<pre><code class="javascript"><span class="keyword">var</span> p1 = <span class="keyword">new</span> Promise(<span class="function"><span class="keyword">function</span> <span class="params">(resolve, reject)</span> {</span>
    setTimeout(resolve, <span class="number">500</span>, <span class="string">'P1'</span>);
});
<span class="keyword">var</span> p2 = <span class="keyword">new</span> Promise(<span class="function"><span class="keyword">function</span> <span class="params">(resolve, reject)</span> {</span>
    setTimeout(resolve, <span class="number">600</span>, <span class="string">'P2'</span>);
});
<span class="comment">// 同时执行p1和p2，并在它们都完成后执行then:</span>
Promise.all([p1, p2]).then(<span class="function"><span class="keyword">function</span> <span class="params">(results)</span> {</span>
    console.log(results); <span class="comment">// 获得一个Array: ['P1', 'P2']</span>
});
</code></pre>


> + `Promise.race()` 

<pre><code class="javascript"><span class="keyword">var</span> p1 = <span class="keyword">new</span> Promise(<span class="function"><span class="keyword">function</span> <span class="params">(resolve, reject)</span> {</span>
    setTimeout(resolve, <span class="number">500</span>, <span class="string">'P1'</span>);
});
<span class="keyword">var</span> p2 = <span class="keyword">new</span> Promise(<span class="function"><span class="keyword">function</span> <span class="params">(resolve, reject)</span> {</span>
    setTimeout(resolve, <span class="number">600</span>, <span class="string">'P2'</span>);
});
Promise.race([p1, p2]).then(<span class="function"><span class="keyword">function</span> <span class="params">(result)</span> {</span>
    console.log(result); <span class="comment">// 'P1' (p1执行较快，Promise的then()将获得结果'P1'。p2仍在继续执行，但执行结果将被丢弃。) </span>
});
</code></pre>

## RegExp
`\d`: a number \\
`\w`: a number or letter\\
`.`: any character ; `js.`  ==> `jss`, `js!`\\
要匹配变长的字符，用`*`表示任意个字符（包括0个），用`+`表示至少一个字符，`?`表示0个或1个字符，用`{n}`表示n个字符，用`{n,m}`表示n-m个字符; \\
`\d{3}\s+\d{3,8}`

\d{3}表示匹配3个数字;

\s可以匹配一个空格（也包括Tab等空白符），\s+表示至少有一个空格；

\d{3,8}表示3-8个数字，例如'1234567'。


`[0-9a-zA-Z\_]`可以匹配*一个*数字、字母或者下划线；

`[0-9a-zA-Z\_]+`可以匹配至少由一个数字、字母或者下划线组成的字符串，比如'a100'；

`[a-zA-Z\_\$][0-9a-zA-Z\_\$]*`可以匹配由字母或下划线、$开头，后接任意个由一个数字、字母或者下划线、$组成的字符串

`[a-zA-Z\_\$][0-9a-zA-Z\_\$]{0, 19}`长度是1-20个字符（前面1个字符+后面最多19个字符）。

`A|B`可以匹配A或B，(J|j)ava(S|s)cript可以匹配'JavaScript'、'Javascript'、'javaScript'或者'javascript'。

`^`表示行的开头，`^\d`表示必须以数字开头。

`$`表示行的结束，`\d$`表示必须以数字结束。

`()` 提取分组	  
`var re = /^(\d{3})-(\d{3,8})$/;` \\
`re.exec('010-12345'); // ['010-12345', '010', '12345']`

## 单表
文本框，对应的`<input type="text">`，用于输入文本；

口令框，对应的`<input type="password">`，用于输入口令；

单选框，对应的`<input type="radio">`，用于选择一项；

复选框，对应的`<input type="checkbox">`，用于选择多项；

下拉框，对应的`<select>`，用于选择一项；

隐藏文本，对应的`<input type="hidden">`，用户不可见，但表单提交时会把隐藏文本发送到服务器。

