<template>
   <section class="px-4 py-3">
      <h3 class="text-center fw-bold mt-3">BMI CALCULATOR</h3>
      <div class="d-flex mt-4">
         <button class="btn btn-dark d-flex flex-wrap justify-content-center align-item-center w-50 px-3 py-3" type="button">
            <i class="fas fa-mars display-1 w-100"></i>
            <small class="mt-2 fw-bold" >MALE</small>
         </button>
         <button class="btn btn-dark d-flex flex-wrap justify-content-center align-item-center ms-3 w-50 px-3 py-3" type="button">
            <i class="fas fa-venus display-1 w-100"></i>
            <small class="mt-2 fw-bold" >FEMALE</small>
         </button>
      </div>
      
      <div class="mt-3 w-100">
         <div class="bg-dark text-center px-3 py-3 rounded">
            <small class="fw-bold text-light" >HEIGHT</small>
            <h1 class="text-light mt-2 fw-bold display-1" >
               180
               <small style="font-size: 22px">cm</small>
            </h1>
            <div class="mt-3 mb-2 d-flex justify-content-center">
               <input class="w-75" type="range" name="" id="" value="" />
            </div>
         </div>
      </div>
      
      <div class="d-flex mt-3">
         <div class="bg-dark d-flex text-light rounded flex-wrap justify-content-center align-item-center w-50 px-4 py-3">
            <small class="w-100 text-center" >WEIGHT</small>
            <h1 class="fw-bold display-2 mt-2" >75</h1>
            <div class="w-100 d-flex justify-content-between mt-2">
               <button class="btn btn-warning py-1 fw-bold" type="button">+</button>
               <button class="btn btn-warning py-1 fw-bold" type="button">-</button>
            </div>
         </div>
         <div class="bg-dark ms-3 d-flex text-light rounded flex-wrap justify-content-center align-item-center w-50 px-4 py-3">
            <small class="w-100 text-center" >AGE</small>
            <h1 class="fw-bold display-2 mt-2" >25</h1>
            <div class="w-100 d-flex justify-content-between mt-2">
               <button class="btn btn-warning py-1 fw-bold" type="button">+</button>
               <button class="btn btn-warning py-1 fw-bold" type="button">-</button>
            </div>
         </div>
      </div>
      
      <div class="mt-3">
         <button class="btn btn-primary w-100 fw-bold py-3 mb-3 " type="button">Calculate Your BMI</button>
      </div>
      
   </section>
   
</template>

<script>
   
   export default {
      data() {
         return {
            
         }
      }
   }
   
</script>

<style>
   
   #app {
      font-family: 'Poppins', Sans-Serif;
      font-weight: 600;
   }
   
   body {
      min-height: 120vh;
   }
      
</style>




