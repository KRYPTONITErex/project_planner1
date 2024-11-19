<template>

    <nav class="filter-nav">

      <button class="filter-button" @click="filterBy('all')" 
      :class="{active:current==='all'}">All</button>

      <button class="filter-button" @click="filterBy('complete')" 
      :class="{active:current==='complete'}">Complete</button>

      <button class="filter-button" @click="filterBy('ongoing')" 
      :class="{active:current==='ongoing'}">Ongoing</button>

    </nav>

</template>
  
<script>
  export default {
    props:['current'],
    methods:{
        filterBy(value){
            // console.log(value)
            this.$emit("filterValue",value);
        }
    }

  };
</script>
  
<style>
  .filter-nav {
    margin-top: 25px;
    display: flex;
    justify-content: center;
    gap: 30px;
    padding: 0px;
    background-color: #f3f2f2; /* Light gray background for the nav */
    border-radius: 3px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1); /* Subtle shadow for modern look */
  }
  
  .filter-button {
    padding: 8px 16px;
    font-size: 14px;
    font-weight: 500;
    color: #7f6868; /* Default text color */
    background-color: #fff;
    border: 1px solid #ddd;
    border-radius: 100px;
    padding: 10px 30px 10px 10px;
    cursor: pointer;
    transition: all 0.3s ease;
  }
  
  .filter-button:hover {
    background-color: orange; /* Hover effect: light blue */
    color: rgb(255, 255, 255);
  }
  
  button.active{
    font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
    letter-spacing: 1px;
    font-weight: bold;
    font-size: large;
    color: #f9e593;
    background-color: rgb(52, 133, 102);
    box-shadow: 10px 0px 0px 9px rgba(3, 252, 252, 0.315);

  }

</style>