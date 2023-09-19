<script lang="ts">
        import "two-up-element"
 import {originalImage, modifiedImage} from './store'

 let proncessingImage = true
 let tries = 0
 let intervalId: number
 $:{
        if (proncessingImage){
          clearInterval(intervalId)
          intervalId = setInterval(()=>{
            tries++
          }, 500)
        }
 }

</script>

<two-up>
<img src={$originalImage} alt="Imagen original subida por el usuario">
<img 
        on:load={()=> (proncessingImage = false)}
        on:error={()=> (proncessingImage = true)}
        src={`${$modifiedImage}&t=${tries}`} alt="Imagen sin fondo subida por el usuario">
</two-up>

<a download href={$modifiedImage} class=" block bg-blue-500 hover:bg-blue-700 w-full text-xl text-center font-bold text-white rounded-full px-4 py-2 mt-10">
        Descargar imagen sin fondo
</a>