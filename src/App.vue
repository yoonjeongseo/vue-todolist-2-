<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput></TodoInput>
    <!-- app.vue에서는 내용을 표시할 뿐 데이터를 직접 받거나 할 필요가 없기 때문 -->
    <TodoList></TodoList>


    <TodoFooter></TodoFooter>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'



export default {
  // data() {
  //   return {
  //     todoItems: [] 
  //   }
  // }, 
  //state를 store에서 관리해서 필요가 없다
  methods: { //mutations와 같다.

    //store.js 파일로 넘김
    // addOneItem(todoItem) {
    //   const obj = {completed: false, item: todoItem};
    //   localStorage.setItem(todoItem, JSON.stringify(obj)); 
    //   this.todoItems.push(obj); 
    // }, 
    // removeOneItem(todoItem, index) {
      
    //   localStorage.removeItem(todoItem.item);
    //   this.todoItems.splice(index, 1);
    // },
    // toggleOneItem(todoItem, index) {
      

    //   this.todoItems[index].completed = !this.todoItems[index].completed;

    //   localStorage.removeItem(todoItem.item);
    //   localStorage.setItem(todoItem.item, JSON.stringify(todoItem));
    // },
    // clearAllItem() {
    //   localStorage.clear();

    //   this.todoItems = [];
    // }
  },
  components: {
    TodoHeader,
    TodoInput,
    TodoList,
    TodoFooter
  }
}
</script>

<style>
  body {
    text-align: center;
    background-color: #f6f6f6;
  }
  input {
    border-style: groove;
    width: 200px;
  }
  button {
    border-style: groove;
  }
  .shadow {
    box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03);
  }
</style>
