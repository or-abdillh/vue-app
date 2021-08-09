<template>

   <section class="container bg-white mt-5 mx-auto px-5 py-3">
      <img class="img-thumbnail rounded-circle" src="src/assets/1613282023468-picsay.png"  alt="hero" />
      <h2 class="mt-4 mb-3" >Sign Up</h2>
      <form >
         <div class="mb-3 d-flex">
            <input v-model="formValues.firstName" class="form-control w-50 me-2 border border-2 border-secondary" type="text" name="firstName" id="firstName" placeholder="First name" required="" />
            <input v-model="formValues.lastName" v-on:input="setFullName" class="form-control w-50 border border-2 border-secondary" required="" type="text" name="lastName" id="lastName" placeholder="last name" />
         </div>
         <div class="mb-3">
            <input v-model="formValues.email" class="form-control border border-2 border-secondary" required="" type="email" name="email" id="email" placeholder="E-mail" />
         </div>
         <div class="input-group d-flex flex-nowrap mb-2">
            <input v-model="formValues.password" v-on:input="pwdValidation" v-on:blur="clearAlert" class="form-control border border-2 border-secondary" required="" v-bind:type="isHidden ? 'password' : 'text'" name="password" id="password" placeholder="Create password"/>
            <span v-on:click="showPassword" class="input-group-text bg-secondary text-light border border-2 border-secondary" >
               <i v-if="isHidden" class="fas fa-eye-slash"></i>
               <i v-else class="fas fa-eye" ></i>
            </span>
         </div>
         <div class="mb-3">
            <p v-if="!isPwdValid" class="fw-bold mb-0" >
               <small>Password must be at least 8 characters long.</small>
            </p>
         </div>
         <div v-if="isCreated" class="alert alert-success py-2" role="alert">
            Account was created. Please, check your inbox
         </div>
         <div class="mb-2">
            <button v-bind:disabled="!isPwdValid" v-on:click="createAccount" class="btn btn-primary fw-bold px-3 py-2 w-100" type="button">
               {{ btnMsg }}
            </button>
         </div>
         <div class="mb-3">
            <p class="fw-bold mb-0">
               <small>
                  Already a member?
                  <a href="#" class="text-decoration-none" >Sign in</a>
               </small>
            </p>
         </div>
      </form>
   </section>
   
</template>

<script>
   
   export default {
      data() {
         return {
            isPwdValid: false,
            isCreated: false,
            isHidden: true,
            btnMsg: 'Sign Up',
            formValues: {
               firstName: '',
               lastName: '',
               fullName: '',
               email: '',
               password: ''
            }
         }
      },
      methods: {
        createAccount() {
            this.btnMsg = 'loading';
            setTimeout(() => {
               this.btnMsg = 'Success';
               this.isCreated = true;
            }, 1000)
         },
         showPassword() {

            this.isHidden = !this.isHidden;
         }
      },
      computed: {
         setFullName() {
            let form = this.formValues;
            form.fullName = `${form.firstName} ${form.lastName}`;
         },
         pwdValidation() {
            let form = this.formValues;
            let lengthPwd = form.password.split('').length;
            
            if (lengthPwd < 8) this.isPwdValid = false;
            else this.isPwdValid = true;
         },
         clearAlert() {
            let form = this.formValues;
            let lengthPwd = form.password.split('').length;
            
            if(lengthPwd <= 0) this.isPwdValid = true;
         }
      }
   }
   
</script>

<style scoped>
   img {
      width: 55px;
   }
</style>




