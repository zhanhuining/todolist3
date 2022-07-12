<template>
	<div class="todo-header">
        <input type="text" placeholder="请输入你的任务名称，按回车键确认" v-model="title" @keyup.enter="add"/>
    </div>
</template>

<script>
  import {nanoid} from 'nanoid'
	export default {
		name:'MyHeader',
    data() {
      return {
        title:''
      }
    },
    props:['addTodo'],
		//接收从Demo传递过来的addTodo
    methods: {
      add(){
        //校验数据
        if(!this.title.trim()) return alert('输入不能为空')
        //将用户输入生成一个对象
        const todoObj={id:nanoid(),title:this.title,done:false}
        //将新生成的对象传给App
        this.addTodo(todoObj)
        this.title=''
      }
    },
    
	}
</script>

<style scoped lang="less">
  .todo-header{
    width: 500px;
    height: 50px;
    border-bottom: 1px solid black;
     input{
       width: 480px;
       height: 30px;
       margin: 10px 0px 0px 5px;

     }
  }
</style>