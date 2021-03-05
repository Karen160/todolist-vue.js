<template>
<article v-for="(task, index) in task" :key="(task, index)">
    <div>
        <input type="checkbox" v-on:click='check(index)'>
        <p v-bind:class="{'fini':task.checked}">{{ task.description }}</p>
    </div>
    <button v-on:click='remover(index)'>
        <i class="fas fa-trash"></i>
    </button>
</article>
<br>
 <button v-on:click='removeAll(index)'>
    Tous supprimer 
</button>
 <button v-on:click='removeAllChecked()'>
    Tous supprimer checked
</button>
</template>

<script>
    export default {
        name : "todo-list",
        props: ['task'],
        methods: {
            check(index){
                this.$emit('finCheck', index)
            },

            remover(index){
                this.$emit('supprime', index)
            },
            
            removeAll(index){
                this.$emit('supprimeTous', index)
            },

            removeAllChecked(){
                this.$emit('supprimeChecked')
            }
        }
    }
</script>

<style scoped>
 article{
        display: flex;
        justify-content: space-between;
        padding: 10px 100px;
    }

    article div{
        display: flex;
         align-items: center;
         font-size: 14px;
    }

    p{
        font-size: 14px;
    }
    
    input{
       appearance: none;
        width: 30px;
        height: 30px;
        border-radius: 50%;
        border: 1px solid grey;
        outline: 0;
        margin-right: 20px;
    }

    input::before{
        background-color: grey;
        content: ' ';
        width: 24px;
        height: 24px;
        display: none;
        border-radius: 50%;
        margin: 2px 0 0 2px;
    }

    input:checked::before{
        display: block;
    }

    button{
        background-color: red;
        border-radius: 45px;
        color: white;
        font-size: 14px;
        border: none;
        padding: 10px 20px;
    }

    article button{
        background-color: red;
        border-radius: 45px;
        height: 40px;
        width: 40px;
        border: none;
        justify-content: center;
        display: flex;
    }

    button:hover{
        cursor: pointer;
    }

    i{
        font-size: 20px;
        font-weight: bold;
        color: white;
        padding-bottom: 50px;
        display: block;
    }

    .fini{
        text-decoration: line-through;
    }

    input:focus, button:focus{
        outline: none;
    }

</style>