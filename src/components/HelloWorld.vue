<template>
  <div>
      <div class="row">
          <div class="col-md-12">
              <div class="well">
                  <h2>Create a New Todo</h2>
                  <form>
                      <div class="form-group">
                          <label for="todoitem">Todo Item</label>
                          <input type="text" v-model="input.text" class="form-control" id="todoitem" placeholder="Todo Item" />
                      </div><br>
                      <button type="button" v-on:click="add()" class="btn btn-default">Create</button>
                  </form>
              </div>
          </div>
      </div>
      <div class="row">
          <div class="col-md-12">
              <h2>List</h2>
              <ul class="list-group">
                  <li v-for="(todo, index) in todos" :key="index" class="list-group-item" v-on:click="complete(index)" v-bind:class="{completeToDo: todo.isComplete}">
                      {{ index + 1 }} : {{ todo.text }}, Hello!!!
                  </li>
              </ul>
          </div>
      </div>
  </div>
</template>

<script>
export default {
    name: "Todo",
    data () {
        return {
            todos: [],
            input: {}
        }
    },
    methods: {
        add() {
            this.input.isComplete = false;
            this.todos.push(this.input);
            this.input = {};
        },
        complete(index) {
          for(var i=0; i<this.todos.length; i++){
            if(i==index) {
              this.todos[index].isComplete=true;
            }
          }
          this.input = {};
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  /*display: inline-block;*/
  margin: 10px 10px;
}
a {
  color: #42b983;
}
.completeToDo {
  text-decoration: line-through;
}
</style>
