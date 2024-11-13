<template>

    <div>
        <div class="project" @click="showDetail=!showDetail">
            <h3>{{ project.title }}</h3>
        
            <h4 v-if="showDetail">{{ project.detail }}</h4>
        </div>
    </div>


  
</template>

<script>
export default {
    props:['project'],
    data(){
        return{
            showDetail: false
        }
    }

}
</script>

<style>

.project{
    padding: 20px;
    background-color: rgba(247, 247, 69, 0.712);
    cursor: pointer;
    margin: 20px;
    border-radius: 15px;
}

</style>