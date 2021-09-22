<template>
<section class="todoapp">

  <header>
    <h1>Todo App</h1>
    <input type="text" class="new-todo" placeholder="add task" v-model="newTodo" @keyup.enter="addTodo">
  </header>

   <div class="main">

     <ul class="todo-list">
       <li class="" :key="todo" v-for="todo in todos" :class="{completed: todo.completed}">
         <div class="view">

            <input type="checkbox" class="toggle" v-model="todo.completed"/>
           <label>

             {{ todo.name }}

           </label>

         </div>

       </li>
     </ul>

   </div>

  <footer></footer>


</section>

</template>

<script>
export default {
  name: "Todos",
  data(){

       return{


              todos:[],
              newTodo:''
       }
  },

  methods:{

    addTodo()
    {
      this.todos.push({
          name:this.newTodo,
          completed : false
      });
      this.newTodo = '';

    }
  },

}
</script>

<style src="./todo.css">

</style>
