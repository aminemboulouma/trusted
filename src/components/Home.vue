<template lang="html">
  <div class="home">
    <div class="jumbotron"></div>

    <section class="search-container">
      <div class="search-top">
        
        <input id="search-bar" type="text" name="search" value="Tesla Model S" class="form-control">
      </div>
      <div class="search-bottom">

        <div class="dropdown">
        <button class="btn btn-secondary dropdown-toggle" type="button" id="dropdownMenuButton" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false" style="margin:10px; margin-top:30px;">
          Brand
        </button>
        <div class="dropdown-menu" aria-labelledby="dropdownMenuButton">
          <a class="dropdown-item" href="#">Action</a>
          <a class="dropdown-item" href="#">Another action</a>
          <a class="dropdown-item" href="#">Something else here</a>
        </div>
       </div>

        <div class="dropdown">
        <button class="btn btn-secondary dropdown-toggle" type="button" id="dropdownMenuButton" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false" style="margin:10px; margin-top:30px;">
          Model
        </button>
        <div class="dropdown-menu" aria-labelledby="dropdownMenuButton">
          <a class="dropdown-item" href="#">Action</a>
          <a class="dropdown-item" href="#">Another action</a>
          <a class="dropdown-item" href="#">Something else here</a>
        </div>
       </div>


        <div class="dropdown">
        <button class="btn btn-secondary dropdown-toggle" type="button" id="dropdownMenuButton" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false" style="margin:10px; margin-top:30px;">
          Price range
        </button>
        <div class="dropdown-menu" aria-labelledby="dropdownMenuButton">
          <a class="dropdown-item" href="#">Action</a>
          <a class="dropdown-item" href="#">Another action</a>
          <a class="dropdown-item" href="#">Something else here</a>
        </div>
       </div>


    <div class="dropdown">
        <button class="btn btn-secondary dropdown-toggle" type="button" id="dropdownMenuButton" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false" style="margin:10px; margin-top:30px;">
          Rate
        </button>
        <div class="dropdown-menu" aria-labelledby="dropdownMenuButton">
          <a class="dropdown-item" href="#">Action</a>
          <a class="dropdown-item" href="#">Another action</a>
          <a class="dropdown-item" href="#">Something else here</a>
        </div>
       </div>


       
      </div>
    </section>

    <section class="car-boxes">
      <div class="car" v-for="car in cars">
        <div class="img-container">
        <a href="../../detail/index.html">
          <img :src="car.img">
        </a>
        </div>
        <div class="text-container">
          <p class="car-id">{{ car.make }} {{ car.model }}</p>
          <p class="car-information"><span>Price: {{ car.price }}</span><span>Milage: {{ car.milage }}</span></p>
        </div>
      </div>
    </section>

    <!-- <router-link tag="div" class="btn btn-1" to="/score">SCORE／分数</router-link>
    <router-link tag="div" class="btn btn-2" to="/game">{{ firstTime ? "COMMENCER/开始" : "CONTINUER／继续" }}</router-link> -->
  </div>
</template>

<script>
import Slider from './Slider.vue'

import { cars } from '../data/cars.js'

export default {
  data () {
    return {
      cars: cars,
      search: '',
    }
  },
  components: {
    'slider': Slider,
  },
  watch: {
    search (newSearch, oldSearch) {
      this.debouncedGetResults()
    }
  },
  created: function () {
    this.debouncedGetResults = _.debounce(this.getResults, 500)
  },
  methods: {
    getResults: function() {
      this.results
    }
  }
}
</script>

<style lang="css" scoped>
.jumbotron {
  height: 420px;
  width: 100vw;
  background-image: url("../assets/banner1.jpg");
  background-size: cover;
}

#menu a {
  color: #12528A;
  font-size: 1.05em;
}

.search-container {
  display: flex;
  flex-direction: column;
  height: 80px;
  width: 100vw;
  background-color: #cccccc;
  position: relative;
}

.search-top {
  display: flex;
  justify-content: center;
}

#search-bar {
  width: 70vw;
  height: 3rem;
  font-size: 1.5rem;
  position: absolute;
  top: -1.5rem;
}

.search-bottom {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 2rem;
}

.search-bottom select {
  margin: 0 1rem;
  font-size: 1rem;
}

search {
  display: inline;
}

#results {
  background: #4E4B74;
}

.car-boxes {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-evenly;
  background-color: #cccccc;
}

.car {
  border: 2px solid black;
  width: 350px;
  height: 360px;
  margin: 1em;
}

.img-container {
  width: 346px;
  height: 260px;
  background-color: #cccccc;
}

.img-container img {
  max-width: 100%;
  max-height: 100%;
}

.text-container {
  padding: 0.5rem 0.5rem 0.5rem 0.5rem;
}

.car-id {
  text-align: center;
}

.car-information {
  display: flex;
  justify-content: space-between;
}

.buy-btn {
  width: 330px;
  height: 40px;
  font-size: 20px;
  margin-top: 5px;
}
</style>
