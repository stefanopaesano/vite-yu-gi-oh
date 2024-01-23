<script>
 import SingleCard from './SingleCardApp.vue';
 import { store } from '../store.js';
 import axios from 'axios';


  export default {
    data() {
      return {
        searchStatus: '',
        searchText: '',
        store

      }
    },
    components: {
      SingleCard, 
    },
    methods:{
        HandleFormSubmit (){
            if (this.searchText.length > 0) {
               this.getDataForApi();
            }
            else{
                this.getDataForApi();
            }

          
        },
        getDataForApi(){

            let quesrystring = '';

            if (this.searchText.length > 0){
                quesrystring= '?name-' + this.searchText
            }

            const fullurl = this.store.baseUrl + quesrystring;
            console.log(fullurl)
            axios
                .get(fullurl)
                .then((response)=> {
                console.log('api response: ', response);
                this.store.cards = response.data.data;
                console.log(this.store.cards)
                })

        }

    }
  }
</script>

<template>

<main>

    

        <div class="dropdown">

            <form @submit.prevent="HandleFormSubmit ()">
                    
                <input v-model="searchText" type="text" placeholder="search card" aria-label="searchcard">

                <select v-model="searchText" ria-label="Status">
                        
                    <option Selected value="archetype">alien</option>
                    <option value="archetype">Infernoble Arms</option>
                    <option value="archetype">Noble Knight</option>
                    <option value="archetype">melodius</option>
                    <option value="archetype">Archfiend</option>
                

                </select>

                <button type="submit">
                      search
                </button>

            </form>
            
            

        </div>
        <div class="cards-album ">

            <div class="p-2">
                Found {{ store.cards.length }} cards
            </div>

            <div class="cards-container">
                <SingleCard :card="card" v-for="(card, index) in store.cards"
                    :key="index" />
                
            </div>
        </div>

</main>

  
</template>

<style lang="scss" scoped>
main{
    background-color: orangered;
}
.cards-album{
    .cards-container{
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        align-items: center;
        text-align: center;
        
    }
    
}

</style>