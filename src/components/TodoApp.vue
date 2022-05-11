<template>
  <div class="container">
    <h1 class="text-center" mt-5>My Todo List</h1>

    <!-- Input -->
    <div class="d-flex">
      <input v-model="task" type="text" class="form-control">
      <button @click="submitTask" class="btn btn-warning rounded-0">Submit</button>
    </div>
    <br>

    <!-- Task Table -->
    <table class="table table-hover table-dark">
      <thead>
        <tr>
          <th scope="col">Tasks</th>
          <th scope="col" class="">Status</th>
          <th scope="col" class="text-center">#</th>
          <th scope="col" class="text-center">#</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(task, index) in tasks" :key="index">
          <td :class="{'finished': task.status === 'finished'}">{{ task.name }}</td>
          <td style="width: 120px">
            <span :class="{'text-danger': task.status === 'todo',
            'text-warning': task.status === 'in-progress',
            'text-success': task.status === 'finished'}"
              @click="changeStatus(index)" class="pointer">
              {{ firstCharUpper(task.status) }}
            </span>
          </td>
          <td>
            <div class="text-center" @click="editTask(index)">
              <span class="fa fa-pen"></span>
            </div>
          </td>
          <td>
            <div class="text-center" @click="deleteTask(index)">
              <span class="fa fa-trash"></span>
            </div>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'TodoApp',
  props: {
    // msg: String
  },
  data(){
    return {
      task: '',
      editedTask: null,
      availableStatuses: ['to-do', 'in-progress', 'finished'],

      tasks: [
        {
          name: 'Buy playstation 4, this evening',
          status: 'todo'
        },
        {
          name: 'Write some vue code',
          status: 'finished'
        },
        {
          name: 'Buy a new phone',
          status: 'in-progress'
        }

      ]
    }
  },

  methods: {
    submitTask(){
      if(this.task.length === 0) return;

      if(this.editedTask === null){
        this.tasks.push({
        name: this.task,
        status: 'to-do'
      });
      }
      else{
        this.tasks[this.editedTask].name = this.task;
        this.editedTask = null;
      }

      this.task = '';
    },

    deleteTask(index){
      this.tasks.splice(index, 1);
    },

    editTask(index){
      this.task = this.tasks[index].name;
      this.editedTask = index;
    },

    changeStatus(index){
      let newIndex = this.availableStatuses.indexOf(this.tasks[index].status)
      if(++newIndex > 2) newIndex = 0;
      this.tasks[index].status = this.availableStatuses[newIndex];
    },

    firstCharUpper(str){
      return str.charAt(0).toUpperCase() + str.slice(1);
    }
  }


};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.pointer{
  cursor: pointer;
}
.finished{
  text-decoration: line-through;
}
</style>
