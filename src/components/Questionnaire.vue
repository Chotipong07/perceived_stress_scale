<template>
  
  <div class="min-h-screen h-full bg-slate-100">
    <!-- <div class="fixed top-4 left-4 flex items-center justify-center bg-gray-100 border-2 border-gray-400 w-24 h-16 rounded-xl">
      <span class="sm:hidden">Mobile</span>
      <span class="hidden sm:block md:hidden">SM</span>
      <span class="hidden md:block lg:hidden">MD</span>
      <span class="hidden lg:block xl:hidden">LG</span>
      <span class="hidden xl:block 2xl:hidden">XL</span>
      <span class="hidden 2xl:block">2XL</span>
    </div> -->
    <HeaderTitle />
  <main>
    
    <Explanation />
    <LoopExample />
    
  </main>
</div>
</template>

<script>
import LoopExample from './LoopExample.vue';
import Explanation from '@/components/Explanation.vue'
import HeaderTitle from './HeaderTitle.vue';

export default {
  components: {
    LoopExample,
    Explanation,
    HeaderTitle,

  },
};
</script>



<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Itim&family=Noto+Sans+Thai:wght@400;500;600;700&display=swap');

main ,header{
  font-family: 'Noto Sans Thai', sans-serif;
  font-size: 20px;
  color: #676a6c;
  font-weight: normal;               
}  
</style>
