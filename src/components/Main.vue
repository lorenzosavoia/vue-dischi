<template>
  <main>
      <div class="container">
          <div class="row cards">
              <div 
                class="col-2 m-2 card"
                v-for="(card,index) in cards"
                :key="index"
              >
                  <img :src="card.poster" alt="">
                  <h1 class="title">{{ card.title }}</h1>
                  <h5 class="artist">{{ card.author }}</h5>
                  <h5 class="age-song">{{ card.year}}</h5>
              </div>
              
          </div>
      </div>
  </main>
</template>

<script>
import axios from 'axios';
export default {
    name: 'Main',
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