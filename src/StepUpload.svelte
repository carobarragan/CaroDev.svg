<script lang="ts">
    import Dropzone from "dropzone"
    import "dropzone/dist/dropzone.css"
 
    import {imageStatus, originalImage} from "./store"
      import { ImageStatus } from "../types.d"
import{onMount} from "svelte"
onMount(()=>{
    const dropzone=new Dropzone('#dropzone',{
        uploadMultiple:false,
        acceptedFiles:'.jpg,.png,.webp',
        maxFiles:1,
    })
    dropzone.on('sending',(file,xhr,formData)=>{
        formData.append("upload_preset","ml_default")
        formData.append("timestamp", Date.now()/1000)
        formData.append("api_key",824285191819181)
    })
    dropzone.on("success",(file,response)=>{
        const{
            secure_url:url
        }=response
         imageStatus.set(ImageStatus.DONE)
         originalImage.set(url)
         //crear la imagen fondo transparente
         // y guardar en el background
         console.log(response)
    })
    dropzone.on("error",(file,response)=>{
        console.log("ha ido mal")
        console.log(response)
    })
})
</script>
<form
id="dropzone"
class="shadow-2xl border-dashed border-2 border-gray-300 rounded-lg aspect-video w-full flex items-center justify-center flex-col"
action=" https://api.cloudinary.com/v1_1/djx40lpsg/image/upload"
> 
{#if $imageStatus===ImageStatus.READY}
<button class="pointer-events-none bg-blue-600 rounded-full text-bold text-white text-xl px-6 py-4">
Upload Files

</button>
<strong class="text-lg mt-4 text-gray-800">Or drop a file</strong>
{/if}
</form>