# 前端开发规范
## 约束大于遵守
> 每个团队都有各自的规范。细微的不同，也不保证代码审核阶段能查阅出，而且这对查阅者的工作增加了非常不必要的负担。

直接使用强制约束，不符合不予代码commit
## eslint
eslint可以保证代码的严格规范

1. eslint规则配置使用需要注意和团队规范达成一致
2. eslint配置时需要与项目的开发框架对应

## prettier

eslint更多是保证编码的实现写法和减少无效代码，prettier更能管控项目代码的编码风格
[eslint和prettier组合](https://github.com/prettier/prettier-eslint)
## git commit hook
git支持特定动作下执行钩子函数，可以在git commit阶段，对需要提交的部分代码进行eslint，保证每次提交的内容都是经过检查的。
1. npm安装[yorkie](https://www.npmjs.com/package/yorkie)
2. package.json增加以下声明
```
"gitHooks": {
  "pre-commit": "lint-staged"
},
"lint-staged": {
  "*.js": [
    "eslint",
    "git add"
  ]
}
```

*只有安装了node_modules才有效*
