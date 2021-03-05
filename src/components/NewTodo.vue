<template>
    <section>
        <form>
            <input v-model="task_title" type="text" placeholder="Nouvelle tâche...">
            <button v-on:click="nombre +=1;newTask()">
                <span>+</span>
            </button>
        </form>
    </section>
</template>

<script>
export default{
    name: "new-todo",

    data(){
        return{
            task_title: "",
            nombre: 0,
        }
    },

    methods:{
        newTask(){
            this.$emit("newTask", this.task_title)
            this.$emit('nombre', this.nombre)
        }
    }
}
</script>

<style scoped>

form{
    display: flex;
    width : 500px;
    margin: 20px auto;
}

input{
    text-align: center;
    border: none;
    border-bottom: 2px aqua solid;
    font-size: 14px;
    padding: 10px 20px;
    width : 500px;
    background-color: whitesmoke;
    margin: 0 20px;
}

input:focus, button:focus{
    outline: none;
}

button{
    background-color: lawngreen;
    border-radius: 45px;
    height: 45px;
    width: 55px;
    border: none;
}

button:hover{
    cursor: pointer;
}

span{
    font-size: 30px;
    font-weight: bold;
    color: white;
    padding-bottom: 50px;
    display: block;
}
</style>