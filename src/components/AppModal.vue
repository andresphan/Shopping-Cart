<template>
  <div v-if="isOpen" class="modals" @click="handleClick">
    <div class="modals__container" @click.stop>
        <div class="modals__header">
            <h1 class="modals__title">Cart</h1>
            <div class="modals__close" @click="handleClick"><i class="fa fa-times"></i></div>
        </div>
        <div class="modals__body">
            <slot></slot>
        </div>
        <div class="modals__footer"></div>
    </div>
  </div>
</template>

<script>
export default {
       props:{
          isOpen:{
            type:Boolean,

          },
          handleClose:{
                type:Function,
          }


       },
       methods:{
        handleClick(){
       this.handleClose();
       
        }
       }
}
</script>

<style>
.modals{
 position: fixed;
 z-index: 1;
 left:0;
 top:0;
 display:flex;
 width:100%;
 height:100%;
 background: rgba(0,0,0,0.4);




}

.modals__container{


    width:950px;
    margin:auto;
    margin-top:70px;
    background: white;
    border: 1px solid #888;
    padding:10px 20px;
}
.modals__header{
  display:flex;
  justify-content: space-between;
  align-items:center;



}

.modals__close{
   width:50px;
   height:50px;
   line-height:50px;
   border-radius:50%;
   text-align:center;
   font-size:30px;


}
.modals__close:hover{
    background-color:rgba(0,0,0,0.2) ;
    cursor:pointer;
}
</style>