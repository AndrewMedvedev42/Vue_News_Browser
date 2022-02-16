<template>
  <MainSection/>
  <SideBar/>
</template>

<script>

import SideBar from './components/SideBar.vue'
import MainSection from './components/MainSection.vue'

export default {
  name: 'App',
  components: {
    MainSection,
    SideBar
  }
}
</script>

<style>
body{
  margin:0;
  padding: 1rem;
}
a{
  text-decoration: none;
}
#app {
  display: flex;
  flex-direction: row-reverse;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

  .image{
    width: 100%;
    max-height: 500px;
  }
  .slot{
    transition: .5s;
    cursor: pointer;
    margin-bottom: 1rem;
    overflow: hidden;
    border-radius: 15px;
    box-shadow: rgba(0, 0, 0, .25) 2.5px 2.5px 5px;
    /* border: tomato 5px solid; */
  }
  .slot:hover{
    opacity: .5;
  }
  .news_details{
    margin: 1rem;
  }
  .article_title{
    color: black;
    font-size: 1.5rem;
  }
  .article_big_title{
    font-size: 2rem;
  }
  .paragraph{
    color:rgba(0, 0, 0, 0.5);
  }
</style>
