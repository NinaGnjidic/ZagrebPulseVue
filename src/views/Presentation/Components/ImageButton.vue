<template>
    <div
      class="bg-image d-flex justify-content-center align-items-center rounded"
      :style="{ 
        backgroundImage: 'url(' + imageUrl + ')',
        backgroundSize: 'cover',
        backgroundPosition: 'center',
        height: '15vh',
        width: '27vh'
      }"
      @click="scrollToElement"
    >
      <h3 class="text-white">{{ text }}</h3>
    </div>
  </template>
  
  <script>
  export default {
    name: "ImageButton",
    props: {
      imageUrl: {
        type: String,
        required: true
      },
      targetId: {
      type: String,
      required: true // The ID of the element to scroll to
    },
      text: {
        type: String,
        default: "Show"
      }
    },
    methods: {
        scrollToElement() {
            const targetElement = document.getElementById(this.targetId);
  if (targetElement) {
    const elementPosition = targetElement.getBoundingClientRect().top + window.scrollY; // Calculate element's position relative to the top of the document
    const offsetPosition = elementPosition - 60; // Subtract the navbar height (50px) from the position

    window.scrollTo({
      top: offsetPosition,
      behavior: "smooth" // Smooth scrolling
    });
  } else {
    console.warn(`Element with ID "${this.targetId}" not found.`);
  }
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
  