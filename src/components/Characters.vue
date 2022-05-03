<template>
  <div class="characters">
    <div
      v-for="character in charactersList"
      :key="character.id"
      class="character"
    >
      <div class="character-inner">
        <div class="character-front">
          <img :src="character.img" class="character-image" />
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
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  grid-gap: 0.5rem;
}
.character {
  perspective: 1000px;
  background-color: transparent;
  width: 100%;
  height: 250px;
}
.character-inner {
  position: relative;
  width: 100%;
  height: 100%;
  transition: transform 0.8s;
  transform-style: preserve-3d;
}

.character-front,
.character-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden; /* Safari */
  backface-visibility: hidden;
}
.character:hover .character-inner {
  transform: rotateY(180deg);
}
.character-image {
  width: 100%;
  height: 250px;
  object-fit: cover;
}
.character-back {
  background-color: dodgerblue;
  color: white;
  transform: rotateY(180deg);
}
</style>
