<template>
    <div id="app">
        <div class="header">
            <h1>Todo Sheet</h1>
            <div class="hello">hello {{ firstName }}.</div>
        </div>
        <div class="days">
            <div @click="changeDay" ref="SA" class="day active">Saturday
                <div v-if='todos.some(todo => todo.day == "SA" && todo.isChecked == false)' class="red-point">
                    {{ todos.filter((todo) => todo.day == "SA" && todo.isChecked == false).length }}
                </div>
            </div>
            <div @click="changeDay" ref="SU" class="day">Sunday <div
                    v-if='todos.some(todo => todo.day == "SU" && todo.isChecked == false)' class="red-point">
                    {{ todos.filter((todo) => todo.day == "SU" && todo.isChecked == false).length }}
                </div>
            </div>
            <div @click="changeDay" ref="MO" class="day">Monday <div
                    v-if='todos.some(todo => todo.day == "MO" && todo.isChecked == false)' class="red-point">
                    {{ todos.filter((todo) => todo.day == "MO" && todo.isChecked == false).length }}
                </div>
            </div>
            <div @click="changeDay" ref="TU" class="day">Tuesday <div
                    v-if='todos.some(todo => todo.day == "TU" && todo.isChecked == false)' class="red-point">
                    {{ todos.filter((todo) => todo.day == "TU" && todo.isChecked == false).length }}
                </div>
            </div>
            <div @click="changeDay" ref="WE" class="day">Wednesday <div
                    v-if='todos.some(todo => todo.day == "WE" && todo.isChecked == false)' class="red-point">
                    {{ todos.filter((todo) => todo.day == "WE" && todo.isChecked == false).length }}
                </div>
            </div>
            <div @click="changeDay" ref="TH" class="day">Thursday <div
                    v-if='todos.some(todo => todo.day == "TH" && todo.isChecked == false)' class="red-point">
                    {{ todos.filter((todo) => todo.day == "TH" && todo.isChecked == false).length }}
                </div>
            </div>
            <div @click="changeDay" ref="FR" class="day">Friday <div
                    v-if='todos.some(todo => todo.day == "FR" && todo.isChecked == false)' class="red-point">
                    {{ todos.filter((todo) => todo.day == "FR" && todo.isChecked == false).length }}
                </div>
            </div>
        </div>
        <div v-for='todo in todos.filter((todo) => todo.isChecked == false)' :key="todo.id" v-show="todo.day == day"
            :class="{ item: true, checked: todo.isChecked }">
            <div @click="changeStatus($event, todo.id)" :class="{ check: true, ed: todo.isChecked }"></div>
            <div class="content">
                <div class="title">{{ todo.name }}</div>
                <div class="description">{{ todo.description }}</div>
            </div>
        </div>
        <div v-if="!todos.some(todo => todo.day == day && todo.isChecked == false)">
            <p>empty!</p>
        </div>
        <div @click="addTodo" title="create todo" class="plusButton">+</div>
    </div>
</template>

<style scoped>
h1 {
    color: #b153ff;
}

p {
    color: #3f7cff;
    font-size: 1.2rem;
}

#app {
    display: flex;
    align-items: center;
    justify-content: start;
    width: 100vw;
    height: 90vh;
    flex-wrap: wrap;
    flex-direction: column;
    color: white;
    gap: 10px;
}

#app .item {
    width: 100%;
    display: flex;
    gap: 10px;
    align-items: center;
    transition: all .3s;
    justify-content: center;
}

#app .item .content {
    transition: all .3s;
    width: 70%;
    border-radius: 10px;
    word-break: break-all;
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

.header {
    width: 100vw;
    padding: 0 10px;
    display: flex;
    align-items: center;
    justify-content: space-around;
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

.check.ed {
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

.hello {
    border-radius: 100px;
    padding: 2px 20px;
    font-size: 1rem;
    background-color: #b153ff;
}

.days {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 90vw;
    cursor: pointer;
    flex-wrap: wrap;
    gap: 20px;
    padding: 20px;
}

.day {
    border-radius: 5px;
    background-color: #3f7cff;
    width: 80px;
    height: 40px;
    display: flex;
    align-items: center;
    transition: all .3s ease-in-out;
    justify-content: center;
    font-size: .9rem;
    position: relative;
}

.day:hover {
    transform: scale(1.2);
}

.day.active {
    background-color: #b55bff;
}

.red-point {
    position: absolute;
    top: -10px;
    right: -10px;
    border-radius: 100%;
    background-color: #ff5252;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 20px;
    height: 20px;
}

.plusButton {
    width: 50px;
    height: 50px;
    background-color: #3f7cff;
    box-shadow: 4px 4px 6px #00000044;
    border-radius: 100%;
    position: absolute;
    bottom: 20px;
    left: 20px;
    font-size: 3rem;
    display: flex;
    align-items: center;
    justify-content: center;
    box-sizing: border-box;
    padding-top: 5px;
    cursor: pointer;
    user-select: none;
    transition: all .3s;
}

.plusButton:hover {
    transform: scale(.9);
}

.plusButton:active{
    box-shadow: none;
    transform: translateY(2px) translateX(2px) scale(.9);
}

@keyframes move {
    from {
        transform: translateX(-200px);
    }

    to {
        transform: translateX(105vw);
    }
}
</style>

<script>
export default {
    name: 'TodoList',
    data() {
        return {
            day: 'SA'
        }
    },
    props: {
        todos: {
            type: Array
        },
        firstName: {}
    }, methods: {
        changeStatus(ev, todoId) {
            setTimeout(() => {
                ev.target.parentNode.classList.add('checked')
                ev.target.classList.add('ed')
                ev.target.parentNode.style.transform = 'translateX(-5vw)';
                setTimeout(() => {
                    ev.target.parentNode.style.transform = 'translateX(100vw)';
                    setTimeout(() => {
                        ev.target.parentNode.style.display = 'none'
                        this.$emit('changeStatus', todoId)
                    }, 300)
                }, 300)
            }, 350)
        },
        changeDay(ev) {
            this.day = ev.target.innerText.slice(0, 2).toUpperCase()
            document.querySelector('.day.active').classList.remove('active')
            ev.target.classList.add('active')
        },
        addTodo() {
            this.$emit('addTodoModel')
        }
    }
}
</script>