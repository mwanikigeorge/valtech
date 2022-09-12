<script setup lang="ts">
  import {ref, onMounted} from 'vue'
  import citiesData from '@/data/cities.json'

interface city  {
  name: string,
  country: string,
  description: string,
  image: string,
}
const cities = ref<Array<city>>([])

onMounted(() => {
  cities.value = citiesData
})
</script>

<template>
  <div class="wrapper">
    <div class="banner">
      <img class="card-img-top" src="https://images.unsplash.com/photo-1650388354143-3ba4c71d0397?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1740&q=80" alt="sun set">
      <div class="card-body">
        <h5 class="card-subtitle">front-end</h5>
        <h5 class="card-title">Valtech_</h5>
        <p class="banner-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
      </div>
    </div>

    <div class="cities">
  <template v-for="item in cities" :key="item.id">
    <div class="card">
      <div class="overlay"></div>
      <img class="card-img-top" :src="item.image" alt="Card image cap">
      <div class="card-body">
        <div class="content">
        <h5 class="card-subtitle">{{item.country}}</h5>
        <h2 class="card-title">{{item.name}}</h2>
        <div class="desc">
          <p class="card-text">{{item.description}} </p>
        <button>
          Explore More
        </button>
        </div>
        </div>
        
      </div>
    </div>
  </template>
  </div>
    </div>
</template>

<style scoped>
  .cities {
    display: grid;
    grid-gap: 1.5rem;

  }

  h5, h2{
    margin: 0;
  }
  .card{
     height: 25rem;
      border-radius: 10px;
      filter: drop-shadow(0 0 1em #cececeaa);
  }

  .banner{
    position: relative;
    height: 35rem;
    width: 100%;
    margin-bottom: 2rem;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: #f5f5f5;
    border-radius: 10px;
  }

  .banner-title{
    font-size: 2rem;
    font-weight: bold;
    color: #fff;
  }

  .card-title{
    font-size: 2rem;
    font-weight: 400;
    text-transform: uppercase;
    margin-top: 0.6rem;
  }
  .card-subtitle{
    letter-spacing: 0.2rem;
    font-weight: 300;
    text-transform: uppercase;
  }


  .card-img-top{
    width: 100%;
    height: 100%;
    object-fit: cover;
    border-radius: 20px;
  }
  .card-body{
    position: absolute;
    display: flex;
    flex-direction: column;
    justify-content: center;
    width: 100%;
    top: 0;
    color: aliceblue;
    height: 100%;
    text-align: center;
  }

  .desc{
    margin: 3rem 0;
    opacity: 0;
    height: 0;
    transition: all 0.5s;
    font-weight: 300;
    will-change: transform;
  }
.card::before, .banner::before{
  content: "";
  border-radius: 20px;
  position: absolute;
  transition: all 0.5s;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0,0,0,0.3);
}

.content{
  transform: translateY(0px);
  transition: all 0.5s;
  padding:0px 1rem;
  will-change: transform;
}


 .card:hover:before{
  background-color: rgba(0,0,0,0.5);
}

.card:hover .content{
  transform: translateY(-80px);
}

.card:hover .desc{
  opacity: 1;
  /* max-height: 200px; */
  transform: translateY(0px);
}


@media (min-width: 768px) {
.cities {
    grid-template-columns: repeat(2, 1fr);
  }

}
@media (min-width: 1024px) {
  .cities {
      grid-template-columns: repeat(4, 1fr);
    }
  
    .card:first-child,
    .card:last-child {
      grid-column: span 2;
    }
}
</style>
