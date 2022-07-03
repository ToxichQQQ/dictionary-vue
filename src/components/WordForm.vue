<template>
  <form class="word-form" v-on:submit.prevent="getWordInformation">
    <TheHeader msg="Dictionary" />
    <input
      class="input"
      v-model="value"
      type="text"
      placeholder="Type your word here"
    />
    <div>
    <button class="search-button" type="submit">
      <img src="../assets/icons-search.svg" alt="Icon" />
    </button>
    </div>
  </form>
</template>

<script>
import TheHeader from "@/components/TheHeader";

export default {
  name: "WordForm",
  components: {
    TheHeader,
  },
  props: {
    searchValue: String,
  },
  data() {
    return {
      value: this.searchValue,
    };
  },
  methods: {
    getWordInformation() {
      this.$emit("get-word-info");
    },
  },
  watch: {
    value: function (val) {
      this.$emit("change-input-value", val);
    },
  },
};
</script>

<style scoped>
.word-form {
  display: flex;
  flex-direction: column;
  padding-top: 25vh;
  padding-right: 10px;
}
.input {
  margin-bottom: 10px;
  width: 250px;
  padding: 5px;
  border-radius: 10px;
  border: 1px solid grey;
}
.search-button {
  cursor: pointer;
  border-radius: 50%;
  border: 1px solid grey;
}
</style>
