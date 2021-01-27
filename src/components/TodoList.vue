<template>
  <div class="container">
      <input 
        type="text" 
        name="" 
        id="" 
        placeholder="What's your todo ?" 
        class="todo-input"
        v-model="newTodo"
        @keyup.enter="addTodo"
        >

        <div 
        v-for="(todo , index) in todos" 
        :key="todo.id"
        class="todo-item"
        >

        <div class="todo-item-left">
            <div v-if="!todo.editing" @dblclick="editTodo(todo)" class="todo-item-lable">
                {{todo.title}}
            </div>
            <input v-else type="text" class="todo-item-edit" v-model="todo.title">
        </div>

        <div class="remove-item" @click="removeTodo(index)">
            &times;
        </div>
        </div>
        
        
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      newTodo:'',
      idForTodo:3,
      todos:[
          {
              'id': 1,
              'title': 'Finish Vue Screencast',
              'completed' : false,
              'editing' : false
          },
          {
              'id': 2,
              'title': 'Take Over World',
              'completed' : false,
              'editing' : false
          }
      ]
    }
  },
  methods:{
      addTodo(){
          if(this.newTodo.trim().length == 0){
              return
          }
          this.todos.push({
              id:this.idForTodo,
              title:this.newTodo,
              completed:false
          })

          this.newTodo = ''
          this.idForTodo++
      },
      editTodo(todo){
          alert("double click")
          todo.editing =true
      },
      removeTodo(index){
          this.todos.splice(index,1)
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style >
.container{
    margin: 0 auto;
    width: 500px;
}
.todo-input{
    width: 100%;
    padding: 10px 18px;
    font-size: 18px;
    margin-bottom: 16px;
}

.todo-item{
    margin-bottom: 17px;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.remove-item{
    cursor: pointer;
    margin-left: 14px;
}
.todo-item-left{
    display: flex;
    align-items: center;
}
.todo-item-edit{
    font-size: 20px;
    color: #2c3e50;
    margin-left: 12px;
    width: 100%;
    padding: 10px;
    border: 1px solid #ccc;
    font-family: Arial, Helvetica, sans-serif;

}

</style>
