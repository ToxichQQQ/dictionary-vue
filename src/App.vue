<template>
  <div class="container">
    <WordForm
      v-on:get-word-info="getWordInformation"
      v-on:change-input-value="changeInputValue"
      v-bind:searchValue="searchValue"
    />
    <hr>
    <WordDescription v-bind:word="word" />
  </div>
</template>

<script>
import WordForm from "@/components/WordForm";
import WordDescription from "@/components/WordDescription";

export default {
  name: "App",
  components: {
    WordDescription,
    WordForm,
  },
  data() {
    return {
      searchValue: "",
      word: Object,
    };
  },
  methods: {
    changeInputValue(val) {
      this.searchValue = val;
    },
    getWordInformation() {
      if (this.searchValue) {
        fetch(
          `https://api.dictionaryapi.dev/api/v2/entries/en/${this.searchValue}`
        )
          .then((response) => response.json())
          .then((json) => {
            this.word = json[0];
          });
      } else {
        alert("Please type some word");
      }
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 60px 0;
}
.container {
  width: 700px;
  margin: 0 auto;
  display: flex;
}
</style>
