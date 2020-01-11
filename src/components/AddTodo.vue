<template>
    <div>
        <form @submit="addTodo">
            <input type="text" name="title" placeholder="Add Todo ...." v-model="title">
            <input type="submit" value="Submit" class="btn">
        </form>
    </div>
</template>
<script>
export default {
    name:'AddTodo',
    data: () => ({
        title: ''
    })
}
</script>
<style scoped>
form{
    display: flex;
}
input[type="text"]{
    flex:10;
    padding: 5px;
}
input[type="submit"]{
    flex:2;
}

</style>