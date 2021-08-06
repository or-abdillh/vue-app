<template>
   <div :class="element.bgCard" class="border border-3 pt-3 w-75 mt-5 mx-auto px-3 py-2 shadow-lg rounded">
      <p :class="element.bgText" class="text-center" >{{ header }}</p>
      <h2 :class="element.bgText" class="text-center display-1 fw-bold">
         {{ count }}
      </h2>
      <div class="w-50 mx-auto justify-content-center  d-flex">
         <button v-on:click="increment" class="btn btn-primary border border-2 fw-bold mx-2">+</button>
         <button v-on:click="decrement" :disabled="over" class="btn btn-success border border-2 fw-bold mx-2">-</button>
      </div>
      
      <div class="mt-3 d-flex justify-content-center w-100" >
         <button :class="element.btnBg" v-on:click="changeMode" class="btn rounded-circle px-2 py-1">
         <i v-if="lightMode" class="fas fa-moon"></i>
         <i v-else="lightMode" class="fas fa-sun"></i>
      </button>   
      </div>
      
      <p class="text-center mt-3 text-muted" >{{ footer }}</p>
   </div>
</template>

<script>

   export default {
      data() {
         return {
            element: {
              bgCard: 'bg-white',
              btnBg: 'btn-dark',
              bgText: 'text-dark'
            },
            count: 0,
            over: true,
            lightMode: true,
            header: 'Counter App',
            footer: 'Made with Vue JS 3',
         }
      },
      methods: {
         increment() {
            this.count += 1;
            this.over = false;
         },
         decrement() {
            if (this.count > 0) {
               this.count -= 1;
               if (this.count === 0) this.over = true;
            }
         },
         changeMode() {
            this.lightMode = !this.lightMode;
            
            if (this.lightMode) {
               this.element.bgCard = 'bg-white';
               this.element.btnBg = 'btn-dark';
               this.element.bgText = 'text-dark';
            }
            else {
               this.element.bgCard = 'bg-dark';
               this.element.btnBg = 'btn-light';
               this.element.bgText = 'text-light';
            }
         }
      }
   }
</script>