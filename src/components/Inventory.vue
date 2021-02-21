<template>
     <div class="row">
               
                   <div class="card" v-for="(item,index) in items" :key="index" style="width: 13rem;">
                    <img :src="item.photo" class="card-img-top" alt="Product Image">
                    <div class="card-body">
                      <h5 class="card-title">{{ item.title }}</h5>
                      <p class="card-text">{{ item.price }}</p>
                      <a href="#" class="btn btn-primary">+Add</a>
                    </div>
                 
                 </div>
             
                 
      </div>
</template>


 <script>
 export default {
     props: ['items']
 }
 </script>

 <style >
 
 </style>