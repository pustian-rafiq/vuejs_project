<template>
  <div id="app">
    <Navbar @searched="searchItem"></Navbar>
 
      <div class="container">
          <div class="row ">
            <div class="col-sm-9">
              <Inventory @addItemEvent="addItem" :items="items"></Inventory>
            </div>

            <div class="col-sm-3">
              <Cart @removedItem="itemRemoved" :items="cart"></Cart>
          </div>
          </div>
      </div>
  </div>
</template>

<script>
import Navbar from './components/Navbar'
import Cart from './components/Cart'
import Inventory from './components/Inventory'
import data from './data.js'
 
export default {
     data(){
       return {
         items: [],
         cart: [],
       }
     },
     components: {
         Navbar,
         Cart,
         Inventory,
     },
     mounted(){
       this.items = data
       
     },
     methods:{
       addItem(item){
         this.cart.push(item)
       },
       itemRemoved(item){
         this.cart.splice(item,1)
       },
       searchItem(keyword){
         this.items = data.filter(item =>{
          return item.title.toLowerCase().indexOf(keyword.toLowerCase()) !== -1
         })
       }
     }
}
</script>

<style>
.container{
  padding-top: 10px;
}
.card img{
  height: 250px;
}
</style>
