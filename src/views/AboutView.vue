<template>
  <div class="todolist">
    <br>
    <div class="todo-box">
      <input
        type="text"
        v-model="task"
        placeholder="Zadejte úkol..."
        class="todo-bar">
      <button class="btn btn-warning rounded-0" @click="submitTask">
        <img src="../assets/add.svg">
      </button>
    </div>

    <table>
      <thead>
        <tr>
          <th scope="col" class="thead-ukol">Úkol</th>
          <th scope="col" class="thead-deledit">Splněno</th>
          <th scope="col" class="thead-deledit">Smazat</th>
          <th scope="col" class="thead-deledit">Upravit</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(task, index) in tasks" :key="index">
          <td>
            <span :class="{ 'line-through': task.status === 'finished' }">
              {{ task.name }}
            </span>
          </td>
          <td>
            <input class="checkbox" type="checkbox">
          </td>
          <td class="text-center">
            <div @click="deleteTask(index)">
              <img src="../assets/delete.svg">
            </div>
          </td>
          <td class="text-center">
            <div @click="editTask(index)">
              <img src="../assets/edit.svg">
            </div>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    return {
      task: "",
      editedTask: null,
      statuses: ["to-do", "in-progress", "finished"],
      
      tasks: [
        {
          name: "Dokončit projekt na WTL.",
          status: "to-do",
        },
        {
          name: "lorem ipsum lorem ipsum lorem ipsum",
          status: "to-do",
        },
        {
          name: "lorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsum",
          status: "to-do",
        },
      ],
    };
  },
  methods: {
    /**
     * Capitalize first character
     */
    capitalizeFirstChar(str) {
      return str.charAt(0).toUpperCase() + str.slice(1);
    },
    /**
     * Change status of task by index
     */
    changeStatus(index) {
      let newIndex = this.statuses.indexOf(this.tasks[index].status);
      if (++newIndex > 2) newIndex = 0;
      this.tasks[index].status = this.statuses[newIndex];
    },
    /**
     * Deletes task by index
     */
    deleteTask(index) {
      this.tasks.splice(index, 1);
    },
    /**
     * Edit task
     */
    editTask(index) {
      this.task = this.tasks[index].name;
      this.editedTask = index;
    },
    /**
     * Add / Update task
     */
    submitTask() {
      if (this.task.length === 0) return;
      /* We need to update the task */
      if (this.editedTask != null) {
        this.tasks[this.editedTask].name = this.task;
        this.editedTask = null;
      } else {
        /* We need to add new task */
        this.tasks.push({
          name: this.task,
          status: "todo",
        });
      }
      this.task = "";
    },
  },
};
</script>

<style scoped>

.todolist {
  background-color: #fff;
  min-height: 90vh;
  padding: 25px;
}

thead {
  padding: 15px;
  width: 200%;
  color: #313131;
  font-size: 20px;
  appearance: none;
  border:none;
  outline: none;
  background: none;
  box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.5);
  border-radius: 16px 16px 0px 0px;
  transition: 0.4s;
}

.thead-ukol {
  padding: 10px;
  width: 70%;
}

.thead-deledit {
  padding: 10px;
  width: 5%;
}

.checkbox {
  width: 5vh;
  height: 5vh;
}

table {
  width: 100%;
  margin: auto;
}
.todo-box {
  display: flex;
  margin-bottom: 30px;
}

.todo-box {
  justify-content: center;
}

.todo-bar {
  width: 50%;
}
.todo-box .todo-bar, button{
  padding: 15px;
  
  color: #313131;
  font-size: 20px;
  appearance: none;
  border:none;
  outline: none;
  background: none;
  box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.5);
  border-radius: 16px 0px 0px 16px;
  transition: 0.4s;
}

button {
  border-radius: 0px 16px 16px 0px;
  padding: 0;
}

td {
  padding: 10px;
  color: #313131;
  font-size: 20px;
  appearance: none;
  border:none;
  outline: none;
  background: none;
  box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.25);
  background-color: rgba(255, 255, 255, 0.5);
  transition: 0.4s;
}
</style>