<template>
  <header>
    <div class="top p-2 mb-5 d-flex justify-content-between">
      <div class="img_container">
        <img src="@/assets/spotify-logo.png" alt="" />
      </div>
      <SelectFilter v-model="musicGenre" @changeMusicGenre="search" />
    </div>
  </header>
</template>
<script>
import SelectFilter from "@/components/SelectFilter.vue";
import state from "@/state.js";
export default {
  name: "SiteHeader",
  components: {
    SelectFilter,
  },
  data() {
    return {
      musicGenre: ''
    };
  },
  methods: {
    search() {
      console.log("Searching...");
      state.musicGenre = this.musicGenre;
      console.log(state.musicGenre);
    },
  },
};
</script>
<style lang="scss" scoped>
.top {
  background-color: #2f3a47;
}
img {
  width: 50px;
}
</style>