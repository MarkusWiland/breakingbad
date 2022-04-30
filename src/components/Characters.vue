<template>
  <div class="characters">
    <div
      v-for="character in charactersList"
      :key="character.id"
      class="character"
    >
      <div class="character-inner">
        <div class="character-front">
          <img :src="character.img" class="character_image" />
        </div>
        <div class="character-back">
          <h1>{{ character.name }}</h1>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    charactersList: {
      required: true,
      type: Array,
    },
  },

  name: "CharactersList",
};
</script>

<style scoped>
.characters {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  grid-gap: 0.5rem;
}

.character_image {
  width: 100%;
  height: 250px;
  object-fit: cover;
}
</style>
