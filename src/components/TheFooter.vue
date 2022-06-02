<template>
    <div class="main-footer">
        <h2>Hope you have seen it🤪</h2>
    </div>
</template>


<script>
export default {
    props: ['footer']

}
</script>


<style scoped>
.main-footer{
    background: rgb(255, 255, 255);
    color: rgb(0, 0, 0);
    padding: 4rem;
    width: 100%;
    margin-top: 5rem;
    

    -webkit-box-shadow: 0px -8px 37px 0px rgba(0,0,0,0.75);
    -moz-box-shadow: 0px -8px 37px 0px rgba(0,0,0,0.75);
    box-shadow: 0px -8px 37px 0px rgba(0,0,0,0.75);
}

h2{
    font-size: 3rem;
}
</style>