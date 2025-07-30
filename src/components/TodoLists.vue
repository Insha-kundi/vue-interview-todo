<script setup>

import { ref, reactive } from 'vue';


const showDeletePopup = ref(false);

const taskToDelete = ref('null');



// create task
const task = ref('');
// edit task 
const editedTask = ref(null);

//  status update  simple array
const availableStatus = ref(['Todo', 'Pending', 'Completed']);

// array object for task adding 
const todoList = ref([{

  name: 'This is a simple Task',
  status: 'Todo',
  date: new Date().toLocaleString(),
},

]);


// adding task to the table 

const submitTask = () => {

  //    console.log(task.value);

  if (task.value.trim() === '') {

    alert('Please Enter Your Task')

    return;
  }

  if (editedTask.value === null) {

    todoList.value.push({
      name: task.value,
      status: 'Todo',
      date: new Date().toLocaleString(), // adds current date and time

    });
  }
  else {

    todoList.value[editedTask.value].name = task.value;
    editedTask.value = null;
  }

  task.value = '';
}

// edit task function 

const EditTask = (index) => {

  task.value = todoList.value[index].name;

  editedTask.value = index;
}


const confirmDelete = (index) => {

  taskToDelete.value = index;
  showDeletePopup.value = true;


}
// Task deletions function 

const deleteTask = () => {

  if (taskToDelete.value !== null) {

    todoList.value.splice(taskToDelete.value, 1);

  }

  showDeletePopup.value = false;
  taskToDelete.value = null;
}

// cancel deletion 

const cancelDeletion = () => {

  showDeletePopup.value = false;
  taskToDelete.value = null;
};


const statusTextStyle = (status) => {

  const styles = {
    Completed: {

      color: '#28a745',
      fontWeight: '600',
      textDecoration: 'line-through',
    },

    Pending: {

      color: '#fd7e14',
      fontWeight: '600',
    },


    Todo: {

      color: 'black',
      fontWeight: '600',
    },

  };

  return styles[status] || styles.Todo;

}

// task status changing function 

// const changeStatus = (index) => {

//     let currentStatus = availableStatus.value.indexOf(todoList.value[index].status);
//     if(++currentStatus > 2) currentStatus =0;
//     todoList.value[index].status = availableStatus. value[currentStatus];

// }

</script>

<template>

  <!-- <h4>{{ message }}</h4> -->


  <div>




    <h1>My Todo List App</h1>

    <input v-model="task" type="text" @keyup.enter="submitTask()">
    <button @click="submitTask()" style="cursor: pointer;">
      {{ editedTask !== null ? 'Update Task' : 'Add Task' }}
    </button>


    <table>

      <thead>
        <tr>
          <th>Task</th>
          <th>Status</th>
          <th>Date</th>
          <th>Edit</th>
          <th>Delete </th>


        </tr>
      </thead>

      <!-- added task to the table using for loop -->

      <tr v-for="(task, index) in todoList" :key="index">
        <td style="width: 400px;" :style="statusTextStyle(task.status)"> <span style="width: 80px;">
            {{ task.name }}
          </span> </td>




        <!-- status dropdown  -->
        <td style="width:80px;"> <span style="cursor: pointer">
            <select v-model="task.status">

              <option v-for="status in availableStatus" :key="status" :value="status">
                {{ status }}
              </option>

            </select>
          </span> </td>

        <!-- Edit task by clicking edit button using editTask function  -->
        <td style="width: 200px;">{{ task.date }}</td>


        <td v-on:click="EditTask(index)"> <span style=" color: green; cursor: pointer;">Edit</span> </td>


        <!-- Task deletion function  -->

        <td v-on:click="confirmDelete(index)"><span style="cursor: pointer;color: red;">Delete </span> </td>



      </tr>



    </table>

    <!-- popup setting for deletons confirmation  -->

    <div v-if="showDeletePopup" class="popup-overlay">

      <div class="popup">
        <p> Sabr Sabr pehly Dekyn , Ap Delete Karna Chahty hyn a Task </p>
        <button @click="deleteTask()"> Yes </button>
        <button @click="cancelDeletion()"> No </button>
      </div>
    </div>
  </div>



</template>


<style scoped>
table {
  margin-top: 3rem;
  width: 50%;
  border-collapse: collapse;
}

th,
td {
  border: 1px solid #ddd;
  padding: 8px;
}

th {
  background-color: #f2f2f2;
  text-align: left;
}

input {
  width: 350px;
  padding: 10px;
  margin-right: 10px;
}

button {
  padding: 10px 20px;
  background-color: greenyellow;
  color: white;
  border: none;
  cursor: pointer;
}

button:hover {
  background-color: #45a049;
}

/* Popup Styles */
.popup-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
}

.popup {
  background: #fff;
  padding: 20px;
  border-radius: 8px;
  text-align: center;
}

.popup button {
  margin: 5px;
}
</style>
