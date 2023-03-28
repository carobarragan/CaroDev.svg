<script lang="ts">
    import {Cloudinary} from '@cloudinary/url-gen'
    import{backgroundRemoval} from '@cloudinary/url-gen/actions/effect'
    import Dropzone from "dropzone"
    import "dropzone/dist/dropzone.css"
 
    import {imageStatus, modifiedImage, originalImage} from "./store"
      import { ImageStatus } from "../types.d"
import{onMount} from "svelte"

//creo mi instancia de cloudinary 
const cloudinary= new Cloudinary({
    cloud:{
        cloudName: 'djx40lpsg',
    },
    url:{
        secure:true
    }
})
onMount(()=>{
    const dropzone=new Dropzone('#dropzone',{
        uploadMultiple:false,
        acceptedFiles:'.jpg,.png,.webp',
        maxFiles:1,
    })
    dropzone.on('sending',(file,xhr,formData)=>{
        imageStatus.set(ImageStatus.UPLOADING)
        formData.append("upload_preset","ml_default")
        formData.append("timestamp", Date.now()/1000)
        formData.append("api_key",824285191819181)
    })
    //aca tengo la respuesta 
    dropzone.on("success",(file,response)=>{
        const{public_id:publicId, secure_url:url
        }=response
        
        //crear la imagen fondo transparente
        // y guardar en el background
        const imageWithoutBckground=cloudinary
        .image(publicId)
        .effect(backgroundRemoval())
       console.log( imageWithoutBckground.toURL())
         imageStatus.set(ImageStatus.DONE)
         modifiedImage.set(imageWithoutBckground.toURL())
         originalImage.set(url)
        //  console.log(response)
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
action="https://api.cloudinary.com/v1_1/djx40lpsg/image/upload/e_background_removal/"


> 

{#if $imageStatus===ImageStatus.READY}
<button class="pointer-events-none bg-blue-600 rounded-full text-bold text-white text-xl px-6 py-4">
Upload Files

</button>

<strong class="text-lg mt-4 text-gray-800">Or drop a file</strong>

{:else if $imageStatus===ImageStatus.UPLOADING}
<strong class="text-lg mt-4 text-gray-800">Uploading files...</strong>
{/if}

</form>
<style>
    @media(min-width:300px){
    .form{
        width: 100%;
      height: 80px;
      grid-template-columns: repeat(1, 50%);
    }
    .strong{
        width: 100%;
        background: block;
        position: relative;
    }
    .button{
        width: 100%;
        position: absolute;
    }
  }
</style>