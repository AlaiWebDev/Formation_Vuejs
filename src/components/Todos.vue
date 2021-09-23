<template>
<section class="todoapp">

  <header>
    <h1>Todo App</h1>
    <input type="text" class="new-todo" placeholder="add task" v-model="newTodo" @keyup.enter="addTodo">
  </header>

   <div class="main">

     <ul class="todo-list">
       <li class="" :key="todo" v-for="todo in filterTaskbyState" :class="{completed: todo.completed}">
         <div class="view">

            <input type="checkbox" class="toggle" v-model="todo.completed"/>
           <label>

             {{ todo.name }}

           </label>

         </div>

       </li>
     </ul>

   </div>

  <footer>
    <div class="select-filter">
      <div>
  <input type="radio" id="all" name="filter" value="all" v-model="selectedState"
         checked>
  <label for="all">All</label>
</div>
<div>
  <input type="radio" id="completed" name="filter" value="completed" v-model="selectedState">
  <label for="completed">Completed</label>
</div>

<div>
  <input type="radio" id="uncompleted" name="filter" value="uncompleted" v-model="selectedState">
  <label for="uncompleted">Uncompleted</label>
</div>
    </div>
  </footer>


</section>

</template>

<script>
export default {
  name: "Todos",
  data(){

       return{

              todos:[],
              newTodo:'',
              selectedState: "All"
       }
  },

  methods:{

    addTodo()
    {
      this.todos.push({
          name: this.newTodo,
          completed: false
      });
      this.newTodo = '';

    }
  },
  computed: {
    filterTaskbyState: function() {
      if (this.selectedState === "completed") {
        return this.todos.filter(todo => todo.completed);
      }
      if (this.selectedState === "uncompleted") {
        return this.todos.filter(todo => !todo.completed);
      } else {
        return this.todos;
      }
    }
  }

}
</script>

<style src="./todo.css">

</style>
