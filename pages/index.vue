<template>
  <div class="h-screen bg-fond flex flex-col justify-center overflow-hidden">
    
    <div class="flex justify-center">
      
      <img class="w-1/3" src="@/assets/menu/logo/Logo_big.png" alt="Logo radio mazette">
      
    </div>
    <div class="flex justify-center mt-12 mb-12">
      <p class="text-white text-3xl">Le transfert d'énergie par la diffusion</p>
    </div>
    <div class="flex justify-center">
      <NuxtLink to="/home" class="text-white font-bold text-2xl bg-blueDark py-2 px-6 rounded-full shadow-buttonShadow">Écoutez</NuxtLink>
    </div>
    <div class="absolute right-0 bottom-0 w-2/4">
      <img class="" src="@/assets/menu/logo/LogoMazetteBack.png" alt="Logo radio mazette pour fond de site situé en bas à droite">
    </div>
    
  </div>
</template>

<script>
  export default {
    layout:'firstHome',
    name: 'Index'
  }
</script>

<style lang="scss">
#logo_first_home {
  div {
    h1:first-child {
      font-size: 6rem;
    }
    h1:last-child {
      font-size: 8rem;
    }
  }
}
</style>