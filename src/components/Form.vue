<template>
   <section class="mt-4 mx-auto w-75 bg-white overflow-hidden border rounded shadow-sm">
      <div class="bg-dark bg-opacity-50 px-3 py-3 text-center">
         <p class="mb-0 fw-bold text-light fs-3" >Register</p>
      </div>
      <form class="px-3 py-2">
         <div class="mb-3">
            <input v-model="form.firstname" class="form-control" type="text" id="firstname" placeholder="firstname" required="" />
         </div>
         <div class="mb-3">
            <input v-model="form.lastname" class="form-control mb-3" type="text" id="lastname" placeholder="lastname" required="" />
         </div>
         <div class="mb-3">
            <input v-model="form.email" @input="emailValidation" class="form-control mb-3" type="email" id="email" placeholder="email" required="" />
            <p v-if="form.validEmail === true" class="text-success" >{{ form.alertText.email }}</p>
            <p v-else-if="form.validEmail === false" class="text-danger" >{{ form.alertText.email }}</p>
         </div>
         <div class="mb-3">
            <input v-model="form.password" class="form-control mb-3" type="password" id="password" placeholder="password" required="" />
         </div>
         <div class="mb-3">
            <input v-model="form.confirmPassword" class="form-control mb-3" type="password" id="passwordConfirm" placeholder="Confirm password" required="" />
         </div>
         <div class="mb-3 d-flex">
            <button class="btn btn-primary w-75" type="submit">Submit</button>
            <button class="btn btn-light border ms-2" type="reset">Reset</button>
         </div>
      </form>
   </section>
   
   <pre class="mt-3">
      {{ form }}
   </pre>
   
   <pre class="mt-3">
      {{ log }}
   </pre>
   
</template>

<script>
   
   export default {
      data() {
         return {
            form: {
               firstname: "",
               lastname: "",
               email: "",
               password: "",
               confirmPassword: "",
               validEmail: false,
               validPassword: false,
               alertText: {
                  email: "",
                  password: ""
               }
            },
            log: ""
         }
      },
      methods: {
         emailValidation() {
            const email = this.form.email.split('');
            if ( email.includes("@") ) {
               let domain = email.join('').split('@')[1].split('')
               if (domain.includes('.')) {
                  this.form.validEmail = true;
                  this.form.alertText.email = "Your email valid";
               } else {
                  this.form.validEmail = false;
                  this.form.alertText.email = "Not valid email !";
               }
            } else {
               this.form.validEmail = false
               if (email.length <= 0) {
                  this.form.alertText.email = "Empty input";
               } else {
                  this.form.alertText.email = "Not valid email !";
               }
            }
         }
      }
   }
   
</script>