<template>
    <div>
       <h1>API Data</h1>
       <div v-if="data">
         <p>{{ data }}</p>
       </div>
       <div v-else>
         <p>Loading...</p>
       </div>
    </div>
   </template>
   
   <script>
   export default {
    data() {
       return {
         data: null,
       };
    },
    async mounted() {
       try {
         const response = await fetch('https://jsonplaceholder.typicode.com/todos/1');
         if (!response.ok) {
           throw new Error('Network response was not ok');
         }
         this.data = await response.json();
       } catch (error) {
         console.error('There was a problem with your fetch operation:', error);
       }
    },
   };
   </script>