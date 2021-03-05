<template>
    <div id="card">
        <section id="date">
            <p>{{ date }}</p>
            <span>{{ title }}</span>
            <p v-if="somme < 2">{{ somme }} tâche</p>
            <p v-else>{{ somme }} tâches</p>
        </section>
        <new-todo @nombre=nb @newTask="addTask"></new-todo>
        <todo-list :task="task" @finCheck="check" @supprime="poubelle" @supprimeTous="poubelleAll"></todo-list>
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
                somme: 0,
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
                this.somme++; 
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
                this.somme--
            },

            poubelleAll(task) {
                this.task.splice(task)
                this.somme = 0;
            },
        }
    }
</script>

<style scoped lang="css">
    #card {
        background-color: whitesmoke;
        width: 80%;
        margin: auto;
        border-radius: 20px;
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