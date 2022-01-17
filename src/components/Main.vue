<template>
  <main>
      <div class="container">
          <div class="row cards">
              <Card
                
                v-for="(card,index) in cards"
                :key="index"
                :image="card.poster"
                :title="card.title"
                :artist="card.author"
                :years="card.year"
              />
                  <!-- <img :src="card.poster" alt="">
                  <h1 class="title">{{ card.title }}</h1>
                  <h5 class="artist">{{ card.author }}</h5>
                  <h5 class="age-song">{{ card.year}}</h5> -->
            
              
          </div>
      </div>
  </main>
</template>

<script>
import axios from 'axios';
import Card from './Card.vue';
export default {
    name: 'Main',
    components: {
        Card,
    },
    data(){
        return{
            cards: [],
        }
    },
    mounted() {
        axios
        .get('https://flynn.boolean.careers/exercises/api/array/music')
        .then((result) => {
          console.log(result.data.response);
          this.cards = result.data.response;
        })
        .catch((error) => {
          console.log(error);
        });
    }
}

</script>

<style lang="scss">
    main{
        margin-top: 3em;
        .cards{
            width: 100%;
            height: 70%;

            .card{
                background-color: #2d3a46;
                color: white;
                padding: 1em;
                h1{
                    font-size: 1.5em;
                    margin-top: .5em;
                }
                h5{
                    color: #4b545d;
                    font-size: 1em;
                }
            }
        }
    }
</style>