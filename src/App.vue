<template>
  <div id="app">
  <div class="navbar">navbar</div>

            <div class="content">
                <sidebar :TotalTasks="TotalTasks" :CompletedTasks="CompletedTasks" />

                <!-- Principal -->
                <div class="main">
                    <div class="main-title">
                        <input type="input" id="title" placeholder="Title" v-model="MainTitle" />
                    </div>

                    <div class="main-tasks">
                        <ul class="tasks">
                            <li class="task blue">
                                <!-- Adicionar tarefa -->
                                <div class="main-add-tasks-title">
                                    <input @keyup.enter="Add()" type="text" placeholder="Title" v-model="NewTask" />
                                </div>
                                <div class="main-add-tasks-description">
                                    <input @keyup.enter="Add()" type="text" placeholder="Description" v-model="NewDescription" />
                                </div>
                                <button @click="Add()" class="button">Add task</button>
                            </li>
                            <!-- Tarefas adicionadas -->
                            <li v-for="(task, index) in tasks" :key="index" :class="{'green': task.completed}" class="task red">
                                <input type="checkbox" v-model="task.completed" />

                                <div class="title">{{task.title}}</div>
                                <div class="description">{{ task.description}}</div>
                            </li>
                        </ul>
                    </div>
                </div>
            </div>
  </div>
</template>

<script>

import sidebar from '@/components/sidebar'
export default {
  name: 'App',
  components: {sidebar},
   data() {
        return {
            MainTitle: "My tasks",
            tasks: [
                {
                    title: "Task 1",
                    description: "Description",
                    completed: false
                },
            ],
            NewTask: '',
            NewDescription:'',

            
        }
    },
    methods: {
        Add() {
            this.tasks.push({
                title: this.NewTask,
                description: this.NewDescription,
                completed: false
            })
            this.NewTask = '',
            this.NewDescription = ''

        },

    },
    computed: {
        TotalTasks() {
            return this.tasks.length
        },
        CompletedTasks() {
            return this.tasks.filter(tasks => tasks.completed).length
        },
        
        
            
        
    }

}

</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@400;500&display=swap");

body {
    margin: 0;
    padding: 0;
    font-family: Roboto;
    font-size: 20px;
}

.navbar {
    height: 10vh;
    width: 100%;
    border-bottom: solid 1px hsl(0, 0%, 70%);
}
.content {
    min-height: 90vh;
    display: flex;
    flex-direction: row;
    background-color: #f1f0ea;
}

/* Conteudo  */

.main {
    display: flex;
    flex-direction: column;
    background-color: #ffffff;
    border: solid 1px hsl(0, 0%, 70%);
    border-radius: 15px;
    padding: 1rem;
    margin: 5px;
    width: 100%;
}
.main-title {
    margin: 0 auto 0 auto;
    padding: 1rem;
}
.main-add-task {
    display: flex;
    flex-direction: column;
    align-items: center;
}
.tasks {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-auto-rows: 200px;
    grid-gap: 1rem;
}
.task {
    border: solid 1px;
    padding: 1rem;
    border-radius: 15px;
    padding: 25px;
}
.title {
    color: black;
    font-weight: bolder;
    margin: 20px auto auto auto;
}
.button {
    margin: 50px;
}

.description {
    font-weight: lighter;
    font-size: small;
    color: rgba(0, 0, 0, 0.5);
}
.blue {
    background-color: hsl(202, 66%, 39%, 50%);
    color: #2274a5;
}
.red {
    background-color: hsl(4, 79%, 63%, 50%);
    color: #eb5e55;
}

.green {
    background-color: hsl(131, 11%, 49%, 50%);
    color: #708b75;
}

li {
    list-style-type: none;
}
ul {
    padding-inline-start: 0;
}

.tasks input {
    outline: 0;
    border: 0;
    border-bottom: solid 1px;
    background: transparent;
    font-weight: bold;
}

/* Barra lateral  */

.sidebar {
    display: flex;
    flex-direction: column;
    height: 90vh;
    width: 20rem;
    background-color: #ffffff;
    border: solid 1px hsl(0, 0%, 70%);
    border-radius: 15px;
    margin: 5px;
    padding: 1rem;
}

</style>
