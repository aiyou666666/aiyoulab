                                     kami+yo的使用 


 **## 1.yo和kami  ##**
> 1.1 yo是使用sass开发的css框架 适用于移动端 同时也适用于pc端的高级浏览器
 
> 1.2 kami是基于yo开发的js组件库

 **## 2.使用时产生的问题  ##**
    <div style="backgound:#000;font-size:15px">
        <h3>
         关于滑动列表触发连接跳转的问题
       </h3>
       <p>
        问题描述:当使用 kami组件时，滑动列表，会很容易触发tap事件
      </p>
      <p>
         问题解决方案:
          局部滚动的时候 触发的是scroll事件，这个时候去除父级元素的touchstart冒泡事件，可以防止滚动的时候跳转页面如代码:
          <code>
               父级元素.addEventListener("touchstart", function(e){
                     e.stopPropagation();
              }, false);    
          </code>
      </p> 
    <h3>关于弹出框选取不了正确值得问题</h3>
    <p>
      问题描述:当使用kami日历组件的时候，时间跨度（比如年）比较大的时候 选取值不准确
   </p> 
   <p>
     问题解决方案:
      问题的根源是在使用了rem去做单位 导致了换算成px的时候有小数点问题，这个时候应该不用rem去做单位 改为px 如代码：
     <code>
       @include yo-select($item-height: 38px) {
             color: #333;
             font-size: 16px;
             width: 100%;
         > .unit {
            display: none;
          }
        };
     </code>
   </p>
   <p>
    <h3>不触发点击事件的问题</h3>
   </p>
  <p>
     问题描述:当使用阉割版本的zepto的时候 不触发tap事件
  </p>
  <p>
    问题的解决方案:
    问题在于阉割版zepto没有封装tap事件,kami底层对tap事件封装过，这个时候只需要引入kami组件就ok!
  </p>
   <p>
    <h3>关于使用kami点击击穿的问题</h3>
    <p>
      问题描述:当选择日历 选择确认或取消的时候 会触发底部input textare等的点击事件
      问题的解决方案:不使用tap事件 使用click事件 然后使用fastclick去除click事件300ms延迟
    </p>
  </p>
   ## **3.kami封装了那些组件** ##
   <p>
     kami主要封装了日历，对话框，搜索，toast,下载提示框，图片懒加载，滑动选择框，列表，面板(panel),模板等，详细请访问 http://ued.qunar.com/kami/demo/index.html
  </p>
   

 </div>
