<template>
    <form @submit.prevent="onSubmit">
        <input type="text" class="form-control" v-model="title">
        <button type="submit" class="btn btn-primary">Добавить</button>
    </form>
</template>

<script>

    export default {
        data(){
            return {
                title : '',
                newTodo : {}
            }
        },
        methods : {
            onSubmit(){
                if (this.title.trim()){
                     this.newTodo = {
                        id : Date.now(),
                        title : this.title,
                        complated:false
                    }
                }
                this.$emit('onSub', this.newTodo);
                this.title = ''
            }
        }
    }
</script>

<style scoped>
    form {
        margin-top: 30px;
        display: flex;
    }
    .form-control{
        width: 40%;
    }
</style>
