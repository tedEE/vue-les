<template>
  <div id="app" class="container">
      <h2 class="js-split">Список дел</h2>
      <add-todo @onSub="addInput" />
      <hr>
        <todo-list :todos="todos" @removeItem="removeItem"/>

  </div>
</template>

<script>
import Todo from '@/components/TodoList.vue'
import AddTodo from '@/components/AddTodo.vue'
import Splitter from 'split-html-to-chars'


export default {
  name: 'app',
    mounted(){
        let els = this.$el.querySelectorAll(".js-split");
        [].forEach.call(els, function(el) {
            // outerHTML, thats *important*, no direct text nodes should be in parsed HTML
            el.outerHTML = Splitter(el.outerHTML, '<span class="letter">$</span>');
        });
    },
    data(){
      return{
          todos : [
              {id:1, title:'Купить хлеб', complated:false},
              {id:2, title:'Купить масло', complated:false},
              {id:3, title:'Купить пиво', complated:false}
          ],
          obj : []
      }
    },
    methods : {
        removeItem(id){
            this.todos = this.todos.filter(t => t.id !== id)
        },
        addInput(e){
            this.todos.push(e)
        },
    },
    watch : {
        todos(){
            localStorage.setItem('todos', JSON.stringify(this.todos));
        }
    },
    created() {
        this.obj = JSON.parse(localStorage.getItem('todos'));
        this.todos = this.obj

    },

  components: {
      TodoList: Todo,
      AddTodo
  }
}
</script>

<style scoped>
    h2 {
        text-align: center;
        margin: 100px;
        font-size: 70px;
        text-transform: uppercase;
        letter-spacing: 8px;
    }

</style>
