<template>
    <div id="app">
        <!--  @click="removeTodo(todo.id)" -->
        <div v-for="todo in todos" :key="todo.id"
            :class="{ item: true, checked: todo.isChecked }">
            <div @click="changeStatus(todo.id)" :class="{ check: true, ed: todo.isChecked }"></div>
            <div class="content">
                <div class="title">{{ todo.name }}</div>
                <div class="description">{{ todo.description }}</div>
            </div>
        </div>
    </div>
</template>

<style scoped>
#app {
    display: flex;
    align-items: center;
    justify-content: start;
    width: 100vw;
    height: 90vh;
    flex-wrap: wrap;
    flex-direction: column;
    color: white;
}

#app .item {
    width: 100%;
    padding: 10px;
    display: flex;
    gap: 10px;
    align-items: center;
    justify-content: center;
}

#app .item .content {
    transition: all .3s;
    width: 70%;
    height: 60px;
    border-radius: 10px;
    cursor: pointer;
    position: relative;
    display: flex;
    align-items: start;
    justify-content: center;
    flex-direction: column;
    padding: 10px;
    background-color: #436fff27;
}

#app .item .content .title {
    transition: all .3s;
    font-family: 1.5rem;
    font-weight: bolder;
    color: #3f7cff;
}

#app .item .content .description {
    transition: all .3s;
    font-size: 1rem;
    color: #5c82ff;
}

.check {
    width: 40px;
    height: 40px;
    border-radius: 100%;
    background-color: #3f7cff;
    position: relative;
    cursor: pointer;
}

.check::after {
    content: "";
    width: 20px;
    height: 20px;
    border-radius: 100%;
    background-color: white;
    position: absolute;
    top: 10px;
    right: 10px;
    z-index: 111;
}
.check.ed{
    background-color: #b55bff;
}
#app .item.checked .content {
    background-color: #d07fff2a;
}
#app .item.checked .title {
    color: #b55bff;
}
#app .item.checked .description {
    color: #d097ff;
}
</style>

<script>
export default {
    name: 'TodoList',
    props: {
        todos: {
            type: Array
        }
    }, methods: {
        removeTodo(todoId) {
            this.$emit('removeTodo', todoId)
        },
        changeStatus(todoId) {
            this.$emit('changeStatus', todoId)
        }
    }
}
</script>