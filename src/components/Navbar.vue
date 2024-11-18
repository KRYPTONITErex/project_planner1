<template>
    <nav class="main-nav">
      <router-link to="/" class="nav-link">Project</router-link>
      <span class="separator">||</span>
      <router-link :to="{ name: 'AddProject' }" class="nav-link">Add Project</router-link>
    </nav>
  </template>
  
  <script>
  export default {
    name: "MainNav",
  };
  </script>
  
  <style scoped>
  .main-nav {
    width: 400px;
    display: inline-flex; /* Compact width around the content */
    justify-content: center;
    align-items: center;
    gap: 10px;
    background-color: #f8f9fa;
    padding: 0px 0px;
    border-radius: 20px; /* Rounded corners */
    font-family: Arial, sans-serif;
    border: 2px solid #ccc;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1); /* Optional shadow for depth */
  }
  
  .nav-link {
    text-decoration: none;
    color: #034891d8;
    font-size: 20px;
    font-weight: bold;
    padding: 10px;
  }
  
  .separator {
    color: #6c757d;
    font-size: 14px;
  }
  .router-link-active {
  color: #fcf2d6; /* Highlighted text color */
  font-weight: bold; /* Emphasize the active link */
  background-color: rgb(3, 125, 90);
  border-radius: 15px; /* Rounded corners for a smoother look */
  margin: 2px;
  height: 30px;
  padding: 5px 20px;
  }
  </style>