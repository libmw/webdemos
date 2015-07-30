---
  layout: api
  title: 正则表达式
---

## RegExp

RegExp是一个正则的全局类，保存了很多静态属性，静态属性被所有正则有关的方法所修改，包括string的方法

$1-$9代表()里面的东西，每次执行相关的匹配方法都会从$1开始赋值

RegExp.input 被匹配的字符串，没匹配到就不会更新

RegExp.lastMatch 最后一次匹配到的字符串

RegExp.lastParen 最后一次字匹配(即括号里面的匹配)

RegExp.leftContex被查找的字符串中从字符串开始位置到最后匹配之前的位置之间的字符

RegExp.rightContext被搜索的字符串中从最后一个匹配位置开始到字符串结尾之间的字符

RegExp. multiline 多行匹配 ，ie和opera不可用。实例的/m不会更改静态的multiline属性。此属性可读 可写。

## RegExp实例

实例的方法：exec，test

对于全局性的正则表达式，每次调用正则表达式的匹配方法都会去修改正则表达式实例的属性。包括test、exec。而没有/g或者非正则表达式的方法则不会修改实例。

lastIndex代表匹配后的索引，如最后匹配到的字符索引为8，lastIndex就是9。这也是指定下次匹配的开始索引，是可写的。`非全局匹配忽略此值`

### exec方法

exec是RegExp实例的方法

如果有/g，exec将从实例的lastIndex处开始匹配，否则从起始端匹配。

只会单次匹配不会全局匹配，要全局匹配必须重复调用，调用一次更新一次lastIndex值。

#### exec返回值

如果没有匹配到，返回null

如果无括号，返回值为长度为1的数组，元素为匹配到的文本。

如果有括号，除了返回匹配到的文本，数组还包含括号里面的所有东西。

如果返回值不为null，则返回值还有两个属性，input是被匹配的字符串，index是匹配到的第一个字符的index。

### test方法

test方法是RegExp实例的方法

此方法不接受字符串外的其他格式参数，包括数字，否则返回false。

如果有/g，test将从实例的lastIndex处开始匹配，否则从起始端匹配。

#### test返回值

返回值为true或者false

### match方法

match是String的方法，它的返回值依赖于有没有g属性。如果没有g，它返回值于exec一样，且有index和input属性，如果有g，它只返回数组，数组就是匹配到的所有值。

### replace方法

replace是字符串的方法，此方法遵守正则实例的lastIndex等属性。

#### 第二个参数是字符串

字符串里面可以使用 $1-$99代表匹配到的各个括号里的值。$&代表匹配到的字符串。$`代表匹配到的字符串的左边的字符串。$&apos;代表匹配到的字符串的右边的字符串。$$代表字符&apos;$&apos;。

#### 第二个参数是function

function(regStr,b1-b*,ind,sourceStr)。第一个参数是匹配到的串，b1-b*代表各个匹配到的括号，ind代表第一次匹配到的位置。sourceStr代表被匹配的串。在function里面也可以使用段字符，不过不能直接使用$&，应该是RegExp[&apos;$&&apos;] RegExp[&apos;$`&apos;] RegExp[&apos;$\&apos;&apos;] RegExp[&apos;$1&apos;]

如在replace方法里若有global，则会多次匹配字符串，每次匹配都会调用一次function，每次调用regStr,b1-b*,ind,sourceStr参数都会重置。

### search方法

search是字符串的方法，此方法不遵守正则实例的lastIndex。search返回的是被查找的正则或者字符串出现在本字符串中的位置。

### split方法

split的第一个参数也可以是正则表达式。

split第二个参数代表截取后的数组的最大length，若超过，这后面的被忽略。


## 量词+ . ?

量词默认都是`贪婪匹配`，即尽可能匹配多点。

如果要非贪婪匹配，需要在量词后加上问号(?)，比如/a+?/.test('aaa')，这样尽量匹配少，得到a

关于/a*/写法：这种写法和/\B/相等。都是匹配单词边界。所以他们返回的都是一个空字符串。

### 前瞻

捕获特定字符前的字符，比如/a(?=\d)/.exec(&apos;a1&apos;)匹配后面跟一个整数的a

### 后瞻

捕获非特定字符前的字符，比如/a(?!\d)b/.exec(&apos;ab&apos;)匹配后面不跟一个整数的a

## 关于\g参数

global参数一旦存在，正则表达式则会多次匹配。 每次都会修改RegExp的各个属性值。






## 例子

### 用前瞻实现金额的逗号分隔

<pre><code data-language="javascript">'1234567890'.replace(/\B(?=((\d{3})+)$)/g,',');</code></pre>

\B匹配非单词边界,?=代表后面跟了什么
<script>
</script>


