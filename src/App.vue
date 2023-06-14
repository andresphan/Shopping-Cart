<template>

<header>
  <TheHeader :cartList="cartList" @handle-delete-cart="handleDeletes" @handle-upordown="Handleupordown"/>
</header>
<main class="container">
<product-list-vue @handleBuy="handleBuy"/>

</main>

</template>

<script>
import ProductListVue from './components/ProductList.vue';
import TheHeader from './components/TheHeader.vue';


export default {
  name: 'App',
  components: {
    TheHeader,
    ProductListVue,
  },
  data(){
  return{
    cartList:[],

  }

  },
  methods:{
  handleBuy(product)
  {
    const index=this.cartList.findIndex((item)=>
      item.id===product.id);
    if(index!==-1)
    {
     this.cartList[index].amount+=1;
    }else{
      const newItem={...product,amount:1}
      this.cartList=[...this.cartList,newItem];
    }
   
   
  },
  handleDeletes(cart)
  {
    this.cartList=this.cartList.filter((item)=>item.id!==cart.id);
  },
  Handleupordown(params)
  {
    const{state,cart}=params;
    const index=this.cartList.findIndex((item)=>
      item.id===cart.id);
      if(index!==-1)
      {
        if(state)
        {
          if(this.cartList[index].amount<this.cartList[index].quantityInStock)
           this.cartList[index].amount+=1;
           else{
               alert("Không được tăng nữa");
           }

        }else{
          if(this.cartList[index].amount>1)
             this.cartList[index].amount-=1;
             else{
              alert("Bạn không thể giảm xuống được nữa!");
             }

        }
          

      }
  }


  }
}
</script>

<style>
#app{
  font-family: Avenir, Arial, Helvetica, sans-serif;
  -webkit-font-smoothing:antialiased;
  -moz-osx-font-smoothing:grayscale;
  text-align:center;
  color:#2c3e50;
  



}
</style>
