<template>
     <ul class="list-group">
                <li class="list-group-item" >  
                  <span class="item-name"> Item Name</span>
                  <span class="item-price pull-right">Price</span>
                </li>
                 <hr>
                 <li class="list-group-item" v-for="(item,index) in items" :key="index">  
                  <span class="item-name">{{ item.title }}</span>
                  <span class="item-price pull-right">{{ item.price }}</span>
                  <button @click="itemRemoved(index)" class="btn btn-danger btn-sm pull-right">-Remove</button>
                </li>
                <hr>
                <li class="list-group-item">  
                  <span class="item-name">Total</span>
                  <span class="item-price pull-right">${{ totalCost }}</span>
                </li>
              </ul>
</template>


 <script>
 export default {
     props: ['items'],
     methods:{
       itemRemoved(item){
         this.$emit('removedItem',item)
       }
     },
     computed:{
       totalCost(){
         var total = 0
         this.items.forEach(item => {
           total += parseFloat(item.price)
         })
         return total
       }
     }
 }
 </script>

 <style >
 .item-name{
  font-size: 20px;
  margin-right: 20px;
 }
 </style>