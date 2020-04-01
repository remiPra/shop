<template>
  <div class="w-25 p-3 product-container d-flex flex-column">
    <div class="d-flex flex-row justify-content-center">
      <img style="height: 150px" :src="product.img">
    </div>
    <div>
      <h3>{{ product.title }}</h3>
      <hr>
    </div>  
    <div>
      <p>{{ product.description }}</p>
    </div>
    <div>
      <span>{{ product.price }}</span>
      <button @click="addProductToCart" class="btn btn-primary btn-sm float-right">Commander</button>
    </div>
  </div>
</template>

<script>
  import {eventBus} from '../../main';

  export default {
    //   on le fait passer en propriété  product pluto que data car dans le v-for c'est lui qui st appelé
    props :['product'],
    methods:{
      addProductToCart() {
        //ajout de l'evenement a l'eventBus avec sa copie ...this.product
        eventBus.addProductToCart({...this.product});

      }

    }
  };
</script>

<style>
  .product-container {
    height: 400px;
  }
</style>