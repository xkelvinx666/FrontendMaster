# 字段与对应实现抽象
> 有时出现同一份表单内容，在不同环境下的展示交互ui不一样的问题(pc与手机端)，这是我们需要把字段后对应的ui组件进行进一步处理
## 后期绑定
因为字段申明是一个对象，代码引入的对象可以在使用之前针对动态组件进行修改
```js
// pc.entry.js
import PCUserChooser from 'components/user-chooser'
import {user} from 'config';
user.editComponent = PCUserChooser;
````
```js
// mobile.entry.js
import MobileUserChooser from 'components/mobile/user-chooser'
import {user} from 'config';
user.editComponent = MobileUserChooser;
````
## 重定义全局声明组件
在入口文件针对使用到的全局组件，进行重新声明。保证组件的可用性，且需要用同一套api
```js
// pc.entry.js
import PCUserChooser from 'components/user-chooser'
Vue.component('user-chooser', PCUserChooser);
````
```js
// mobile.entry.js
import MobileUserChooser from 'components/mobile/user-chooser'
Vue.component('user-chooser', MobileUserChooser);
````
