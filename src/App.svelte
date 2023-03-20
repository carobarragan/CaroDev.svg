<script lang="ts">
  import { space } from 'svelte/internal';
import { ImageStatus } from '../types.d';
import svelteLogo from './assets/svelte.svg'
  import CloudinaryLogo from './cloudinaryLogo.svelte';
  import Counter from './lib/Counter.svelte'
  import StepEdit from './StepEdit.svelte';
  import StepUpload from './StepUpload.svelte';
  import { imageStatus } from './store'

</script>

<div class="max-w-xl m-auto grid grid-cols-1 place-content-center w-full h-screen p-4">
  
  <header class="flex justify-center py-10">
<h1 class="text-3xl font-bold text-blue-900 tracking-tighter">New<span class="text-blue-600">Styles</span></h1>
</header>
<main class="w-ful block">
{#if $imageStatus===ImageStatus.READY ||$imageStatus===ImageStatus.UPLOADING }
<StepUpload/>
{:else if $imageStatus===ImageStatus.DONE}
<StepEdit/>
{/if}
</main>
<footer class="p-5 fñex fñex-col text-xs sm:gap-4 lg:flex-row lg:gap-0 justify-around items-center text-white lg:text-xl w-full mx-auto bg-[#07182E]"> Hecho con <a href="https://cloudinary.com" target="_black" rel="noreferrer"><CloudinaryLogo/></a>
  <div class="card2 scale-[0.7] sm:scale-100 mx-auto">
    <div
    x-show="isOpen"
    x-transition:enter="transition ease-out duration-100 transform "
    x-transition:enter-start="opacity-0 scale-200"
    x-transition:enter-end="opacity-50 scale-100"
    x-transition:leave="transition ease-in duration-75 transform"
    x-transition:leave-start="opacity-100 scale-100"
    x-transition:leave-end="opacity-0 scale-95"
    class="origin-top-right absolute right-0 mt- w-56 rounded-md shadow-lg">contacto   <a class="" href="https://github.com/carobarragan"> git</a> <div>
  
  </div>
  
  
</footer>
</div>
