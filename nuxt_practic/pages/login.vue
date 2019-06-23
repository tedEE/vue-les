<template>
    <section>
        <h1>Login Page</h1>
        <form >
            <div class="form-group">
                <input type="text" class="form-control">
            </div>
            <p>
                <nuxt-link to="/">to home page</nuxt-link>
            </p>
            <button class="btn-primary btn" type="submit">Login</button>
        </form>
    </section>
</template>
<script>
    export default {
        layout: 'empty'
    }
</script>
<style scoped>
    form{
        width: 500px;
        margin: 0 auto;
    }
    h1{
        text-align: center;
        margin-top: 50px;
        margin-bottom: 20px;
    }

</style>
