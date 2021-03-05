<template>
    <article>
        <div>
            <input type="checkbox">
            <p>{{ task_title }}</p>
        </div>
        <button>
            <i class="fas fa-trash"></i>
        </button>
    </article>
</template>

<script>
export default{
    name: "NewTask",
    props:['task_title'],
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
</style>