<template>
    <div class="todo-list">
        <ul>
            <item v-for="(todo,index) in todos"
                    :todo="todo"
                    :index="index"
                    @removeTodo="removeItem"
            ></item>
        </ul>
    </div>
</template>

<script>
    import Item from '@/components/TodoItem.vue'
    export default {
        name: 'list',
        props : ['todos'],
        data(){
            return{

            }
        },
        methods : {
            removeItem(id){
                this.$emit('removeItem', id)
            }
        },

        components: {
            Item
        }
    }
</script>

<style scoped>
    ul{
        list-style: none;
        margin: 0;
        padding: 0;
    }
</style>
