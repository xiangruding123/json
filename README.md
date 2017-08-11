## json
###json数据格式的理解以及json字符串和json对象之间的转换方法

demo1.html
--------------
/*
 * 在Firefox，chrome，opera，safari，ie9，ie8等高级浏览器直接可以用JSON对象的stringify()和parse()方法。
 * 
 * JSON.stringify(obj)   将JSON转为字符串。
 * 
 * JSON.parse(string)    将字符串转为JSON格式。
 * 
 * 
 */
 
 
 demo2.html
 -----------------------
 ie8(兼容模式),ie7和ie6没有JSON对象，不过http://www.json.org/提供了一个json.js,
这样ie8(兼容模式),ie7和ie6就可以支持JSON对象以及其stringify()和parse()方法；
你可以在https://github.com/douglascrockford/JSON-js上获取到这个js，一般现在用json2.js。

ie8(兼容模式),ie7和ie6可以使用eval()将字符串转为JSON对象，
eval("("+c+")")


demo3.html
----------------------------
<p>jQuery中也有将字符串转为JSON格式的方法jQuery.parseJSON( json )，接受一个标准格式的 JSON 字符串，并返回解析后的 JavaScript （JSON）对象.</p>
<p>
	描述: 接受一个标准格式的 JSON 字符串，并返回解析后的 JavaScript 值。

	从jQuery 3.0开始，不推荐使用$.parseJSON。 要解析JSON字符串，请改用原生的 JSON.parse 方法。

	传入格式有误的 JSON 字符串可能导致抛出异常。例如，下面这些无效的 JSON 字符串：
	---------------------------------------------------
	{test: 1} (test 没有使用双引号包裹).
	{'test': 1} ('test' 用了单引号而不是双引号包裹).
	"{test: 1}" (test 没有使用双引号包裹).
	"{'test': 1}" ('test' 用了单引号而不是双引号包裹).
	"'test'" ('test' 用单引号代替双引号).
	".1" (number 必须以数字开头; "0.1" 将是有效的).
	"undefined" (undefined 不能表示一个 JSON 字符串; 然而null,可以).
	"NaN" (NaN 不能表示一个 JSON 字符串; 用Infinity直接表示无限也是不允许的).
	---------------------------------------------------

	JSON标准不允许“控制字符”如制表符或换行符。
	比如$.parseJSON('{"testing":"1\t2\n3"}')，大多数实现中将抛出一个错误，因为JavaScript分析器直接转换字符串的制表符和换行符为文本的制表符和换行符; 
	产生双反斜杠，例如"1\\t2\\n3"是预期的结果。
	这个问题往往在服务器端语言，如PHP，JSON注入到一个JavaScript文件时发生。

	如果浏览器实现了原生的 JSON.parse， jQuery 则会使用它来解析字符串。

	在jQuery 1.9之前,如果传递给$.parseJSON一个空字符串，null, 或者 undefined,，将返回null，而不是抛出一个错误，即使这些都不是有效的JSON。

	jQuery 3.0开始，$.parseJSON已经过时（不建议使用）。要将字符串解析成JSON对象，请使用原生的JSON.parse方法来代替。

</p>
