<template>

   <section class="container bg-white mt-5 mx-auto px-5 py-3">
      <h2 class="mb-3" >Sign Up</h2>
      <form>
         <div class="mb-3 d-flex">
            <input class="form-control w-50 me-2 border border-2 border-secondary" type="text" name="firstName" id="firstName" placeholder="First name" />
            <input class="form-control w-50 border border-2 border-secondary" type="text" name="lastName" id="lastName" placeholder="last name" />
         </div>
         <div class="mb-3">
            <input class="form-control border border-2 border-secondary" type="email" name="email" id="email" placeholder="E-mail" />
         </div>
         <div class="mb-2">
            <input class="form-control border border-2 border-secondary" type="password" name="password" id="password" placeholder="Create password" />
         </div>
         <div class="mb-3">
            <p class="fw-bold mb-0" >
               <small>Password must be at least 8 characters long.</small>
            </p>
         </div>
         <div class="mb-2">
            <button class="btn btn-primary fw-bold px-3 py-2 w-100" type="submit">Sign Up</button>
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