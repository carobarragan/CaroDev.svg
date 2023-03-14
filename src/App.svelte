<script lang="ts">
  import { ImageStatus } from '../types.d';
import svelteLogo from './assets/svelte.svg'
  import CloudinaryLogo from './cloudinaryLogo.svelte';
  import Counter from './lib/Counter.svelte'
  import StepEdit from './StepEdit.svelte';
  import StepUpload from './StepUpload.svelte';
  import { imageStatus } from './store';
</script>

<div class="max-w-xl m-auto grid grid-cols-1 place-content-center w-full h-screen p-4">
  <header class="flex justify-center py-10">
<h1 class="text-3xl font-bold text-blue-900 tracking-tighter">remove<span class="text-blue-600">bg</span></h1>
</header>
<main class="w-ful block">
{#if $imageStatus===ImageStatus.READY ||$imageStatus===ImageStatus.UPLOADING }
<StepUpload/>
{:else if $imageStatus===ImageStatus.DONE}
<StepEdit/>
{/if}
</main>
<footer class="flex justify-center items-center gap-x-2 font-semibold pt-10"> Hecho con <a href="https://cloudinary" target="_black" rel="noreferrer"><CloudinaryLogo/></a></footer>
</div>
