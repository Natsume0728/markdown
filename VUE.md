# VUE

[视频: MVVM 设计模式](https://www.bilibili.com/video/av57366545/)
[视频: ES5 访问器属性 get set](https://www.bilibili.com/video/av57373116/)

## 什么是 VUE

>VUE 是渐进式的基于 MVVM 设计模式的纯前端 JS 框架  
>>渐进式: 可以在项目中逐步使用 VUE 的功能，也可以和其它技术混搭。
>>vs 全家桶: 要使用，就必须使用全套所有技术。且不能喝其它技术混搭。

   MVVM 设计模式: ?
   框架: 原生 DOM vs jQuery 函数库 vs VUE 框架
   原生 DOM: 步骤多， 函数繁琐
   jQuery 函数库: 步骤没少，每个函数都变的很简单

   框架: 彻底简化了步骤，无需人工干预。
   什么是框架: 已经是一个半成品的项目，封装了大量重复性劳动。人只要提供个性化定制即可。
   何时: VUE 只适合于数据操作为主的项目
   还是五件事: 增删改查+事件绑定.

1. 如何使用:
   下载: 2 种方式:
2. 下载并引入 vue.js 文件: 前 2 天
3. 用脚手架代码: 最后一天讲

版本: 2.5
开发版: 未压缩版本 , 有完备的错误提示
生产版: 压缩版本 , 删掉了错误提示

3. MVVM 设计模式
   传统前端划分:
   HTML: 专门保存网页内容和结构的文档
   CSS: 专门定义网页样式的文档
   JS: 为网页添加交互行为
   问题: HTML 和 CSS 太蠢了！不会动态变化
   一切交互都只能靠 JS 添加。
   导致 JS 中大量重复的代码和重复的步骤。
   MVVM 模式:
1. 界面 View: 增强版的 HTML 和 CSS，可跟据数据自动变化
1. 模型数据 Model:集中存储一个页面内的所有变化的数据。
1. 视图模型 ViewModel: 将 View 界面和 Model 模型数据包裹起来，统一管理，自动同步修改。
   ViewModel 中(new Vue()对象)
   包含两大子系统: 1. 响应系统: 将模型数据包裹起来，为每个模型变量自动添加 get()和 set()保镖。
   今后只要修改任何模型变量，都自动经过 set()，set()中会触发通知: xx 变量变为 xx 新值
   通知会发给虚拟 DOM 树 2. 虚拟 DOM 树
   什么是: 创建 new Vue 时，通过扫描完整 DOM 树，仅提取可能变化的元素和属性，组成的一颗及精简的虚拟 DOM 树。
   优点: 1. 查找元素快 2. 封装了重复性的增删改查 DOM 操作
   虚拟 DOM 树接到通知，快速找到受影响的元素。调用已经封装好的 DOM 函数，仅更新受影响的元素的受影响的属性。

1) 绑定语法: 学名: 插值语法 Interpolation == {{}}
   什么是: 让 HTML 可以自动找到程序中的变量的特殊语法
   为什么: 因为传统的 HTML 是静态的，缺少动态变化的能力。导致 js 当中要想操作 HTML，需要大量重复的代码。
   何时: 只要 HTML 中某个位置的数据，需要根据程序中的一个变量动态变化！都要用绑定语法！
   如何: 2 步:
   1. 先找页面中所有可能发生变化的地方有几处
   2. 再在模型数据中定义相同数量的变量:
      new Vue({
      el:"#app",
      data:{
      变量名:值,
      ... : ...,
      }
      })
      强调: HTML 中有几处变化，data 对象中就要有几个变量与之对应。
   3. 在 HTML 中，可能发生变化的位置用绑定语法定义变量: {{变量或表达式}}
      强调: 其实{{}}的用法和模板字符串中\${}的用法完全一样！
      能写：变量, 算术计算，关系/逻辑运算，函数调用, 访问数组元素, 三目——凡是有返回值的 js 表达式都能
      不能: if else while for——都是程序结构，没有返回值！
      结果: 运行时，HTML 中的所有{{}}会自动去 data 中找同名的变量使用。且内存中的 data 中的变量值发生变化，HTML 中的{{}}的值自动变化！用户最终看到的是{{}}中的变量或者表达式计算后的值！而看不见双花括号——节省了大量重复的查找和修改操作。——多亏了 MVVM 中的 ViewModel 中的两大子系统: 响应系统和虚拟 DOM 树。

## 指令

什么是: 为 HTML 添加更多新功能的 Vue 预置的自定义属性
为什么: 因为原来 HTML 缺少程序必须的功能: 判断/分支结构，循环。。。功能。所以只能依靠 js 中反复查找，反复修改来控制 HTML 元素的内容和状态。
如何: 13 种: 1. 绑定属性:
什么是: v-bind 属性专门动态绑定元素的属性值
为什么: 要绑定属性值，不能用{{}}，只能用 v-bind 或:简写
何时: 只要属性值需要根据变量动态变化时，就要用 v-bind 或:简写
如何: <img v-bind:src="pm25<100?'img/1.png':
             		  pm25<200?'img/2.png':
             		  pm25<300?'img/3.png':
                      		    'img/4.png'">
去{{}}换 v-bind:
其实可简写: <img v-bind:src="...
去{{}}换: 2. 控制元素的显示隐藏: 1. 控制一个元素的显示隐藏:
<ANY v-show="判断条件"
只要条件满足，就显示元素
一旦条件不再满足，就隐藏元素！ 2. 控制多个元素，多选一显示:
<ANY v-if="判断条件" 单用时
v-if 从现象上看，和 v-show 是完全一样的
但是原理不一样
鄙视: v-show vs v-if 的差别:
v-show 用 display:none 控制显示隐藏
v-if 用删除节点的方式，控制显示隐藏
如果一个元素频繁需要显示隐藏,v-show 的效率高！
和 v-else-if v-else 配合使用:
<元素 1 v-if="条件 1"
<元素 2 v-else-if="条件 2"
... ...
<元素 n v-else
强调: v-if 和 v-else-if 和 v-else 之间禁止插入一切其他元素。必须连续写！
原理: Vue 会自动判断每个条件：
哪个条件符合，就只显示哪个条件的元素。其余元素都不显示。
如果前一个条件已经满足，则后续判断都不再执行。所以，不可能同时显示多个元素。
如果所有条件都不满足，会显示 v-else 的元素

    3. 根据数组反复生成多个相同结构的HTML元素:
    	其实就是为HTML添加循环功能:
    	如何:
    		1. data中必须先定义一个可遍历的数组
    		2. 在HTML中使用v-for遍历数组，反复生成多个相同结构的元素，并动态绑定元素的内容。
    			语法:
    <要反复生成的元素 v-for="(elem,i) of 数组" :key="i"
    			强调: 特例: v-for中的循环变量可被v-for自己或子元素用于绑定！

    4. 事件绑定:
    	v-on:事件名="处理函数"
    	可简写为:
    	@事件名="处理函数"
        强调:
    	1. 处理函数必须定义在:
           new Vue({
             el:"#app",
    		 data:{ ... },
    		 methods:{
    			处理函数(){
     				this.data中变量
                }
          	 }
           })中的methods:{}结构中
    	2.	其实可以传参: @事件名="处理函数(实参值)"
    	3. 也可以用事件对象e：用法和DOM中完全一样
    		获得e: methods:{
    				事件处理函数(e){ ... }

}
后续:
获得目标元素，实现事件委托： e.target
取消冒泡: e.stopPropagation()
阻止默认行为: e.preventDefault();
键盘事件中获得键盘号: e.keyCode
获得鼠标坐标位置: e.screenX, e.screenY
e.clientX, e.clientY
e.offsetX, e.offsetY

    5. 避免用户短暂看到{{}}
    	问题: 如果new Vue加载慢，则可能短暂看到{{}}
    	解决: v-cloak 可让元素在new Vue加载之前暂时隐藏。当new Vue加载完成后，会自动查找页面中的所有v-cloak斗篷删除该属性，让元素显示出来。
     	强调: v-cloak没有属性值！
        问题: v-cloak空有属性名，没有配套的样式

解决: 只能自己手写！用属性选择器:
[v-cloak]{display:none}
强调: v-cloak 不能改名！改名了，vue 就找不到了！
其实，除了 v-cloak 外，还可用 v-text 代替{{}}绑定元素内容，避免短暂看到{{}}
如何:
<ANY v-text="`js模板字符串语法，用${变量}动态生成内容`"
比如:
<h1 v-text="`姓名: ${uname}`"></h1>
<h2 v-text="`性别: ${sex==1?'男':'女'}`"></h2>
原理: v-text 在未绑定时，是一个浏览器不认识的属性，所以，显示不出来。直到 new Vue 加载完，认出 v-text，才用 V-text 的内容代替元素的 innerHTML 内容。
v-cloak vs v-text:
v-cloak: 需要额外添加 css 样式，且需要选择放在哪个元素上，隐藏什么范围内的元素。整个网页都隐藏，用户体验还是不好的。
v-text: 仅对当前元素有效，不会影响其它元素的显示不显示。用户体验比 v-cloak 要好。但是使用反引号的语法，很晦涩。

    6. 绑定HTML片段:
    	问题: 使用{{}}绑定HTML片段，VUE不会解析HTML片段为网页内容。而是原样显示HTML代码
    	解决: 今后，只要绑定一段HTML片段，必须用v-html。
    	如何: <ANY v-html="变量"></ANY>
    7. 只在页面加载之初，绑定一次。之后及时数据变化，也不反复更改页面：v-once
    	强调: v-once没有任何属性值，写在元素中，就起作用
    	原理:
    		在构建虚拟DOM树时，会扫描到v-once的元素，所以首次绑定，能绑定v-once的元素的内容。
    		首次绑定后，v-once的元素会从虚拟DOM树中移除。从此，再出发变量改变时，不会再修改v-once的元素。
    8. 万一内容的正文中，有{{}}，但是不是用于绑定的，会出错。
    	解决: v-pre  可阻止内容中的{{}}被编译，而是让{{}}原样显示。

总结:

1. 如果元素内容要变化:
   用 {{变量或表达式}} 绑定
   也可用 v-text="`变量或表达式`"
2. 如果元素的属性值要变化: 用 :属性名="变量或表达式" 绑定
3. 一个元素控制显示隐藏: v-show="条件"
4. 多个元素选其一显示:
   v-if="条件" v-else-if="条件" v-else
5. 反复生成多个相同结构的元素时:
   v-for="(elem, i ) of 数组" :key="i"
6. 只要绑定事件处理函数都用: @事件名="处理函数"
7. 只要不希望用户短暂看到{{}}语法:
   v-cloak 或 v-text
8. 只要绑定 HTML 片段: v-html
9. 只要希望只在页面加载之初绑定一次，之后不再变化，就用 v-once.
10. 如果内容中包含不想被 vue 编译的{{}}正文，可用 v-pre 阻止 VUE 编译元素的内容。
