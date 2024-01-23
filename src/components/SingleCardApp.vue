<script>
export default {
    data() {
      return {
      }
    },
    props: {
      card: Object
    }
}

</script>

<template>

  <div class="single-card">
    <div>
      <img :src="card.card_images[0].image_url" :alt="card.name">
    </div>


    <div class="unico">
        
          {{ card.name }}
        

       
          {{ card.type }}
        
    </div>
    
  </div>


  
</template>

<style lang="scss" scoped>
.nome{
  color: white;
  border:5px solid green;
  border-radius: 30%;
  
  
  

}
.type{
  color: white;
  border:5px solid black;
  border-radius: 30%;
  
  
}
.single-card{
     width: 25%;
     margin: 5px;
           
           
           
           
            
}

.unico{
  background-color: blue;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 30px;

}


</style>