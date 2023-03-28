<script lang="ts">
  import { space } from 'svelte/internal';
import { ImageStatus } from '../types.d';
import svelteLogo from './assets/svelte.svg'
  import CloudinaryLogo from './cloudinaryLogo.svelte';
  import Counter from './lib/Counter.svelte'
  import StepEdit from './StepEdit.svelte';
  import StepUpload from './StepUpload.svelte';
  import { imageStatus } from './store'
  import Description from './lib/description.svelte';

</script>

<div class="max-w-xl m-auto  place-content-center w-full h-screen p-2" >
  
  <header class="max-w-3xl mx-auto py-2 px-4 flex justify-between items-center">
    
<h1 class="text-3xl font-bold text-blue-900 tracking-tighter">New<span class="text-indigo-500 text-xl">Styles</span></h1>
<h2 class="text-5xl font-extrabold tracking-tight text-black md:text-6xl dark:text-white">
  
  <span class="block text-indigo-400 dark:text-indigo-500">
    Edita tu foto al instante
  </span>
  <p class='font-pt-serif font-normal text-md md:text-xl md:font-normal'> Diga adiós a la edición manual, con esta New stylos,podes hacerlos rapido y sencillo, una herramienta en linea y gratuita</p>
</h2>


</header>
<main class="flex justify-around md:block mt-8 md:mt-0 md:flex-1 ">
  {#if $imageStatus===ImageStatus.READY ||$imageStatus===ImageStatus.UPLOADING }
  <StepUpload/>
  {:else if $imageStatus===ImageStatus.DONE}
  <StepEdit/>
  {/if}
  <br/>
  <div>
  
  <Description/>
  </div>
<br/>
</main>
<footer class="p-5 fñex fñex-col text-xs sm:gap-4 lg:flex-row lg:gap-0 justify-around items-center text-white lg:text-xl w-full mx-auto bg-[#07182E]"> Hecho con <a href="https://cloudinary.com" target="_black" rel="noreferrer"><CloudinaryLogo/></a>
  <div class="card2 scale-[0.7] sm:scale-100 mx-auto">

  
</footer>
</div>
<style>
  @media(max-width:800px){
    .p{
      padding: 3rem;
      width: 100%;
      
    }
    .span{
      filter: invert(1) drop-shadow(0 0 0.3rem #ffffff70);
    }
  }
  @media(min-width:300px){
    .p{
      height: 80px;
      grid-template-columns: repeat(2, 50%);
    }
  }
  p{
    display: block;
    margin-block-start: 1em;
    margin-block-end: 1em;
    margin-inline-start: 0px;
    margin-inline-end: 0px;
  }
  p:hover{
    width: 300px;
    height: 200px;
    top: -30px;
    right: 50px;
    border-radius: 350px;
    color: rebeccapurple;
  }
  span{
    display: block;
    font-weight: 700;
    
    padding-left: 1rem;
    padding-right: 1rem;
    flex-direction: column;
   

  }
  h2{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    vertical-align: baseline;
  }
  
</style>
