<template>




  <div class="flex justify-center" v-if="data == null">
    <img src="../assets/loader.gif" alt="">
  </div>


  <div class="category p-4 my-2 lg:px-16" v-if="data !== null">

    <div class="flex space-x-16 mb-4 items-center">
      <h1 class="text-2xl font-bold">Новые</h1>
      <img src="../assets/arrow-right.svg" alt="" width="40">
    </div>

    <img v-if="data.newBooks.length == 0" src="../assets/nothing.png" alt="nothing found" width="300">

    <div class="flex items-stretch space-x-4 overflow-x-auto slider" style="scroll-snap-type: x mandatory;">

      <div class="card border-2 p-4 rounded-lg hover:shadow-xl flex flex-col justify-between" v-for="(book,index) in data.newBooks"
      :key="index" style="max-width: 170px;">
        <div>
          <div class="book_images" style="min-height: 230px;">
            <img :src="book.cover" alt="" height="280" width="150">
          </div>

          <h3 class="text-start text-md mt-4 mb-2 text-grey-500 line-through" v-if="book.sales_per > 0">{{ book.prev_price }} c.</h3>
          
          <div class="flex items-center justify-between mt-4">
            <h2 class="text-start text-2xl mb-2 text-red-500">{{ book.cur_price }} c.</h2>
            <div class="px-2 bg-red-700 rounded-full" v-if="book.sales_per > 0">
              <h4 class="text-lg text-white font-semibold">{{ book.sales_per }} %</h4>
            </div>
          </div>

          <h1 class="text-start text-sm font-semibold break-words" style="max-width: 120px;">{{ book.name }}</h1>
          <h2 class="text-start text-sm font-light mb-4" style="max-width: 120px;">{{ book.author }}</h2>

          
        </div>

        <div>
          <div class="flex items-center mb-4" style="margin-top: auto">
              <img src="../assets/star_active.png" alt="" width="25" v-for="star in book.stars"> 
          </div>
          <div class="flex items-stretch justify-between space-x-2">
            <button style="background: #26a9e0;flex: 1;" class="px-4 rounded-lg font-bold text-lg text-white" @click="navigate('/book/' + book.id)">Подробнее</button>
            <img src="../assets/bookmark-2.svg" alt="" width="45" class="p-2 rounded-xl" 
            style="background: #ecf6fe;">
          </div>
        </div>
      </div>
    </div>

  </div>


	  <div class="category p-4 my-2 lg:px-16" v-if="data !== null">

    <div class="flex space-x-16 mb-4 items-center">
      <h1 class="text-2xl font-bold">Акции</h1>
      <img src="../assets/arrow-right.svg" alt="" width="40">
    </div>

    <img v-if="data.sales.length == 0" src="../assets/nothing.png" alt="nothing found" width="300">
    
    <div class="flex items-stretch space-x-4 overflow-x-auto slider" style="scroll-snap-type: x mandatory;">

      <div class="card border-2 p-4 rounded-lg hover:shadow-xl flex flex-col justify-between" v-for="(book,index) in data.sales"
      :key="index" style="max-width: 170px;">
        <div>
          <div class="book_images" style="min-height: 230px;">
            <img :src="book.cover" alt="" height="280" width="150">
          </div>
          <h3 class="text-start text-md mt-4 mb-2 text-grey-500 line-through">{{ book.prev_price }} c.</h3>

          <div class="flex items-center justify-between">
            <h2 class="text-start text-2xl mb-2 text-red-500">{{ book.cur_price }} c.</h2>
            <div class="px-2 bg-red-700 rounded-full">
              <h4 class="text-lg text-white font-semibold">{{ book.sales_per }} %</h4>
            </div>
          </div>

          <h1 class="text-start text-sm font-semibold break-words" style="max-width: 120px;">{{ book.name }}</h1>
          <h2 class="text-start text-sm font-light mb-4" style="max-width: 120px;">{{ book.author }}</h2>

          
        </div>

        <div>
          <div class="flex items-center mb-4" style="margin-top: auto">
              <img src="../assets/star_active.png" alt="" width="25" v-for="star in book.stars"> 
          </div>
          <div class="flex items-stretch justify-between space-x-2">
            <button style="background: #26a9e0;flex: 1;" class="px-4 rounded-lg font-bold text-lg text-white" @click="navigate('/book/' + book.id)">Подробнее</button>
            <img src="../assets/bookmark-2.svg" alt="" width="45" class="p-2 rounded-xl" 
            style="background: #ecf6fe;">
          </div>
        </div>
      </div>






    </div>

  </div>




  <div class="category p-4 my-2 lg:px-16" v-if="data !== null">

    <div class="flex space-x-16 mb-4 items-center">
      <h1 class="text-2xl font-bold">Топ продажи</h1>
      <img src="../assets/arrow-right.svg" alt="" width="40">
    </div>

    <img v-if="data.topSelling.length == 0" src="../assets/nothing.png" alt="nothing found" width="300">
    
    <div class="flex items-stretch space-x-4 overflow-x-auto slider" style="scroll-snap-type: x mandatory;">

      <div class="card border-2 p-4 rounded-lg hover:shadow-xl flex flex-col justify-between" v-for="(book,index) in data.topSelling"
      :key="index" style="max-width: 170px;">
        <div>
          <div class="book_images" style="min-height: 230px;">
            <img :src="book.cover" alt="" height="280" width="150">
          </div>
          <div class="flex items-center justify-between">
            <h2 class="text-start text-2xl mb-2 text-red-500 mt-4">{{ book.cur_price }} c.</h2>
          </div>

          <h1 class="text-start text-sm font-semibold break-words" style="max-width: 120px;">{{ book.name }}</h1>
          <h2 class="text-start text-sm font-light mb-4" style="max-width: 120px;">{{ book.author }}</h2>

          
        </div>

        <div>
          <div class="flex items-center mb-4" style="margin-top: auto">
              <img src="../assets/star_active.png" alt="" width="25" v-for="star in book.stars"> 
          </div>
          <div class="flex items-stretch justify-between space-x-2">
            <button style="background: #26a9e0;flex: 1;" class="px-4 rounded-lg font-bold text-lg text-white" @click="navigate('/book/' + book.id)">Подробнее</button>
            <img src="../assets/bookmark-2.svg" alt="" width="45" class="p-2 rounded-xl" 
            style="background: #ecf6fe;">
          </div>
        </div>

      </div>
    </div>


  </div>
















</template>


<script>
//© 2023, Читай-город @ is an alias to /src
import '../assets/tailwind.css'
import '../assets/utils.css'
import axios from 'axios'


export default {
  name: 'HomeView',
  components: {
  },
  data: () => ({
    books: null,
    data: null,
    showSearchResults: false
  }),
  methods: {
    navigate(To) {
      this.$router.push(To)
    },
    addToCart(id) {
      this.$store.state.cartBooks.push(id)
      // this.$store.state.newInCart += 1

      console.log(this.$store.state.cartBooks)
    }
  },
  computed: {
    mainSearch() {
      return this.$store.state.searchInput
    }
  },
  watch: {
    mainSearch() {
      console.log(this.$store.state.searchInput)
      this.showSearchResults = true
    }
  },
  async mounted() {
    if(this.$store.state.searchInput !== '') {
      this.showSearchResults = true
    }

    await axios.get(`${process.env.VUE_APP_API_URL}/getMainData/`)
      .then(data => {
        this.data = data.data
        console.log(this.data)
      })
      .catch(e => {
        console.log(e)
      })
  }
}
</script>


<style>
  .slider > div {
    scroll-snap-align: start;
  }
  .slider::-webkit-scrollbar {
    display: none;
  }
</style>
