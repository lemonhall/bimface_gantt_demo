1、甘特图组件
https://frappe.io/gantt

甘特图用这个组件

=============================================


2、BIM组件
然后

https://api.bimface.com/preview/b62a9ad2?viewid=957


2.1 获取应用token
进入“控制台-项目管理-应用详情”查看APP证书

注册好了：
应用名称：计划进度模型一体化


2.2 获取viewtoken

https://bimface.com/docs/model-viewer/v1/developers-guide/view-token.html


c5bcce8a2f474352aa03c600d749028a

12小时会失效

2.3 第三步，显示模型
https://bimface.com/docs/model-viewer/v1/developers-guide/load-model.html


	<div id="domId" style="width:800px; height:600px;margin-left: 500px;"></div>

    <script src="https://static.bimface.com/api/BimfaceSDKLoader/BimfaceSDKLoader@latest-release.js" charset="utf-8"></script>
    <script>
        //在这里输入BIMFACE JavaScript SDK提供的方法
        let viewer3D;
		let app;
		let viewToken = 'c5bcce8a2f474352aa03c600d749028a';
		//创建BimfaceSDKLoaderConfig
		let loaderConfig = new BimfaceSDKLoaderConfig();
		//设置BimfaceSDKLoaderConfig的viewToken
		loaderConfig.viewToken = viewToken;
		//调用BimfaceSDKLoader的load方法加载模型
		BimfaceSDKLoader.load(loaderConfig, successCallback, failureCallback);

		//加载成功回调函数
		function successCallback(viewMetaData) {
		    //获取DOM元素
		    let domShow = document.getElementById('domId');
		    //创建WebApplication3DConfig
		    let webAppConfig = new Glodon.Bimface.Application.WebApplication3DConfig();
		    //设置创建WebApplication3DConfig的dom元素值
		        webAppConfig.domElement = domShow;    
		    //创建WebApplication3D
		    app = new Glodon.Bimface.Application.WebApplication3D(webAppConfig);    
		    //添加待显示的模型
		        app.addView(viewToken);
		    //获取viewer3D对象
		    viewer3D = app.getViewer();    
		};

		//加载失败回调函数
		function failureCallback(error) {
		    console.log(error);
		};
    </script>

======================================================================
2.4 只显示F2楼层的构件，其他构件半透明处理
https://bimface.com/docs/model-viewer/v1/developers-guide/edit-components.html





BIM用虹桥花苑

https://bimface.com/docs/model-viewer/v1/developers-guide/conditions.html

rvt、rfa等三维模型的objectData信息一般包含categoryId、family、familyType、levelName及specialty等字段，objectData信息示例如下：



==================
2.5 增加一个车辆
https://bimface.com/docs/model-viewer/v1/developers-guide/external-object.html



==================

3、iframe执行函数
执行iframe里面的某个功能
https://stackoverflow.com/questions/251420/invoking-javascript-code-in-an-iframe-from-the-parent-page

Assume your iFrame's id is "targetFrame" and the function you want to call is targetFunction():

document.getElementById('targetFrame').contentWindow.targetFunction();
You can also access the frame using window.frames instead of document.getElementById.

// this option does not work in most of latest versions of chrome and Firefox
window.frames[0].frameElement.contentWindow.targetFunction(); 

4、选择某个图层
$(".bf-tree[title=地下室]")