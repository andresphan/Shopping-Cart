<template>
  <div class="card text-left mt-3">
    <img class="card-img-top" :src="product.image">
    <div class="card-body">
      <h4 class="card-title">{{ product.name }}</h4>
      <p class="card-text" font-weight-bold>{{ product.price }} VND</p>
    </div >
    <div class="mb-2"> <button class="btn btn-danger ml-2" @click="handleBuy(product)">Mua</button>
    <button class="btn btn-info ml-2" @click="handleOpenModal">Chi tiết</button>
</div>
   
  </div>
  <Teleport to="#app">
     <app-modal :isOpen="IsOpenDetail" :handleClose="handleCloseModal"> 
    <h1><ProductDetailVue  :productItem="product"
></ProductDetailVue></h1> 
    </app-modal>

  </Teleport>
</template>

<script>
import AppModal from './AppModal.vue';
import ProductDetailVue from './ProductDetail.vue';
export default {
  data(){
return{
  IsOpenDetail:false,

}
  },
  components: { AppModal ,
    ProductDetailVue

  },
  props:{
    product:{
        type:Object
    }
  },
  methods:{
     handleBuy(product)
     {
      this.$emit('handle-buy',product);
     },
     handleCloseModal()
     {
        this.IsOpenDetail=false;
    

     },
     handleOpenModal()
     {
        this.IsOpenDetail=true;
    

     }



  }
}
</script>

<style>

</style>