<template>
  <div class="container">
    <div class="breakpoint">
      <h1>调试</h1><br>
      <div>
        <h3>代码行断点</h3>
        <button type="button" @click="lineCodeBreakPoint1">最简单的断点-点击Source的左侧行号</button>
        <button type="button" @click="lineCodeBreakPoint2">手动加"debugger"</button>
      </div>
      <div>
        <h3>条件断点 --- value为2时触发断点</h3>
        <button type="button" @click="conditionalBreakpoint(1)">触发同一函数，传值1</button>
        <button type="button" @click="conditionalBreakpoint(2)">触发同一函数，传值2</button>
      </div>
      <div>
        <h3>DOM断点</h3>
        <button type="button" @click="subtreeModification('add')">子树增加DOM</button>
        <button type="button" @click="subtreeModification('remove')">子树移除DOM</button>
        <div style="background-color: yellow">-- 测试开始 --</div>
        <div title="给这个元素加子树修改断点">
          <div ref="subtreeModification">
            测试子树的元素增/删DOM
          </div>
        </div>
        <div style="background-color: yellow">-- 测试结束 --</div>
        <button type="button" @click="attributeModification">节点属性修改</button>
        <div style="background-color: yellow">-- 测试开始 --</div>
        <div ref="attributeModification" title="给这个元素加属性修改断点">
          测试节点属性修改
        </div>
        <div style="background-color: yellow">-- 测试结束 --</div>
        <button type="button" @click="domRemoval">节点移除</button>
        <div style="background-color: yellow">-- 测试开始 --</div>
        <div ref="domRemoval" title="给这个元素加元素移除断点">
          测试当前元素移除
        </div>
        <div style="background-color: yellow">-- 测试结束 --</div>
      </div>
      <div>
        <h3>XHR断点-"unpkg.com"</h3>
        <button type="button" @click="xhrBreakpoint">XHR断点</button>
      </div>
      <div>
        <h3>事件触发断点-复制</h3>
        <div>复制这里</div>
      </div>
      <div>
        <h3>异常断点</h3>
        <button type="button" @click="throwException" >触发抛异常</button>
      </div>
      <div>
        <h3>debug函数断点</h3>
        <button type="button" @click="debugFunction" >触发函数执行</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {

  mounted() {
    document.addEventListener('copy', this.copyFire);
  },
  methods: {
    lineCodeBreakPoint1() {
      const test = '这是常量，断点在这里的时候可以看到当前上下文';

      console.log('要断点在这里');

      console.log(test);
    },
    lineCodeBreakPoint2() {
      const test = '这是常量，断点在这里的时候可以看到当前上下文';

      debugger;

      console.log(test);
    },
    conditionalBreakpoint(value) {
      const test = '这是常量，断点在这里的时候可以看到当前上下文';
      
      console.log('value ==== 2 为条件断点');
      console.log(value);

      console.log(test);
    },
    subtreeModification(type) {
      if (type === 'add') {
        const span = document.createElement('span');
        span.style.color = 'red';
        span.innerText = '增加的元素';
        const test = '这是常量，断点在这里的时候可以看到当前上下文';
        this.$refs.subtreeModification.appendChild(span);
        console.log(test);
      } else if (type === 'remove') {
        const span = this.$refs.subtreeModification.children && this.$refs.subtreeModification.children[0];
        if (span) {
          const test = '这是常量，断点在这里的时候可以看到当前上下文';
          span.remove();
          console.log(test);
        }
      }
    },
    attributeModification() {
      const test = '这是常量，断点在这里的时候可以看到当前上下文';
      this.$refs.attributeModification.setAttribute('style', `color: rgb(${255 * Math.random().toString()}, ${255 * Math.random().toString()}, ${255 * Math.random().toString()})`);
      console.log(test);
    },
    domRemoval() {
      const test = '这是常量，断点在这里的时候可以看到当前上下文';
      this.$refs.domRemoval.remove();
      console.log(test);
    },
    async xhrBreakpoint() {
      const test = '这是常量，断点在这里的时候可以看到当前上下文';
      const cssFile = await fetch('https://unpkg.com/@highlightjs/cdn-assets@11.3.1/styles/default.min.css');
      console.log(test);
      return cssFile;
    },
    copyFire(e) {
      const test = '这是常量，监听复制事件断点在这里的时候可以看到当前上下文';
      console.log(e, test);
    },
    throwException() {
      const test = '这是常量，监听复制事件断点在这里的时候可以看到当前上下文';

      const exception = new Error('自定义异常名称');

      console.log(exception, test);
      throw exception;
    },
    debugFunction() {
      const test = '这是常量，监听复制事件断点在这里的时候可以看到当前上下文';

      debugger
      // 断点住之后，在控制台输入 debug(this.throwException)
      this.throwException();
      
      console.log(test);
    }
  },
  
  unmounted() {
    document.removeEventListener('copy', this.copyFire);
  }
}
</script>

<style lang="less" scoped>
.container {
  padding: 30px;
}
</style>