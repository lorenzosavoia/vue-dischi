<template>
  <div
    class="col-2 m-2 card"
  >
    <img :src="image" alt="">
        <h1 class="title">{{ title }}</h1>
        <h5 class="artist">{{ artist }}</h5>
        <h5 class="age-song">{{ years }}</h5>
  </div>
</template>

<script>
export default {
    name: 'Card',    
    props: [
        'image',
        'title',
        'artist',
        'years',
    ],
};
</script>

<style>

</style>