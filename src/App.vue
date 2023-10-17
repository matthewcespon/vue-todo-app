<template >
  <div class="container ">
    <Header @toggle-add-task="toggleAddTask" title="<&#47to-do>"/>
    <div v-show="showAddTask">
      <AddTask @add-task="addTask"/></div>
    <Tasks @toggle-completed="togglecompleted" @delete-task="deleteTask"
    :tasks="tasks"/>
  </div>
</template>
<script>

// import TheWelcome from './components/TheWelcome.vue'
import Header from './components/Header.vue';
import Tasks from './components/Tasks.vue';
import AddTask from './components/AddTask.vue';

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks: [],
      showAddTask: false,
    }
  },
  methods: {
    toggleAddTask(){
      this.showAddTask =!this.showAddTask;
    },
    addTask(task) {
      this.tasks = [...this.tasks, task]
    },
    deleteTask(id) {
      // this.tasks = this.tasks.filter(task => task.id!== id)
      this.tasks = this.tasks.filter((task) => task.id !== id)
    },
    togglecompleted(id){
      this.tasks = this.tasks.map((task) => task.id === id? {...task, completed:!task.completed} : task
      );
    }
  },
  created() {
    this.tasks = 
    [
      {id: 1, text: 'Follow up on email', taskx: 'Email Dave about the project...', completed: false,},
      {id: 2, text: 'Grocery Shopping', taskx: 'Dont FORGET...', completed: false,},
      {id: 3, text: 'Code java project', taskx: 'Requirements for the project...', completed: false,}
    ]

  }
}
</script>



<style>
@import url('https://fonts.googleapis.com/css2?family=Sora&display=swap');
* {
  box-sizing: border-box;
  font-family: 'Sora', sans-serif;
  margin: 0;
  padding: 0;
}

.container {
  max-width: 90vw;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  padding:30px;
  border-radius: 5px;
}

</style>