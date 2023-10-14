<template>
    <div class="container w-100">
        <h1 class="text-center text-uppercase">Imagenes</h1>
        <v-row>
            
            <appImage v-for="img, idx in images" :key="idx" :img="img.download_url" :author="img.author" :url="img.url" :id="img.id" />
        </v-row>
          
    </div>
</template>
<script>
import appImage from '../components/Image.vue'

export default {
    name: "ImagesView",
    components:{
        appImage
    },
    data(){
        return{
            images: []
        }
    },
    created(){
        this.loadImages()
    },
    methods:{
        async loadImages(){
            try{

                const res = await fetch("https://picsum.photos/v2/list?page=2&limit=100")
                const data = await res.json()
                console.log(data)
                this.images = data
            }
            catch (err){
                console.log(err)
            }
        }
    }
    
}
</script>