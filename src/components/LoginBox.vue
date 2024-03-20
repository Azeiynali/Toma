<template>
    <div class="box">
        <h2>Enter Your First Name</h2>
        <input ref="name" type="text">
        <button @click="changeName">Get Started</button>
    </div>
</template>

<style scoped>
h2 {
    font-weight: bolder;
    font-size: 2rem;
    color: #2b80ff;
}

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

input {
    width: 70%;
    border: none;
    box-shadow: none;
    outline: none;
    border-radius: 5px;
    font-size: 1.5rem;
    background-color: #c5dcff;
    box-sizing: border-box;
    padding: 0 5px;
    margin-bottom: 30px;
    color: #2b80ff;
}

button {
    width: 70%;
    height: 40px;
    color: white;
    outline: none;
    border: none;
    background-color: #c073ff;
    border-radius: 100px;
    font-size: 1.3rem;
    font-weight: bold;
    cursor: pointer;
    position: absolute;
    bottom: 60px;
}
</style>

<script>
export default {
    name: "LoginBox",
    methods: {
        changeName() {
            if (this.$refs.name.value) {
                this.$emit('changeName', this.$refs.name.value)
                document.querySelector('.box').style.transform = 'translateX(105vw)'
                setTimeout(() => {
                    this.$emit('deleteLogin')
                }, 750)
            }
        }
    }
}
</script>