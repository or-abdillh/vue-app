<template>
   <section class="container px-4 py-3 ">
      <h3 class="bg-dark rounded px-3 py-3 text-light text-center fw-bold mt-3">BMI CALCULATOR</h3>
      <div class="d-flex mt-3">
         <button 
         @click="gender = 'male'"
         :class="gender === 'male' ? 'text-white' : 'text-secondary'"
         class="btn btn-dark d-flex flex-wrap justify-content-center align-item-center w-50 px-3 py-3" type="button">
            <i class="fas fa-mars display-1 w-100"></i>
            <small class="mt-2 fw-bold" >MALE</small>
         </button>
         
         <button
         @click="gender = 'female'"
         :class="gender === 'female' ? 'text-white' : 'text-secondary'"
         class="btn btn-dark d-flex flex-wrap justify-content-center align-item-center ms-3 w-50 px-3 py-3" type="button">
            <i class="fas fa-venus display-1 w-100"></i>
            <small class="mt-2 fw-bold" >FEMALE</small>
         </button>
      </div>
      
      <div class="mt-3 w-100">
         <div class="bg-dark text-center px-3 py-3 rounded">
            <small class="fw-bold text-light" >HEIGHT</small>
            <h1 class="text-light mt-2 fw-bold display-1" >
               {{ height }}
               <small style="font-size: 22px">cm</small>
            </h1>
            <div class="mt-3 mb-2 d-flex justify-content-center">
               <input
               v-model.number="height"
               min="100" max="220"
               class="w-75" type="range"/>
            </div>
         </div>
      </div>
      
      <div class="d-flex mt-3">
         <div class="bg-dark d-flex text-light rounded flex-wrap justify-content-center align-item-center w-50 px-4 py-3">
            <small class="w-100 text-center" >WEIGHT</small>
            <h1 class="fw-bold display-2 mt-2" >
               {{ weight }}
               <small style="font-size: 18px" >kg</small>
            </h1>
            <div class="w-100 d-flex justify-content-between mt-2">
               <button 
               @click="weight -= 1"
               class="btn btn-warning py-1 fw-bold" type="button">-</button>
               <button
               @click="weight += 1"
               class="btn btn-warning py-1 fw-bold" type="button">+</button>
            </div>
         </div>
         
         <div class="bg-dark ms-3 d-flex text-light rounded flex-wrap justify-content-center align-item-center w-50 px-4 py-3">
            <small class="w-100 text-center" >AGE</small>
            <h1 class="fw-bold display-2 mt-2" >
               {{ age }}
            </h1>
            <div class="w-100 d-flex justify-content-between mt-2">
               <button
               @click="age -= 1"
               class="btn btn-warning py-1 fw-bold" type="button">-</button>
               <button
               @click="age += 1"
               class="btn btn-warning py-1 fw-bold" type="button">+</button>
            </div>
         </div>
      </div>
      
      <div class="mt-3">
         <button 
         v-if="!isCalculate"
         @click="calculate"
         class="btn btn-primary fs-5 w-100 fw-bold py-3" type="button">Calculate Your BMI</button>
      </div>
      
      <div v-if="isCalculate" class="mt-3">
         <div class="bg-dark rounded text-center px-3 pt-4 py-2 w-100">
            <small class="text-muted d-block fs-6 fw-bold" >Results</small>
            <small class="text-green fs-4 fw-bold" >{{ classification }}</small>
            <h2 class="text-light fw-bold display-1" style="font-size: 4rem" >{{ BMI }}</h2>
            <span class="d-block mt-3">
               <small class="text-muted fs-6" >Normal BMI</small>
               <p class="text-green">18.6 - 24.9</p>
            </span>
            <span class="d-block mb-3" >
               <small class="text-muted fs-6" >Risk of comorbidities</small>
               <h2 class="text-light fw-bold" >{{ message }}</h2>
            </span>
            
            <button 
            @click="isCalculate = false"
            class="btn btn-primary fw-bold mb-3 mt-3 px-4 py-2" type="button">Re calculate your BMI</button>
         </div>
      </div>
      
   </section>
   
</template>

<script>
   
   export default {
      data() {
         return {
            gender: 'male',
            height: 160,
            weight: 75,
            age: 25,
            BMI: 0,
            classification: 'classification',
            message: 'message',
            isCalculate: false
         }
      },
      methods: {
         calculate() {
            //Rumus BMI berat badan dibagi kuadrat tinggi dalam meter
            let heightM = this.height / 100;
            this.BMI =  ( this.weight / (heightM * heightM) ).toFixed(1);
            this.setClassif();
            setTimeout(() => {
               this.isCalculate = true;
            }, 500);
         },
         setClassif() {
            
            if ( this.BMI < 18.5 ) {
               this.classification = 'Underweight';
               this.message = 'Low, but risk of other clinical problems increased';
            } else if ( this.BMI <= 24.9 ) {
               this.classification = 'Normal';
               this.message = 'Average';
            } else if ( this.BMI <= 29.9 ) {
               this.classification = 'Overweight';
               this.message = 'Middly increased';
            } else if ( this.BMI <= 34.9 ) {
               this.classification = 'Obese class 1';
               this.message = 'Moderate';
            } else if ( this.BMI <= 39.9 ) {
               this.classification = 'Obese class 2';
               this.message = 'Severe';
            } else {
               this.classification = 'Obese class 3';
               this.message = 'Very severe';
            }
         }
      }
   }
   
</script>

<style>
   #app {
      font-family: 'Poppins', Sans-Serif;
      font-weight: 600;
   }
   .text-green {
      color: #1dd53a;
   }
</style>