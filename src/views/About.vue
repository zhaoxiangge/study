<template>
  <div class="about page">
    <input style="width: 100%" placeholder="下边输入框使用了自定义的全局指令 v-focus" type="number" name="" id="">
    <input type="number" name="" id="" v-focus>
    <input type="number" name="" id="" v-directivesTest1 v-directivesTest2>
    <h3><span>学到自定义指令,觉得可以用自定义指令 来实现 特定框,在inserted钩子函数中对元素本身做控制,比如按键事件控制能输入的范围,最大长度,以及其他控制(手机号框,放大镜框,双敲复核框...)</span></h3>
    <textarea name="" id="about" cols="90" rows="100">
      在编写组件时，最好考虑好以后是否要进行复用。一次性组件间有紧密的耦合没关系，但是可复用组件应当定义一个清晰的公开接口，同时也不要对其使用的外层数据作出任何假设。 Vue 组件的 API 来自三部分——prop、事件和插槽： Prop 允许外部环境传递数据给组件；
      事件允许从组件内触发外部环境的副作用； 插槽允许外部环境将额外的内容组合在组件中。 子组件引用 尽管有 prop 和事件，但是有时仍然需要在 JavaScript 中直接访问子组件。为此可以使用 ref 为子组件指定一个引用 ID。例如：

      <div id="parent">
        <user-profile ref="profile"></user-profile>
      </div>
      var parent = new Vue({ el: '#parent' }) // 访问子组件实例 var child = parent.$refs.profile 当 ref 和 v-for 一起使用时，获取到的引用会是一个数组，包含和循环数据源对应的子组件。
      $refs 只在组件渲染完成后才填充，并且它是非响应式的。它仅仅是一个直接操作子组件的应急方案——应当避免在模板或计算属性中使用 $refs。 对低开销的静态组件使用 v-once 尽管在 Vue 中渲染 HTML 很快，不过当组件中包含大量静态内容时，可以考虑使用
      v-once 将渲染结果缓存起来，就像这样： Vue.component('terms-of-service', { template: '\
      <div v-once>\
        <h1>Terms of Service</h1>\ ...很多静态内容...\
      </div>\ ' }) 全局混入 在main.js里使用了混入 //全局混入 Vue.mixin({ created: function () { //每个vue实例对象 都赋给 window下的全局变量,可以测试用; //如果每个组件的name都严格按照
      src下的 文件目录+文件名来命名,则可把所有vue实例赋给全局变量,每个组件都能方便使用其他vue实例 window['_' + this.$options.name + '_' + this._uid] = this; } })
      也可以全局注册混入对象。注意使用！ 一旦使用全局混入对象，将会影响到 所有 之后创建的 Vue 实例。使用恰当时，可以为自定义对象注入处理逻辑。 // 为自定义的选项 'myOption' 注入一个处理器。 Vue.mixin({
      created: function () { var myOption = this.$options.myOption if (myOption) { console.log(myOption) } } }) new Vue({
      myOption: 'hello!' }) // => "hello!"
    </textarea>
  </div>
</template>
<script>
  export default {
    name: 'viewsAbout',
    directives: {
      directivesTest1: {
        // 指令的定义
        bind: function (el) {
          el.addEventListener('focus', function () {
            console.log('获得了焦点 使用 局部 自定义指令 directivesTest1 的元素 ');
          })

        }
      },
      directivesTest2: {
        // 指令的定义
        bind: function (el) {
          el.addEventListener('blur', function () {
            console.log('失去焦点  使用 局部 自定义指令 directivesTest1 的元素');
          })
        }
      }
    }
  }
</script>
<style>
  #about {
    height: 1000px;
    width: 100%;
  }
</style>
