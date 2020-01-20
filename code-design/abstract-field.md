# 业务字段抽象

> 表单做的好，下班下的早
>
## 动态组件

动态组件作为具体实现，可以让两个实现(组件)之间不直接依赖。

> [Vue动态组件](https://cn.vuejs.org/v2/guide/components-dynamic-async.html) [JSX](https://zh-hans.reactjs.org/docs/introducing-jsx.html)

## 渲染模版
通过编写渲染模版，可以通过配置让对应映射渲染组件，只需传入配置和数据，模版渲染的表单即可自动和组件绑定
```js
const endTime = {
  key: 'end_time',                // 数据结构中的key
  label: '结束时间',               // 表单展示时的中文标签
  type: 'datetime',               // 表单渲染时，所渲染的对应类型
  disabled: true,                 // 是否禁用此选项
  placeholder: '2020-01-20',      // 默认placeholder提示文字
  required: true,                 // 该字段是否必填
  editComponent: undefined,        // 编辑型表单的动态组件
  listComponent: undefined        // 展示型表单(表格)的动态组件
}
```
```vue
<template>
    <el-form>
        <template v-for="{key, label, type, disabled, placeholder, required, editComponent} in configs">
            <el-form-item :key="key" :label="label" :required="required">
              <component v-if="editComponent" :is="editComponent" v-model="params[key]"></component>
              <el-date-time-picker 
                v-else-if="type === 'datetime'" 
                v-model="params[key]" 
                :disabled="disabled" />
                <!--省略其他-->
            </el-form-item>
        </template>
    </el-form>
</template>
<script>
export default {
    props: {
        configs: {
          type: Array,
          required: true
        },
        params: {
          type: Object,
          required: true
        }
    }
}
</script>
```
