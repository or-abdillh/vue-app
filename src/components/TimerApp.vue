<template>
   <section id="timerApp" v-bind:class="lightMode ? 'bg-white' : 'bg-dark'" class="w-75 rounded shadow mx-auto px-3 py-2 mt-4 border border-2" >
      <p v-bind:class="lightMode ? 'text-dark' : 'text-light'" class="text-center fw-bold mt-3" >{{ header.toUpperCase() }}</p>
      <div v-bind:class="lightMode ? 'border-dark text-dark' : 'border-secondary text-white'" class="border border-3 d-flex justify-content-center align-items-center circle px-3 py-2 mt-3 rounded-circle mx-auto" >
         <h1 class="display-1 mb-0">{{ timer }}</h1>
      </div>
      <div class="mt-3 w-75 d-flex justify-content-center mx-auto">
         <button v-bind:disabled="counter === 0 || isRun" v-on:click="decrement" class="w-50 btn btn-danger border"> -1s </button>
         <span v-bind:class="lightMode ? 'text-dark' : 'text-light'" class="px-3 py-2 border border-2 rounded mb-0 mx-2" >{{ counter }}s</span>
         <button v-bind:disabled="isRun" class="w-50 btn btn-success border" v-on:click="increment" > +1s </button>
      </div>
      <div class="w-75 mx-auto d-flex mt-2 flex-wrap justify-content-center">
         <button v-bind:disabled="hidden" v-on:click="runTimer" class="d-block w-100 btn btn-primary" >Start</button>
         <button v-on:click="changeMode" v-bind:class="lightMode ? 'btn-dark' : 'btn-light'" class="btn btn-circle mt-3 border rounded-circle">
            <i v-if="lightMode" class="fas fa-moon"></i>
            <i v-else="lightMode" class="fas fa-sun" ></i>
         </button>
      </div>
      <p class="text-muted text-center mt-2" >{{ footer }}</p>
   </section>
</template>

<script>
   
   export default {
      data() {
         return {
            header: 'Timer App',
            footer: 'Made With VUE JS 3',
            counter: 0,
            timer: 0,
            hidden: true,
            isRun: false,
            lightMode: true
         } 
      },
      methods: {
         runTimer: function() {
            
            this.timer = this.counter;
            this.hidden = true;
            this.isRun = true;
            
            let run = setInterval(() => {
               this.timer--;
               if (this.timer === 0) {
                  clearInterval(run);
                  this.isRun = false;
                  this.hidden = false;
               }
            }, 1000);
         },
         increment() {
            this.counter += 1;
            this.hidden = false;
         },
         decrement() {
            this.counter -= 1;
            if (this.counter === 0) this.hidden = true;
         },
         changeMode() {
            this.lightMode = !this.lightMode;
         }
      }
   }
   
</script>

<style>
   * {
      -webkit-user-select: none;
      user-select: none;
   }
   .circle {
      width: 100px;
      height: 100px;
   }
   .btn-circle {
      width: 50px;
      height: 50px;
   }
</style>