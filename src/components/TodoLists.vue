<script setup>

import { ref, reactive } from 'vue';


// props

// defineProps([message]);

const task = ref('');
 const editedTask = ref(null);

 const availableStatus = ref(['Todo', 'Completed', 'Pending']);
 

const todoList = ref([{

    name: 'This is a simple Task',
    status: 'Todo',
},
    
]);

const submitTask = ()=>{

//    console.log(task.value);

   if(task.value.length===0) return;
   if(editedTask.value  === null){

    todoList.value.push({
        name:task.value,
        status: 'Todo'
    });
}
else{

    todoList.value[editedTask.value].name = task.value;
    editedTask.value = null;
}

   task.value= '';
}



const deleteTask = (index) =>{

    todoList.value.splice(index, 1);
}

const EditTask = (index)=>{

    task.value = todoList.value[index].name;
    editedTask.value = index;
}

const changeStatus = (index) =>{

    let currentStatus = availableStatus.value.indexOf(todoList.value[index].status);
    if(++currentStatus > 2) currentStatus =0;
    todoList.value[index].status = availableStatus. value[currentStatus];

}

</script>

<template>

    <!-- <h4>{{ message }}</h4> -->
    
    <div>
        <h1>My Todo List App</h1>

        <input v-model="task" type="text">
        <button v-on:click="submitTask" style="cursor: pointer;" >Add Your Task</button>

        <table>

            <thead>
                <tr>
                    <th>Task</th>
                    <th>Status</th>
                    <th>Edit</th>
                    <th>Delete</th>


                </tr>
            </thead>
           
            <tr v-for="(task, index) in todoList" :key="index" >
                <td style="width: 400px;"> <span style="width: 80px;">
                    {{ task.name }}
                </span> </td>
                <td style="width:80px;" v-on:click="changeStatus(index)">  <span style="cursor: pointer">
                    {{ task.status }} 
                </span> </td> 

                

                    <td v-on:click="EditTask(index)"> <span style=" color: green; cursor: pointer;">Edit</span>  </td>
               
                    
                    <td v-on:click="deleteTask(index)" ><span style="cursor: pointer;color: red;">Delete </span>  </td>
             

            </tr>
               


        </table>

    </div>



</template>


<style scoped>

table {
    margin-top: 3rem;
    width: 50%;
    border-collapse: collapse;
}
th, td {
    border: 1px solid #ddd;
    padding: 8px;
}
th {
    background-color: #f2f2f2;
    text-align: left;
}
td {
    text-align: left;
}

input {
    width: 350px;
    padding: 10px;
    margin-right: 10px;
}
button {
    padding: 10px 20px;
    background-color: #4CAF50;
    color: white;
    border: none;
    cursor: pointer;
}

</style>