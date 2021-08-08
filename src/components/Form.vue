<template>
   <section class="w-75 mx-auto mt-3 rounded shadow overflow-hidden border bg-white">
      <div class="bg-dark bg-opacity-75 text-light px-3 py-3 text-center">
         <p class="mb-0 display-6 fw-bold">Sign In</p>
       </div>
      <form @submit="login" class="mt-3 px-3 py-2" accept-charset="utf-8">
         <div class="mb-3">
            <label class="form-label" for="username">Username</label>
            <input v-model="form.username" class="form-control" type="text" name="username" id="username"  />
         </div>
         <div class="mb-3">
            <label class="form-label" for="password">Password</label>
            <input v-model="form.password" :type="showPassword ? 'text' : 'password'" class="form-control" name="password" id="password"  />
         </div>
         <div class="mb-3">
            <input v-model="form.showPassword" class="form-check-input me-2" type="checkbox" name="show-password" id="show-password" />
            <label class="form-check-label" for="show-password">Show password ?</label>
         </div>
         <div class="w-100 d-flex mb-3">
            <button class="btn btn-primary w-75" type="submit">Login</button>
            <button class="btn btn-light border border-dark mx-2" type="reset">Reset</button>
         </div>
      </form>
   </section>
   
   
</template>

<script>
   export default {
      data() {
         return {
            form: {
               username: "",
               password: "",
               showPassword: true
            }
         }
      },
      methods {
         login(event) {
            
         }
      }
   }
</script>