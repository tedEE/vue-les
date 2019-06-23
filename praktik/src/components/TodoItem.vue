<template>
    <li>
        <span :class="{done : todo.complated}">
                <div class="pretty p-default p-round p-smooth">
                    <input type="checkbox" @change="todo.complated = !todo.complated"/>
                     <div class="state p-primary">
                        <label>
                            <strong>{{index + 1}}</strong>
                            <span class="label-text" :class="{done : todo.complated}">{{todo.title}}</span>
                        </label>
                     </div>
                </div>


        </span>
        <button type="button" class="btn btn-danger rm" @click="removeTodo">&times;</button>
    </li>
</template>

<script>

    export default {
        name: 'item',
        props: ['todo', 'index'],
        data() {
            return {}
        },
        methods: {
            removeTodo(){
                this.$emit('removeTodo', this.todo.id)
            }
        },

        components: {}
    }
</script>
<style scoped>
    li {
        margin-top: 20px;
        border: 1px solid #ccc;
        display: flex;
        justify-content: space-between;
    }
    span {
        padding: 10px;
    }
    .done {
        text-decoration: line-through;
    }

</style>

