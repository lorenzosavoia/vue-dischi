<template>
  <div
    class="col-2 m-2 card"
  >
    <img :src="image" alt="">
        <h1 class="title">{{ name }}</h1>
        <h5 class="artist">{{ artist }}</h5>
        <h5 class="age-song">{{ age-song}}</h5>
  </div>
</template>

<script>
export default {
    name: 'Card',    
    props: [
        'image',
        'artist',
        'age-song',
    ],
};
</script>

<style>

</style>