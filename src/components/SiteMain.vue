<template>
  <main>
    <section v-if="!loading">
      <div class="container">
        <div class="row justify-content-evenly">
          <div
            class="col-2 mx-1 mb-3"
            v-for="(disco, index) in filtered"
            :key="index"
          >
            <div class="card border-0" style="">
              <img :src="disco.poster" class="card-img-top p-3" />
              <div class="card-body text-center">
                <h4 class="card-title text-white text-uppercase fw-bold fs-5">
                  {{ disco.title }}
                </h4>
                <div class="info text-secondary fs-5">
                  <p class="mb-0">
                    {{ disco.author }}
                  </p>
                  <span>{{ disco.year }}</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
    <div
      class="d-flex min-vh-100 align-items-center justify-content-center"
      v-else
    >
      <h1>Loading...</h1>
    </div>
  </main>
</template>
<script>
import axios from "axios";
import state from "@/state.js";
export default {
  name: "SiteMain",
  data() {
    return {
      API_URL: "http://localhost/php/db.php",
      disco: Object,
      dischi: null,
      loading: true,
      error: null,
    };
  },
  methods: {
    callApi() {
      axios
        .get(this.API_URL)
        .then((response) => {
          this.dischi = response.data;
          this.loading = false;
        })
        .catch((error) => {
          console.log(error);
          this.error = "sorry ${error}";
        });
    },
  },
  computed: {
    filtered() {
      return this.dischi.filter(disco => {
        console.log(disco.genre.toLowerCase());
        console.log(state.musicGenre.toLowerCase());
        return disco.genre.toLowerCase().includes(state.musicGenre.toLowerCase());
      });
    },
    
  },
  mounted() {
      this.callApi();
    }
}
</script>

<style lang="scss" scoped>
.card {
  background-color: #2f3a47;
  height: 100%;
}
</style>
