## Setting Up The Infrastructure
让我们一起为我们的$watchCollection函数在scope上做一个备份

这个方法大部分很会与$watch非常的相似：用一个watch方法返回我们需要watch的值，用一个listener来监听值得变化。在其内部其实是使用了$watch方法，来支持自身的watch与listener方法，如下所示：


```js
Scope.prototype.$watchCollection =        function(watchFn, listenerFn) {
        var internalWatchFn = function(scope)         {
        };
         var internalListenerFn = function() {
         };
         return this.$watch(internalWatchFn,      internalListenerFn);
         }；
```
As you may recall, the $watch function returns a function with which the watch can be removed. By returning that function directly to the original caller, we also enable this possibility for $watch- Collection.
回想一下，$watch方法返回了一个

让我们同样也做一个测试模块，就像我们在之前的章节中做的一样。他需要是一个包含最高级描述嵌套的describe模块


```js
describe('$watchCollection', function() {
var scope;
beforeEach(function() {
  scope = new Scope();
}); });
```