<template>
  <div class="home">
    <h1>Breaking Bad</h1>
    <input v-model="inputSearchText" />
    <Characters :charactersList="filteredByName" />
  </div>
</template>

<script>
// @ is an alias to /src
import axios from "axios";
import Characters from "../components/Characters.vue";
export default {
  name: "HomeView",
  data() {
    return {
      inputSearchText: "",
      charactersList: [],
    };
  },
  components: {
    Characters,
  },
  computed: {
    filteredByName() {
      return this.charactersList.filter((char) => {
        return char.name
          .toLowerCase()
          .includes(this.inputSearchText.toLowerCase());
      });
    },
  },
  async created() {
    try {
      const response = await axios(
        "https://www.breakingbadapi.com/api/characters"
      );
      this.charactersList = response.data;
      console.log(response.data);
    } catch (e) {
      console.error(e);
    }
  },
};
</script>
<style scoped>
.home {
  max-width: 1000px;
  width: 100%;
}
</style>
