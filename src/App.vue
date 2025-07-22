<script setup>

import { computed, reactive, ref } from 'vue';
import TodoList from './components/TodoLists.vue';
import NewPractice from './components/NewPractice.vue';

// const message = ref('helloo world');

// const RawMessage = ref('This is a raw html saab');
// const IdBind = ref('Khan');
// const ClassBind = ref('classGiven')
// const StyleBind = ref({
//   color: 'red',
//   fontSize: '20px'
// });

// const AllBind = ref({
//   id: 'khan',l
//   class: 'classGiven',
//   style:{
//     backgrondColor: 'blue',
//     fontSize: '20px'
//   }
// })

// const VeIf = ref({
//   name : 'INsha',
//   age: '35'
// });

// const typeing = ref('A')



// const name = ref('This is a anme of anything will change on click');
//  const inputType = ref('value');
//  const value = ref('Dynamic input');

//  const count = ref(0);

//  const myObject = reactive({
//   title: 'How to do lists in Vue',
//   author: 'Jane Doe',
//   publishedAt: '2016-04-10'
// })

//  const decrement = () =>{

//   count.value -=1;

//  }

// //  const StudentName = ref(['insha', 'Ali', 'Awain', 'Tahir']);
//  const StudentName1 = ref([{ name: 'insha', agee: '23'}]);


//  const EvenNumber = ref([2, 4, 6, 8, 5,10]);

//  const FindEven = computed(() => {

//   return EvenNumber.value.filter((n) => n % 2 === 0);

// }
//  );





</script>

<template>

<!-- <NewPractice/> -->

<TodoList/>
<!-- <TodoList message = "this is all about Props" /> -->
<!-- 
  <newpractice />
 <li v-for="numbers in FindEven" >{{ numbers }}</li>

 <p v-for="n in 10">{{ n }}</p>
  <h2 v-for="(myObjects, key) in myObject" >{{ key }}: {{ myObjects }}</h2>

  <li v-for="StudentNames2 in StudentName1"> {{ StudentNames2.name}} {{StudentNames2.agee }} </li>

  <p v-if="VeIf.name == 'INsha' && VeIf.age == '5'">Thiis is Insha</p>
  <p v-else>This is not insha</p>
  <p></p>
   <p v-if="typeing == 'A'">This is A</p>

   <p v-if="typeing == 'B'">This is B</p>

   <p v-else >Not A and B</p>


  <button v-on:click="awsome == awsome">Toggle</button>

  <h2 v-if="awsome" >vue is Awsome</h2>
  <h2 v-else>oh vue is not </h2>

  <h1 v-bind="AllBind" >Heloo This is just Testing</h1> -->


<!-- <p>{{ message }}</p>

<h2 v-html="RawMessage"></h2>

<h2 v-bind:id="IdBind">This si sgive  id</h2>

<h2 v-bind:class="ClassBind">This si sgive  classs</h2>


<h2>{{ name }}</h2>

<button v-on:mouseenter="name= 'this is snew hcange after cliking'" >Click ME</button>

<input :[inputType]="value" />


<h3>{{ count }}</h3>

<button v-on:click="decrement">Decrement</button> -->




</template>



<style>


</style>