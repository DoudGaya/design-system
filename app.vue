<script>
import { defineNuxtComponent } from '#app';

export default defineNuxtComponent({
  data: () => ({
    photos: []
  }),



  computed: {
    photoGalleryLenght () {
      return this.photos.length
    },

    oddNumbersOfPhotos() {
      return this.photos.filter(item => item % 2 == 0)
    }
  },


  methods: {
    fetchData () {
      fetch('https://jsonplaceholder.typicode.com/photos')
      .then(res => res.json())
      .then( jsonData => this.photos = jsonData )
      console.log(this.photos)
    }
  }
})
</script>
<template>
  <div class=" flex flex-col">
    <div class=" flex w-full justify-center py-10">
      <button @click="fetchData" class=" text-white bg-black py-3 px-6 rounded-md">Fetch Data</button>
    </div>
    <div class=" max-w-6xl mx-auto grid grid-cols-10 gap-4">
     <div v-for=" pic in photos" class="">
      <img :src="pic.thumbnailUrl" class=" h-10 w-10" >
     </div>
    </div>
  </div>

</template>