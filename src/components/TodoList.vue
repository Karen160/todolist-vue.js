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
 <button v-on:click='removeAll(index)'>
    Tous supprimer <i class="fas fa-trash"></i>
</button>

 <button v-on:click='removeTaskFinish(index)'>
    Tous supprimer tache fini <i class="fas fa-trash"></i>
</button>
</template>

<script>
    export default {
        name : "TodoList",
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

             removeTaskFinish(index){
                this.$emit('supprimeTaskFini', index)
            }
        }
    }
</script>

<style scoped>
 article{
        display: flex;
        justify-content: space-between;
    }

    p{
        font-size: 14px;
    }
    
    input{
        border-radius: 45px;
        height: 45px;
        width: 55px;
    }

    button{
        background-color: red;
        border-radius: 45px;
        height: 45px;
        width: 55px;
        border: none;
    }

    button:hover{
        cursor: pointer;
    }

    i{
        font-size: 30px;
        font-weight: bold;
        color: white;
        padding-bottom: 50px;
        display: block;
    }

    .fini{
        color: red;
    }

</style>