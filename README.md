# easyUtil_dynamicBg
canvas实现动态背景图方法，两种模式，可全屏切换多图，也可在单一图片按位置切换。
<h3>简介</h3>
		<h4>&emsp;&emsp;原生js加canvas脚本功能实现动态背景图功能可选两种动画模式:setTimeout传统模式和requestAnimation的H5新增动画模式</h4>
		<h4>&emsp;&emsp;支持多帧图切换播放及单图片按位置切换方式</h4>
		<h4>&emsp;&emsp;支持模块化引用</h4>
		<h4>&emsp;&emsp;测试兼容主流（只要支持canvas的）浏览器</h4>
		<h4>&emsp;&emsp;使用提示：此插件虽已进行优化，尽可能的消除不必要的开销，但毕竟为js脚本执行，且依赖图片加载，因此不建议实现过多过长的动画背景，最佳为5s内循环的动画背景；如果需要更优质更长时间的效果，建议使用其他方式</h4>
		<h3>插件API:</h3>
		<h3>入口</h3>
		<ul>
			<li>普通调用全局引用名称为easy_DynamicBg，模块化可自定义名称</li>
		</ul>
		<h3>具体方法及参数（以普通调用名称为例）</h3>
		<ul>
			<li>
				以如下方法初始化即可：<br/>
				&emsp;&emsp;easy_DynamicBg.create(<br/>
								&emsp;&emsp;&emsp;&emsp;id：第一参数，｛String} canvas标签的id，必填 <br/>
								&emsp;&emsp;&emsp;&emsp;src：第二参数，{Array} 图片的src连接名称，必填，单图片情况可以是字符串也可以是数组，多图片必须数组；<br/>
								&emsp;&emsp;&emsp;&emsp;第三参数（根据需求选填）：{<br/>
						&emsp;&emsp;&emsp;&emsp;&emsp;multiple:false，单图片或多图片模式，默认false单图片；<br/>
						&emsp;&emsp;&emsp;&emsp;&emsp;timer:false，是否开始计时器模式(true)，默认requestAnimation模式；<br/>
						&emsp;&emsp;&emsp;&emsp;&emsp;speed:100，计时器模式下的播放速度，默认100ms，最快设置50ms,为了保证正常的动画效果，建议保持100ms,timer为false时该参数无效；<br/>
					&emsp;&emsp;&emsp;&emsp;&emsp;width:0，需显示图片的宽，多图片模式可不填写，默认为canvas的全屏宽高；<br/>
						&emsp;&emsp;&emsp;&emsp;&emsp;height:0，需显示图片的高，多图片模式可不填写，默认为canvas的全屏宽高；<br/>
						&emsp;&emsp;&emsp;&emsp;&emsp;offsetX:0，单图片模式下，图片在canvas画布上显示的偏移坐标x, 多图片模式下无效，不用填写；<br/>
						&emsp;&emsp;&emsp;&emsp;&emsp;offsetY:0，单图片模式下，图片在canvas画布上显示的偏移坐标y, 多图片模式下无效，不用填写；<br/>
						&emsp;&emsp;&emsp;&emsp;&emsp;x:0，单图片模式下，每行x的图片数量，如果相同，则可以只写x的值，多图模式下无效，不用填写；<br/>
						&emsp;&emsp;&emsp;&emsp;&emsp;y:0，单图片模式下，每列y的图片数量，如果相同，则可以只写x的值，多图模式下无效，不用填写。<br/>
						&emsp;&emsp;&emsp;&emsp;}<br/>
					&emsp;&emsp;)<br/>
			</li>
		</ul>
		<h4>具体应用举例</h4>
		<ul>
			<li>
				单图片模式：举例图片中每一个图片为50*65像素，每行每列均为4幅图，在canvas坐标200,100的位置显示，利用默认的requestAnimation方式<br/> 
			&emsp;&emsp;easy_DynamicBg.create("bgCanvas1", "20180606214031336.png", {<br/>
					&emsp;&emsp;&emsp;&emsp;width : 50, <br/>
					&emsp;&emsp;&emsp;&emsp;height : 65,<br/>
					&emsp;&emsp;&emsp;&emsp;offsetX : 200,<br/>
					&emsp;&emsp;&emsp;&emsp;offsetY : 100,<br/>
					&emsp;&emsp;&emsp;&emsp;x : 4,<br/>
			&emsp;&emsp;});<br/>
			</li>
			<li>
				多图片模式：两幅图，利用setTimeout显示,保持100ms刷新<br/>
				&emsp;&emsp;let src = (function(){<br/>
				&emsp;&emsp;let src = [];<br/>
				&emsp;&emsp;for(let i =0; i < 33; i++){<br/>
						&emsp;&emsp;&emsp;&emsp;src.push("pic"+i+".jpg");<br/>
				&emsp;&emsp;}<br/>
				&emsp;&emsp;return src;<br/>
		&emsp;&emsp;}());<br/>
			&emsp;&emsp;easy_DynamicBg.create("bgCanvas2", src, {<br/>
						&emsp;&emsp;&emsp;&emsp;multiple : true,<br/>
						&emsp;&emsp;&emsp;&emsp;timer:true<br/>
				&emsp;&emsp;});<br/>
			</li>
		</ul>
