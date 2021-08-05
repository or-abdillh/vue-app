<template>
   <div :class="isChange ? 'bg-primary' : 'bg-white'" class="mx-2 mt-3 shadow border border-1 border-secondary rounded px-3 py-3">
      <div class="row w-100 d-flex justify-content-center align-items-center">
         <div class="col col-4 d-flex justify-content-center">
            <img :class="isChange ? 'bg-light' : 'bg-white'" class="border border-1 rounded-circle" src="./assets/1613282023468-picsay.png" width="90" alt="">
         </div>
         <div class="col col-7">
            <p class="fw-bold mb-0 fs-6" @title="name" >{{ name }}</p>
            <p :class="isChange ? 'text-white' : 'text-muted'" class="small" >{{ message }}</p>
            <div class="d-flex" >
               <a class="text-decoration-none text-black" :href="href">
                  <i v-for="item in icons" class="me-2 fs-4" v-bind:class="item.icon"></i>
               </a>   
            </div>
         </div>
      </div>
   </div>
   
   <div class="px-2 mt-3">
      <button @click="changeTheme" class="btn btn-primary px-3 py-2">
         Change Theme
         <i class="fas fa-exchange-alt ms-2"></i>
      </button>
   </div>
</template>

<script>
 export default {
    data() {
       return {
          isChange: false,
          name: 'OKA R. ABDILLAH',
          message: 'Junior Front End Developer',
          icons: [
             { icon: "fab fa-instagram"},
             { icon: "fab fa-facebook-square"},
             { icon: "fab fa-github-square"}
          ]
       }
    },
    methods: {
       changeTheme() {
          this.isChange = !this.isChange;
       }
    }
 }
</script>