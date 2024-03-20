<template>
    <div v-show="isShow" class="box">
        <header>
            <div class="left">
                Create <br /> New Todo
            </div>
            <div class="right">
                <img src="https://cdn-icons-png.flaticon.com/512/3176/3176366.png" alt="Todo list image">
            </div>
        </header>
        <div class="titleContainer">
            <p class='title'>Title</p>
        </div>
        <input ref="title" type="text">
        <div class="titleContainer">
            <p>Description</p>
        </div>
        <textarea class="descr" ref="descr" type="text"></textarea>
        <select name="day">
            <option value="6">Saturday</option>
            <option value="7">Sunday</option>
            <option value="1">Monday</option>
            <option value="2">Tuesday</option>
            <option value="3">Wednesday</option>
            <option value="4">Thursday</option>
            <option value="5">Friday</option>
        </select>
        <div class="line">
            --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
        </div>
        <div class="buttons">
            <button>Add</button>
            <button @click="hide" class="circle">></button>
        </div>
    </div>
</template>

<style scoped>
.box {
    padding-top: 30px;
    display: flex;
    align-items: center;
    justify-content: start;
    flex-direction: column;
    width: 100vw;
    height: 100vh;
    position: absolute;
    top: 0;
    right: 0;
    transition: all .7s ease-out;
    background-color: white;
    overflow: none;
}

header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 70%;
}

header .left {
    font-size: 2rem;
    font-weight: bolder;
    color: #c073ff;
}

header .right img {
    position: relative;
    width: 5.5rem;
}

header .right img::before {
    content: "";
    width: 80%;
    height: 80%;
    border-radius: 100%;
    background-color: #c799ee;
    position: absolute;
    top: 10%;
    left: 10%;
}

input,
textarea,
select {
    width: 70%;
    border: none;
    box-shadow: none;
    outline: none;
    border-radius: 5px;
    font-size: 1.5rem;
    background-color: #c5dcff;
    box-sizing: border-box;
    padding: 0 5px;
    font-weight: bold;
    margin-bottom: 30px;
    color: #2b80ff;
}

.titleContainer {
    width: 70%;
}

p {
    float: left;
    font-weight: bold;
}

p.title {
    color: #2b80ff;
}

p:not(.title) {
    color: #b076e0;
}

textarea.descr {
    font-size: 1rem;
    height: 100px;
    padding: 10px;
    resize: none;
    background-color: #dfc7ff;
    color: #b57fe0;
    font-weight: unset;
}

select,
option {
    font-size: 1rem;
    border-style: none;
    font-weight: unset;
}

option:hover {
    background-color: white;
}

.buttons {
    width: 90%;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 20px;
    position: absolute;
    bottom: 60px;
}

button {
    width: 72.7%;
    height: 40px;
    color: white;
    outline: none;
    border: none;
    background-color: #c073ff;
    border-radius: 100px;
    font-size: 1.3rem;
    font-weight: bold;
    cursor: pointer;
}

button.circle {
    width: 40px;
    height: 40px;
    font-size: 2rem;
    display: flex;
    align-items: center;
    justify-content: center;
    box-sizing: border-box;
    padding-top: 3px;
    font-weight: 100;
}

.line {
    width: 70%;
    overflow: hidden;
    height: 14px;
    color: #2b80ff;
    letter-spacing: 5px;
}

@keyframes open-select {
    from {
        transform: scaleY(0);
    }

    to {
        transform: scaleY(1);
    }
}
</style>

<script>
export default {
    name: 'AddBox',
    data() {
        return {
            isShow: false
        }
    },
    methods: {
        show(title = "", description = "") {
            title + description
            document.querySelector('.box').style.transform = 'translateX(105vw)'
            this.isShow = true
            setTimeout(() => {
                document.querySelector('.box').style = ''
                document.body.style.userSelect = 'none';
                document.body.style.overflow = 'hidden';
            }, 30)
        },
        hide() {
            setTimeout(() => {
                document.querySelector('.box').style.transform = 'translateX(105vw)'
                setTimeout(() => {
                    document.body.style = ''
                    this.isShow = false
                }, 750)
            }, 30)
        }
    }
}
</script>