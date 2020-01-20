# 控制反转表单变化逻辑
## [控制反转](https://blog.csdn.net/bestone0213/article/details/47424255)
简单说控制反转，可以不直接显示引用对象，而是交由容器，容器返回具体的对象。
## [策略模式](https://www.cnblogs.com/java-my-life/archive/2012/05/10/2491891.html)
通过策略模式，将每一个变化逻辑，封装为一个函数，在特定条件条件情况下，执行这段函数。而不是把所有的条件和变化逻辑写到一起。
## [组合模式](https://juejin.im/post/5bb730e96fb9a05d0c37e66b)
简单说明，把按文件和文件夹当作组合模式经典案例，多个文件可以被一个文件夹包裹。文件夹有文件上的api，这样api是批量操作，会对这些文件逐个进行操作。
```js
class Field {
  constructor() {
    this.showCondition = () => true; // 默认字段都展示
  }
  setShowCondition(showCondition) {
    this.showCondition = showCondition;
    return this;
  }
  show(context) {
    // 根据传入的上下文信息，决定该字段是否显示IOC
    return this.showCondition(context);
  }
}
```
```js
class Fields {
  constructor(fields) {
    this.fields = fields;
    this.showCondition = () => true; // 默认该组都展示
    this.containers = []; 
  }
  setShowCondition(showCondition) {
    this.showCondition = showCondition;
    return this;
  }
  // 组合模式的api
  show(context) {
    // 根据传入的上下文信息，决定该字段组是否显示
    return this.showCondition(context);
  }
  // 策略模式进行Field变化
  registerChangeField() {
    this.containers.push({
      condition,
      prop,
      converter
    });
    return this;   // 链式调用
  }
  // 重定义字段的表现，后期重新绑定
  redefinedField({ prop, converter }) {
    this.containers.unshift({
      condition: () => true,
      prop,
      converter
    });
    return this;
  }
}
```
```js
// 配置使用
new Fields([
  user,
  userInfo,
  new Fields([startTime, endTime]).setShowCondition((context) => context.isShowTime),  // Fields支持嵌套
]).redefinedField({
  prop: user.prop,               // 后期修改某个字段信息
  converter: (field) => {
    field.setShowCondition((context) => {
      return context.shouldShowUser
  })
}).registerChangeField({         // 根据情况进行变化
  prop: userInfo.prop,
  condition: (context) => context.isSetUserReuqired,
  converter: (field) => {field.setRequired()}
});
```
