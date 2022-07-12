<template>
  <div class="todo-footer" v-show="total!=0">
    <label>
      <input type="checkbox" :checked="isAll" @change="checkAll"/>
    </label>
    <span>
      <span>已完成{{doneTotal}}</span> / 全部{{total}}
    </span>
    <button class="btn btn-danger" @click="clearAll">清除已完成任务</button>
  </div>
</template>

<script>
export default {
  name: "MyFooter",
  props: ["todos", "checkAllTodo","clearAllTodo"],
  computed: {
    total() {
      return this.todos.length;
    },
    doneTotal() {
      return this.todos.reduce((pre, todo) => {
        return pre + (todo.done ? 1 : 0);
      }, 0);
    },
    isAll() {
      return this.total === this.doneTotal && this.total > 0;
    },
  },
  methods: {
    checkAll(e) {
      this.checkAllTodo(e.target.checked);
    },
	clearAll(){
		this.clearAllTodo();
	}
  },
};
</script>

<style scoped></style>
