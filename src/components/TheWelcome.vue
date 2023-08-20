

<template>

<div>
    <h1>hello</h1>
    <p>first project</p>
    <select v-model="selectedHotel">
      <option value="">Select a hotel</option>
      <option v-for="hotel in hotels" :key="hotel.id" :value="hotel.id">{{ hotel.email }}</option>
    </select>
    <div v-if="selectedHotel">
      <h2>Selected Hotel: {{ getSelectedHotel(selectedHotel).email }}</h2>
    </div>
  </div>
      {{ hotels}}
sssssssssss
      <CardsHotel/>
  
</template>


<script >

  import axios from 'axios';
  import CardsHotel from './CardsHotel.vue';
  import { ref } from 'vue'

      
      export default {
         components(){
          CardsHotel 
         },
        setup()
        {
          const hotels = ref('')
                  return {
                    hotels
                  }
        },
        mounted () {
        axios
          .get('http://127.0.0.1:8000/api/hotel/all')
          .then(response => {
              this.hotels = response.data 
          })
         
          .catch(error => {
              console.error('Error fetching data:', error);
            });
          
      }

    }
    
    
</script>



<style>

</style>