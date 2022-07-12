<template>
  <div class="list">
    <ul>
       <li v-for="v in todos" :key="v.id"  @mouseenter="enter(v.id)" @mouseleave="leave(v.id)" >
        <!-- {{v.title}} -->
             <label>
                <input type="checkbox" :checked="v.done" @change="handleCheck(v.id)"/>
                <span>{{v.title}}</span>
             </label>
             <button class="btn btn-danger" @click="handleDelete(v.id)" v-show="flag">删除</button>
       </li>
    </ul>
  </div>
</template>

<script>
	export default {
    data(){
      return{
              flag:false
      }
    },
    props:['todos','checkTodo','deleteTodo'],	//接收
    methods: {
      // enter(id){
      //   for(let i=0;i<this.todos.lenght;i++){

      //       console.log(this.todos[i].id); 
      //   //     if(id===this.todos[i].id) {
      //   //        this.flag=true
      //   //     }
      //   //     else{
      //   //        this.flag=false
      //   //     }
      //        }
      // },
       enter(id){
          this.flag=true
       },
      leave(id){
        this.flag=false
      },
    //通知demo
    handleCheck(id){
        this.checkTodo(id)
    },
    handleDelete(id){
      if(confirm('确定删除吗？')){
          this.deleteTodo(id)
      }
    }
  },
   
		
	}
</script>

<style scoped lang="less">
  .list{
    width: 500px;
    height: 200px;
    background: #aaa;
  }
</style>