<template>
  <article>
    <h2>{{ anime.title }}</h2> 
    <p>{{ anime.description }}</p>
  </article>
</template>

<script>
export default {
  props:['anime'],

}
</script>

<style>

  article{
    background: whitesmoke;
    border-radius: 1rem;
    padding: 10px;
    box-shadow: 0px 3px 5px rgba(0,0,0,0.2);
    margin-bottom: 2rem;
    color: black;
    

  }

  article h2{
    margin-bottom: 1rem;
    text-align: center;
  }
</style>