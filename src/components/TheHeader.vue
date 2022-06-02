<template>
  <div class="header">
    <img src="https://thumbs.gfycat.com/ConventionalAggressiveDeviltasmanian-size_restricted.gif" alt="">
    <a href="https://rickandmortyapi.com/" target="_blank"><h1> Rick and Morty </h1></a>
  </div>
</template>

<script>
export default {
  name: 'TheHeader',
  props: {
    msg: String
  }
}
</script>
<style scoped>
 .header{ 
  background: rgba(24, 22, 22);
  display: flex;
  position: fixed;
  top: 0;
  width: 100%;
  padding: 30px 0;
  z-index: 10;
  align-items: center;
  

  -webkit-box-shadow: -3px 15px 37px -7px rgba(0,0,0,0.75);
  -moz-box-shadow: -3px 15px 37px -7px rgba(0,0,0,0.75);
  box-shadow: -3px 15px 37px -7px rgba(0,0,0,0.75);

 }

h1 {
  font-size: 5rem;
}

h1:hover{
  transform: rotate(2deg) scale(1.3);
  transition-duration: .2s;
}

a{
  text-decoration: none;
  color: white;
}

img{
  border-radius: 50%;
  width: 10rem;
  height: 10rem;
  margin-right: 21rem;
}



</style>
