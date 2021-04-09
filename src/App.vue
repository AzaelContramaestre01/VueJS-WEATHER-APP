<template>
  <div id="app">
    <main>
      <div class="search-box">
        <input type="text" name="" id="" class="search-bar" placeholder="Search. . .">
      </div>
    </main>
  </div>
</template>

<script>
export default {
  name: 'App',
  data () {
    return {
      api_key: "6a64252f5aa08424a201683d80a09439"
  }
}
}

</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "montserrat", sans-serif;
}

#app {
  background-image: url(./assets/ice.jpg);
  background-size: cover;
  background-position: bottom;
  transition: 0.4s;
}

main {
  min-height: 100vh;
  padding: 25px;

  background-image: linear-gradient(to bottom, rgba(0,0,0,0.25), rgba(0,0,0,0.75)) ;
}

.search-box{
  width: 100%;
  margin-bottom: 30px;
}

.search-box .search-bar {
 display: block;
  width: 100%;
  padding: 15px;

  appearance: none;
  background: none;
  border: none;
  outline: none;

  background-color: rgba(255,255,255,0.5);
  border-radius: 0px 0px 16px 16px;
  margin-top: -25px; 

  box-shadow: 0px 5px rgba(0,0,0,0.2);
  color: #313131;

  transition:0.4s ease;
}

.search-bar .search-box:focus{
  background-color: rgba(255,255,255,0.75);
  box-shadow: 0px 0px 16px rgba(0,0,0,0.25);
}
</style>
