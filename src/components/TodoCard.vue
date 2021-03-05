<template>
    <div id="card">
        <section id="date">
            <p>{{ date }}</p>
            <span>{{ title }}</span>
            <p v-if="task.length < 2">{{ task.length }} tâche</p>
            <p v-else>{{ task.length }} tâches</p>
        </section>
        <NewTodo @nombre=nb @newTask="addTask"></NewTodo>
        <TodoList :task="task" @finCheck="check" @supprime="poubelle" @supprimeTous="poubelleAll" @supprimeChecked="poubelleChecked"></TodoList>
    </div>
</template>

<script>
    import NewTodo from './NewTodo';
    import TodoList from './TodoList';
    export default {
        name: "todo-card",
        el: '#date',
        data() {
            return {
                title: "VueJs Tutorial ToDo List",
                task: [],
            }
        },
        computed: {
            date: function () {
                var date = new Date();
                var year = date.getFullYear();
                var months = ["Janvier", "Février", "Mars", "Avril", "Mai", "Juin", "Juillet", "Août", "Septembre",
                    "Octobre", "Novembre", "Décembre"
                ];
                var month = months[date.getMonth()];
                var days = ["Dimanche", "Lundi", "Mardi", "Mercredi", "Jeudi", "Vendredi", "Samedi"];
                var day = days[date.getDay()];
                var jour = date.getDate();
                date = day + " " + jour + " " + month + " " + year;
                return date;
            }
        },
        components: {
            NewTodo,
            TodoList
        },

        methods: {
            addTask(task) {
                if(task != ""){
                    this.task.push({
                    description: task,
                    checked: false
                })
                }
               
            },

            check(taskFini) {
                if (this.task[taskFini].checked === false) {
                    this.task[taskFini].checked = true
                } else {
                    this.task[taskFini].checked = false

                }
            },

            poubelle(task) {
                this.task.splice(task, 1)
            },

            poubelleAll(task) {
                this.task.splice(task)
                
            },

            poubelleChecked() {
                this.task = this.task.filter(task => !task.checked)
                // for(var i = 0; i<this.task.length; i++){
                //     if(this.task[i].checked){
                //         this.task.splice(i, 1)
                //     }
                // }
            }
        }
    }
</script>

<style scoped lang="css">
    #card { 
        background-color: whitesmoke;
        width: 80%;
        margin: auto;
        border-radius: 20px;
        padding: 0 0 10px 5px;
    }

    section:first-child {
        display: flex;
        justify-content: space-between;
        flex-wrap: wrap;
        font-size: 14px;
        font-weight: 500;
        padding: 20px;
        box-shadow: 0px 10px 10px -5px rgba(0, 0, 0, 0.10);
    }

    span {
        color: aqua;
    }
</style>