# vue-gecode

## 基于Vue2.0获取手机验证码插件,可高度自定义.



[这里是可爱的Demo](https://gesnowboy.github.io/vue-gecode/)


## 安装和使用

```javascript
npm install vue-gecode --save-dev
```

- 作为全局组件使用

```javascript
//在项目入口文件
import Vue from 'vue'
import geCode from 'vue-gecode'
Vue.component('geCode', geCode)
```

- 作为局部组件

```javascript
//在某个组件中
import geCode from 'vue-gecode'
export default {
  components: {
    geCode
  }
}
```

HTML中使用:

```html
<template>
	<ge-code :config=config></ge-code>
</template>

<script>
export default {
	data(){
	  return {
	    config:{
	      //开始时候的文本
	      startText: '获取验证码',
	      //获取验证码结束后文本
	      endText: '再次获取',
	      //验证码倒计时总时间(秒)
	      totalTime: 60,
	      //验证码每次隔多久变一次(秒)
	      tickTime: 1,
	      //自定义倒计时期间文本的显示内容
	      computeText(num){
	        return '重新获取 ' + num + 's';
	      },
	      //是否可以发送 
	      canTodo: () => {
	        return /^1[345678]\d{9}$/.test(15232509223);
	      },
	      //canTode验证成功后执行 发送短信验证码
	      todo: () => {
	        //这里写验证码的获取程序
	      }
	    }
	  }
	}
}

</script>
```



## 运行demo


```javascript
//1. 下载代码
git clone https://github.com/GeSnowBoy/vue-gecode.git

//2. 进入目录
cd vue-gecode

//3. 安装依赖
npm install

//4. 运行demo
npm start
```

## API

### Props

| 参数    | 类型    | 说明   |  是否必须 | 默认值 |
| ------------- |-------| -----| ----| -------|
| config | 对象 | 唯一配置参数,详情见下 | 是 | — |

### config属性说明

| 参数    | 类型    | 说明   |  是否必须 | 默认值 |
| ------------- |-------| -----| ----| -------|
| startText | 字符串 | 未输入时显示文字 | 否 | 获取验证码 |
| endText | 字符串 | 验证码发送完成后显示文字 | 否 | 再次获取 |
| computeText | 函数 | 每次时间减少显示的文字,参数为剩余时间 | 否 | 默认返回->重新获取 * s |
| activeClass | 字符串 | 验证码倒计时添加的类名 | 否 | isRun |
| totalTime | 数值 | 获取验证码后的倒计时总数(s) | 否 | 60 |
| tickTime | 数值 | 每次减少的时间(s) | 否 | 1 |
| canTodo | 函数 | 判断是否可以发送验证码 | 否 | — |
| todo | 函数 | 验证成功后调用,在这里发送验证码 | 否 | - |
| endCallback | 函数 | 验证码结束回调 | 否 | - |
| click | 函数 | 每次点击都会被调动 | function | - |
| canUse | 布尔值 | 是否可用 | 否 | true |
| click | 字符串 | 不可用时添加的类名 | 否 | no-can |
