
<script>
import MyHeader from "@/components/MyHeader.vue";
import MyFooter from "@/components/MyFooter.vue";
import MyList from "@/components/MyList.vue";

export default {
  components: {MyFooter, MyList, MyHeader},
  data(){
    return{
      Todos:[
        {
          id: '001',
          name: '吃饭',
          completed: true
        },
        {
          id: '002',
          name: '编程',
          completed: false
        },
        {
          id: '003',
          name: '打豆豆',
          completed: true
        }
      ]
    }
  },
  methods:{
    removeTodo(id){
      // filter返回的
      this.Todos = this.Todos.filter(todo =>{
        return todo.id !== id
      })
    },

    removalsCompleted(){
      this.Todos = this.Todos.filter(todo => !todo.completed)
    }
  }

}
</script>

<template>
  <div>
<!--    传递的是这个列表的引用-->
    <my-header :todos="Todos"></my-header>
    <my-list :todos="Todos" :removeTodo = "removeTodo" ></my-list>

    <my-footer :todos="Todos" :removalsCompleted="removalsCompleted"></my-footer>

  </div>
</template>

<style>
/*base*/
body {
  background: #fff;
}

.btn {
  display: inline-block;
  padding: 4px 12px;
  margin-bottom: 0;
  font-size: 14px;
  line-height: 20px;
  text-align: center;
  vertical-align: middle;
  cursor: pointer;
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.2), 0 1px 2px rgba(0, 0, 0, 0.05);
  border-radius: 4px;
}

.btn-danger {
  color: #fff;
  background-color: #da4f49;
  border: 1px solid #bd362f;
}

.btn-edit {
  color: #4b83c0;
  background-color: #4b83c0;
  border: 1px solid #3b72b0;
}

.btn-danger:hover {
  color: #fff;
  background-color: #bd362f;
}

.btn:focus {
  outline: none;
}

.todo-container {
  width: 600px;
  margin: 0 auto;
}
.todo-container .todo-wrap {
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 5px;
}
</style>