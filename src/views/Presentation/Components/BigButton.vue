<template>
        
    <div
      class="bg-image d-flex justify-content-center align-items-center rounded"
      :style="{ 
        backgroundColor: 'rgb(26, 115, 232)',
        height: '10vh',
        width: '35vh'
      }"
       data-bs-toggle="offcanvas" href="#offcanvasExample" role="button" aria-controls="offcanvasExample"
      @click="scrollToElement"
    >
      <h3 class="text-white">Ispuni moj dan</h3>
    </div>
  </template>
  
  <script>
  export default {
    name: "BigButton",
    props: {
      text: {
        type: String,
        default: "Show"
      }
    },
    methods: {
        scrollToElement() {
    }
    }
  };
  </script>
  
  <style scoped>
  .bg-image {
    /* Adding a border radius to make it rounded */
    border-radius: 15px; /* Adjust the value to control how rounded the corners are */
    cursor: pointer; /* Change the cursor to indicate the element is clickable */
  }
  
  h1 {
    /* Add a slight shadow for text readability */
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
  }
  </style>
  