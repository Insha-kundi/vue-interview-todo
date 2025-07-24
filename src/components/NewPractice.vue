<script setup >
import { ref } from 'vue';

const name1 = ref('This is the new begining');
const myClass = ref('my-class');
const name = ref('new-item');
const stylingsab = ref('font-size:2rem;')



const name2 = ref('Insha');

const texting = ref('');

const status1 = ref('user1, admiqn, dashbqoard');

const status3 = ref(['user1, admiqn, dashbqoard, user, admin, dashboard']);



const age = ref(1)

const name3 = ref('InshaKundi');

</script>

<template>
  <p :class="myClass">Hello!</p>

<p v-bind:id="name" :style="'color:red;'">this is new itema</p>

<p :style="stylingsab">this is styling binding saaab</p>

<h3> {{ name1 }}</h3>

<h2 v-html="name1= 'Insha Kundi'"></h2>


<button @click="cute =! cute">Toggle Button</button>

<h2 v-if="cute">This is cute</h2>
<h2 v-else>this is not cute</h2>

<p v-if="age ===23">this is good for job</p>
<p v-else>this is not good for job</p>

<p v-if="name3 == 'Inshandi'">Yes this is Insha</p>
<p v-else>No, this is not</p>


<p v-if="status1 === 'user'">this is the user interface</p>
<p v-else-if="status1 === 'admin'">this is the admin interface</p>
<p v-else-if="status1 === 'dashboard'">this is the dashboard interface</p>

<p v-else>not anyone of them</p>


<p v-for="(status, index) in status3" :key="index"> {{ status }}</p>

<form action="">

    <input v-model="texting" id="">

    <input v-model="text" name="" id="">

    <p>This is message : {{ texting }}</p>

    <input v-model="messages" placeholder="message Eding" name="" id="">

</form>


</template>


<style scoped>



</style>