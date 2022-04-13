<template>
  <input type="text" v-model="searchField" />

  <button @click="searchImages">Buscar</button>
   <button class="btn btn-primary"></button>

    <!-- Button trigger modal -->
    <button type="button" class="btn btn-primary btn-lg" data-bs-toggle="modal" data-bs-target="#modelId">
      Launch
    </button>
    
    <!-- Modal -->
    <div class="modal fade" id="modelId" tabindex="-1" role="dialog" aria-labelledby="modelTitleId" aria-hidden="true">
        <div class="modal-dialog" role="document">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title">Modal title</h5>
                        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body">
                    Body
                </div>
                <div class="modal-footer">
                    <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
                    <button type="button" class="btn btn-primary">Save</button>
                </div>
            </div>
        </div>
    </div>
    

  <div class="content">

    <div v-for="image in listImages" :key="image.id" >
      <img :src="image.links[0].href" alt="" />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      searchField: "",
      listImages: [],
    };
  },
  methods: {
    searchImages() {
      fetch(
        "https://images-api.nasa.gov/search?media_type=image&q=" +
          this.searchField
      )
        .then((response) => response.json())
        .then((data) => {
          console.log(data);
          this.listImages = data.collection.items;
        });
    },
    searchById() {
      fetch;
    },
  },
};
</script>
     

<style>
.content {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: 1fr;
  gap: 30px 30px;
  width: 80%;
  margin: 0 auto;
  margin-top: 5rem;
  margin-bottom: 4em;
}

input {
  width: 400px;
  height: 20px;
  background-color: rgba(255, 255, 255, 0.795);
}

img {
  width: 350px;
}
</style>