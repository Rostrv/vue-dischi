<template>
<div class="d-flex align-items-center">
  <h4 class="text-white m-0">Seleziona per:</h4>
  <select
    class="form-select-sm mx-3"
    aria-label=".form-select-sm example" @submit.prevent="$emit('clicca')"
    :value="musicGenre"
    @input="$emit('input', $event.target.value)"
    @change="$emit('changeMusicGenre', musicGenre)">
    <option selected>Seleziona un genere</option>
    <option value="">Tutti</option>
    <option value="rock">Rock</option>
    <option value="pop">Pop</option>
    <option value="jazz">Jazz</option>
    <option value="metal">Metal</option>
  </select>
</div>
</template>

<script>
export default {
  name: "SelectFilter",
  props: {
    musicGenre: String
  }
};
</script>

