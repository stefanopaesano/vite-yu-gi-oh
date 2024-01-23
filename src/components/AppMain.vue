<script>
 import SingleCard from './SingleCardApp.vue';
 import { store } from '../store.js';


  export default {
    data() {
      return {
        store
      }
    },
    components: {
      SingleCard, 
    }
  }
</script>

<template>

  <div id="main">
    <div class="dropdown">
      <a class="btn dropdown-toggle ">
        Alien
      </a>
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

  </div>

  
</template>

<style lang="scss" scoped>
#main{
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