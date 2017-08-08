# WheelView
当初写这个控件基于三个原因：
* 想找个控件来练练手，再次熟悉熟悉自定义view
* 最近开始流行学习kotlin语言了，我也已经学习了一段时间，想练练手
* 最近发现公司的滚轮控件出现了一个bug


## 特点
* 使用Kotlin语言编写
* 完全使用自定义的view编写完成，我看过有些人不是完全基于view写的
* 实现了三种滚轮模式：  
	    * 循环模式:  
        * 居中显示模式；    
        * 从头开始显示
* 自己处理了滚动事件和快速滑动事件
* 处理了边界检测和弹性效果
* 通过adapter快速添加数据


## 效果图
![github](https://github.com/victorfan336/WheelView/blob/master/wheelview.gif)  

## 使用

* Import(java版本的)   
    compile 'com.victor.library:wheelview:1.0.2@aar'   

* 定义了三个可配置属性：
	``` java
    <attr name="textColor" format="color"/>
    <attr name="textSize" format="dimension" />
    <attr name="dragOut" format="boolean" />
    ```
* 在xml中配置：
``` java    
	<com.victor.library.wheelview.WheelView
        android:id="@+id/wheelview"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:layout_weight="1.0"
        android:focusable="true"
        android:gravity="center"
        app:dragOut="true"
        app:textColor="@color/black"
        app:textSize="12sp"
        />
```   
* 自定义Adapter
	只需要实现IWheelviewAdapter即可     
	``` java   
	interface IWheelviewAdapter {
	    fun getItemeTitle(i: Int): kotlin.String
	    val count: Int
	    operator fun get(index: Int): Any
	}
	```     
* 在代码中配置：
	``` java
	var provider: ArrayList<String> = ArrayList()
        provider.addAll(listOf("天津市", "北京市", "黑龙江省", "江苏省", "浙江省", "安徽省",
                "福建省", "江西省", "山东省", "河南省", "湖北省", "湖南省", "广东省"))
        val providerAdapter = WheelviewAdapter(provider)
        wheelView1?.setAdapter(providerAdapter)
    // 设置滚动监听
	    wheelView?.setWheelScrollListener(object : WheelView.WheelScrollListener {
	        override fun changed(selected: Int, name: Any) {
	            toast("$name:被选中了第" + selected)
	        }
	    })
	```

    ## 详细说明   
        请参考博客：http://blog.csdn.net/fwt336/article/details/76086360  

    欢迎star或fork
