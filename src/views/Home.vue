<template>
  <div>
   <h1>{{ nasaData.title}}</h1>
   <p>{{ nasaData.explanation }}  <strong>-{{nasaData.date}}</strong></p>
   <h3>{{ nasaData.media_type }}</h3>
   <img :src="nasaData.hdurl" alt="">
  </div>
</template>

<script>
// @ is an alias to /src


export default {
  data(){
    return{
        nasaData:{}
    }
  },
  created:function(){
    this.traerdata()
  },
    methods:{
        traerdata(){
          fetch('https://api.nasa.gov/planetary/apod?api_key=8U3P0ih96UhSmZYJKpb97FxRk9F2Gnogd8kLVS4j')
          .then(response => response.json())
          .then((data) =>{
            console.log(data)
            this.nasaData = data;
          })
        }
    }
  }
</script>

<style scoped>
img{
  width: 1200px;
  border-radius: 14px;
}
</style>
