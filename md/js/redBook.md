## 第2章: 在html中使用js  

1. 延迟脚本 && 异步脚本

延迟脚本: defer='defer'   
	`<script type='text/javascript' defer='defer' src='test.js'></script>`  
异步脚本: async 属性  
	`<script type='text/javascript' async src='test.js'></script>`  

说明:   
1) defer属性, 表明脚本会被立刻下载, 但会被延迟到整个页面都解析完毕后再执行  
2) 理论上, 脚本会按照他们出现的先后顺序执行, 但延迟脚本 "不一定" 会按顺序执行, 所以最好只包含一个延迟脚本  
3) html5 中规定 defer属性只适用于外部脚本文件, 但是ie4-ie7支持嵌入脚本的defer属性  
4) 因为有些浏览器不支持延迟脚本, 所以最好把延迟脚本放在页面底部, 保证它被最后执行  
5) async 也适用于外部脚本  
6) async 是异步脚本, 所以会立即下载, 但是执行的顺序不得而知, 所以, 如果引用多个异步脚本, 要保证各脚本间不相互依赖  

## 第3章: 基本概念 

### 基础知识  
1. 标识符: 就是变量、函数、属性的名字, 或者函数的参数  
2. 严格模式: 严格模式是es5提出的, 它对es3中的某些不确定的行为作出处理, 也会对一些不安全的操作抛出异常, 在脚本顶部添加 "use strict"; 即可启用严格模式  
3. 关键字: 是js语言保留的, 不能用作标识符  
4. 创建变量用 var 关键字, 变量在初始化之前会保存undefined, 变量的类型可以在赋值的时候随意改变, 可以一次定义多个变量  
5. var 创建的变量是它所在作用域的局部变量, 可以不用 var 而直接创建一个全局变量, 但是这样并不推荐  

### 数据类型   
1. 基本数据类型: String, Number, Boolean, Null, Undefined; 复杂数据类型: Object  
2. 检测数据类型: typeof + [要被检测的数据]  注意:  
	1) typeof + [function] => function  
	2) typeof [Object] => object  
3. Undefined: undefined, 未经初始化的变量都保存undefined值, 但是    
	1) 通过typeof检测未声明和未初始化的变量都会返回undefined  
	2) 应用中, 我们把没有初始值的变量显式的赋值为undefined, 这样只要用typeof检测变量返回undefined, 我们就可以确定是变量没有定义而非没有赋值  
4. Null: null, 空对象指针(typeof null => Object), 注意:  
	1) 如果一个变量将来要保存对象, 那么在声明的时候, 就为它赋值为null  
	2) (null == undefined) => true  
	3) (null === undefined) => false  
5. Boolean: true / false  
	1) 其他类型的数据都可以转换成Boolean类型  
	2) 转换方法: Boolean([要被转换的变量])  
	3) 转换为true: 非空字符串, 非零数字, 非空对象  
	4) 转换为false: 空字符串, 0/NaN, Null, undefined  
6. Number: 不分整型和浮点型  
	1) 数据范围: Number.MIN_VALUE <==> Number.MAX_VALUE  
	2) 如果计算中数据的结果超出了规定的范围, 如果结果为负, 转换为: -Infinity; 如果结果为正, 转换为: Infinity  
	3) Infinity / -Infinity 均无法参加下一次计算  
	4) 检测数据范围是否合法: isFinite([被检测的变量]), 在范围内 => true, 不在范围内 => false  
	5) Number.NEGATIVE_VALUE 保存着 -Infinity ; Number.POSITIOV_VALUE 保存着 Infinity  
	6) 非数字: NaN  
	7) (NaN == NaN)  => false  
	8) 检测一个变量是不是NaN, 用 isNaN() , 得到非数字返回true, 数字返回false  
	9) 非数值转为数值: Number([任何类型变量]), parseInt([字符串变量], [几进制]), parseFloat([字符串变量]), 注意: Number()很少用  
7. String: 由双引号/单引号包裹  
	1) 获取字符串长度: [字符串].length  
	2) 转换为字符串: [被转换的变量].toString([几进制]), 注意: 字符串也有这个方法, 获取的是它的一个副本  
	3) null 和 undefined 没有 toString() 方法, 所以用 String([被转换的数据]) 来转换  
8. Object: new Object(), 通过console.dir([对象名称]), 可以查看当前对象有哪些属性和方法  
 
## 第13章: 事件  

## 第17章: 错误调试  

### 怎样在不同浏览器中查错
#### 1. IE   
1) IE默认如果出现错误会在浏览器左下角出现黄色叹号, 双击后会看到错误信息  
2) 通过, 点击 [菜单]-[Internet选项]-[高级]-[勾选显示每个脚本错误的通知]-[ok] 这些设置后, 出现错误会自动弹出错误提示框. 另外, 如果启用了脚本调试功能的话, 出现错误时不仅有错误提示, 还会看到询问是否调试的对话框  
#### 2. 火狐  
1) 火狐的错误提示都会在控制台中打出, windows上面可以按F12打开控制台  
2) 火狐的调试插件Firebug, 是非常好的调试插件  
#### 3. Safari  
1) Safari默认不显示js错误, 通过两步设置可以打开开发者工具
2) 第一, 通过, 点击[Safari]-[偏好设置]-[高级]-[勾选在菜单栏中显示开发菜单] 这些设置后, 菜单栏中会出现开发菜单  
3) 第二, 点击开发菜单后, 会看到很多调试选项, 点击[显示错误控制台]就能看到错误了  
#### 4. Opera  
1) Opera默认不显示错误, 错误都会记录在控制台  
2) 通过, 点击[工具]-[高级]-[错误控制台], 这些设置后, 就可以显示错误控制台了  
3) 通过, 点击[工具]-[首选项]-[高级选项片]-[选择内容]-[选择JavaScript选项]-[选中出错时打开控制台]-[ok] 这些设置后, 每当js出错时, 就会自动调出错误控制台  
4) 针对特定的站点做此设置, [工具]-[快速参数]-[编辑站点首选项]-[脚本选项片]-[出错时打开控制台]  
#### 5. Chrome  
1) Chrome默认隐藏js错误, 所有错误也记录在错误控制台中  
2) windows上面可以按F12调出控制台  

### 错误处理的方法  
#### 1. try-catch  
1) 格式:  
	`try{`
		// 可能会出错的代码
	`} catch (error) {`
		// 出现错误后的处理办法  
		// error对象中包含错误信息, 可以打印查看, 也可以直接将error.message输出给用户看  
		// error对象中, 不同的浏览器可能添加其他的附加信息, 但为了兼容, 最好还是使用message属性  
	`} finally {`

	`};`  
2) try块是必须的, catch块和finally块是可以二者选一的  
3) try-catch-finally: 将可能出错的代码放在try块中, 一旦出现错误, 立刻跳到catch块中, catch块执行完毕, 再执行finally块, 只要有finally块存在就一定要执行, 即使try/catch块中有return, finally也会正常执行  
4) try-catch: finally块是可选的, 如果没有finally块, 就一定要有catch块  
5) try-finally: catch块是可选的, 如果没有catch块, 就一定要有finally块  
	举例:  
	`try{`
		// 连接数据库, 做操作  
	`} finally {`
		// 出错之后, 关闭数据库  
	`}`  
6) 错误类型分类  
-> Error: 错误的基类, 其他的几种类型都继承自它    
-> EvalError: 使用eval()函数而出错  
-> RangeError: 数值超出相应的范围  
-> ReferenceError: 对象找不到  
-> SyntaxError: 语法错误的字符串传入了eval()方法
-> TypeError: 执行特定于类型的操作时, 变量的类型不符合要求  
	最常发生的类型错误的情况, 就是传入给函数的参数事先未经检查, 结果传入类型与预期类型不相符(如在需要使用字符串的时候, 使用了对象)  
-> URIError: 在使用 encodeURI/decodeURI 方法时, 传入的URI格式不正确  
7) 了解错误类型可以更快处理错误, 所以可以在try-catch的catch块中判断错误的类型, 来寻求解决方案  
8) 明知道会发生错误的代码不要放在try-catch中, 只有那些可能出错的代码, 采用try-catch(如引用一个js库的时候, 可以把对他的调用放在try-catch中)
#### 2. throw 抛出错误  
1) 
