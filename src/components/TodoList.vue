<template>
  <div>
    <transition-group name="list" tag="ul"> 
      <li v-for="(todoItem, index) in this.storedTodoItems" v-bind:key="todoItem.item" class="shadow">
        <!-- propsdata대신 this.$store.state.todoItems으로 변경: store파일에 todoItems접근을 위해 -->
        <i class="chkBtn fas fa-check" v-bind:class="{chkBtnCom: todoItem.completed}" v-on:click="toggleComplete({todoItem, index})"></i>
        <span v-bind:class="{textCom: todoItem.completed}">{{ todoItem.item }}</span>
        <!-- <button v-on:click="removeTodo">Delete</button> -->
        <span class="removeBtn" v-on:click="removeTodo({todoItem, index})">
          <i class="fas fa-trash-alt"></i>
        </span>
      </li>
    </transition-group>
  </div>
</template>

<script>
import { mapGetters, mapMutations } from 'vuex';
//mapGetters, mapMutations에 접근 가능 하도록

export default {
  methods: {
    ...mapMutations({
      removeTodo: 'removeOneItem',
      toggleComplete: 'toggleOneItem'
    }),
    //removeOneItem 하나로 받기 때문에 (todoItem, index)없이 위에 removeTodo(todoItem, index) 각각 받았던 것을 removeTodo({todoItem, index}) 객체로 묶어서 받는다
    //toggleComplete도 removeOneItem과 같다

    // removeTodo(todoItem, index) {
    //   this.$store.commit('removeOneItem', {todoItem, index});
    // },
    // toggleComplete(todoItem, index) {
    //   this.$store.commit('toggleOneItem', {todoItem, index});
    // }
  },
  computed: {
    // TodoItems() {
    //   return this.$store.getters.storedTodoItems;
    // }
    ...mapGetters(['storedTodoItems'])
  }
}
</script>


<style scoped>
  ul {
    list-style: none;
    padding-left: 0;
    margin-top: 0;  
    text-align: left;
  }
  li {
    display: flex;
    min-height: 50px;
    height: 50px;
    line-height: 50px;
    margin: 0.5rem 0;
    padding: 0 0.9rem;
    background: #fff;
    border-radius: 5px;
  }
  .chkBtn {
    line-height: 45px;
    color: #62acde;
    margin-right: 5px;
  }
  .chkBtnCom {
    color: #b3adad;
  }
  .textCom {
    text-decoration: line-through;
    color: #b3adad;
  }
  .removeBtn {
    margin-left: auto;
    color: #de4343;
  }

  .shadow {
    box-shadow: 5px 10px 10px rgba(0, 0, 0, .03);
  }

  /* 리스트 아이템 트랜지션 효과 */
  .list-enter-active, .list-leave-active {
    transition: all 1s;
  }
  .list-enter, .list-leave-to /* .list-leave-active below version 2.1.8 */ {
    opacity: 0;
    transform: translateY(30px);
  }
</style>