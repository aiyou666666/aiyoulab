##angular 技巧汇总

##### 1. angular 两个指令之间调用复用代码 require####

<div style="background:#000;color:#fff; padding:10px;padding-left:50px" >
var app = angular.modeule('myapp',[]);

app.directive('common',function(){
    <br>return {
    <br>...
    <br>controller: function($scope){
       <br> this.method1 = function(){
       <br> };
       <br> this.method2 = function(){
       <br> };
   <br> },
   <br> ...
   <br> }
<br>});

<br>app.directive('d1',function(){
  <br>  return {
  <br>  ...
   <br> require: '?^common',
   <br> link: function(scope,elem,attrs,common){
    <br>    scope.method1 = common.method1;
     <br>   ..
     <br>   },
   <br> ...
   <br> }
<br>});

<br>app.directive('d2',function(){
  <br>  return {
  <br>  ...
 <br>   require: '?^common',
 <br>   link: function(scope,elem,attrs,common){
  <br>      scope.method1 = common.method1;
  <br>      ..
  <br>      },
  <br>  ...
   <br> }
});
</div>
####2.