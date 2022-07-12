<template>
  <div id="root">
    <div class="todo-container">
      <div class="todo-wrap">
        <MyHeader :addTodo="addTodo"></MyHeader>
        <!--      表单             //勾选或取消勾选一个todo      删除 -->
        <MyList :todos="todos" :checkTodo="checkTodo" :deleteTodo="deleteTodo"></MyList>
        <!--      表单             //全选或全不选               清除所有已完成todo -->
        <MyFooter :todos="todos" :checkAllTodo="checkAllTodo" :clearAllTodo="clearAllTodo"></MyFooter>
      </div>
    </div>
  </div>
</template>
<script>
import MyHeader from "../components/Header.vue";
import MyList from "../components/List.vue";
import MyFooter from "../components/Footer.vue";

export default {
  components: { MyHeader, MyList, MyFooter },
  data() {
			return {
				todos:[
					{id:"001",title:"抽烟",done:true},
					{id:"002",title:"喝酒",done:false},
					{id:"003",title:"开车",done:true}
				]
			}
	},
  methods:{
    //添加todo
    addTodo(todoObj){
      this.todos.unshift(todoObj)
    },
    //勾选或取消勾选一个todo
    checkTodo(id){
      //遍历todo
      this.todos.forEach((todo)=>{
        if(todo.id===id) todo.done=!todo.done
      })
    },
    deleteTodo(id){
      this.todos = this.todos.filter((todo)=>{
        return todo.id !== id
      })
    },
    //全选或全不选
    checkAllTodo(done){
      this.todos.forEach((todo)=>{
        todo.done = done
      })
    },
    //清除所有已完成todo
    clearAllTodo(){
      this.todos = this.todos.filter((todo)=>{
        return !todo.done
      })
    }
  }
};
</script>

<style></style>
