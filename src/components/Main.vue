<template>
  <main>
      <div class="container">
          <div class="row d-flex justify-content-center">
              <div class="col-3">
                  <h3 class="gender-title">Seleziona genere:</h3>
              </div>
              <div class="col-2 d-flex align-items-center">
                <select 
                    class="gender-select"
                    name="gender" id="gender"
                    v-model="genderSelection"
                    @change="filterGender1"
                >

                    <option value="all">All</option>
                    <option value="rock">Rock</option>
                    <option value="pop">Pop</option>
                    <option value="jazz">Jazz</option>
                    <option value="metal">Metal</option>

                </select>

              </div>
          </div>
          <div class="row cards d-flex justify-content-center">
            <Card                
                v-for="(card,index) in filterGender"
                :key="index + 'A'"
                :image="card.poster"
                :title="card.title"
                :artist="card.author"
                years="card.year"
            />   
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
            filterGender: null,
            genderSelection: 'all',
        }
    },
    mounted() {
        axios
        .get('https://flynn.boolean.careers/exercises/api/array/music')
        .then((result) => {
          console.log(result.data.response);
          this.cards = result.data.response;
          this.filterGender = this.cards
        })
        .catch((error) => {
          console.log(error);
        });
    },
    methods:{
        filterGender1() {
            this.filterGender = this.cards;

            if(this.genderSelection !== 'all'){
                this.filterGender = this.filterGender.filter(album => album.genre.toLowerCase() === this.genderSelection);
            }else{
                return this.filterGender;
            }
            return this.filterGender;
        },
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
    .gender-select{
        width: 100%;
        height: 80%;
    }
    .gender-title{
        color: white;
    }
</style>