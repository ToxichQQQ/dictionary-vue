<template>
  <div class="description">
    <h1>{{ word.word }}</h1>
    <h3 v-if="word.phonetic">{{ word.phonetic }}</h3>
    <ol class="list">
      <li
        class="list-item"
        v-for="(item, index) of word.meanings"
        v-bind:key="index"
      >
        <p>Part of speech: {{ item.partOfSpeech }}</p>
        <div
          class="section definition"
          v-for="(def, index) of item.definitions"
          v-bind:key="index"
        >
          <p><span class="subtitle">Definition</span>: {{ def.definition }}</p>
          <p>
            <span class="subtitle" v-if="def.example">Example</span>:{{
              def.example
            }}
          </p>
        </div>
        <div class="section" v-if="item.antonyms.length">
          <span class="subtitle">Antonyms: </span
          ><span v-for="(ant, index) of item.antonyms" v-bind:key="index"
            ><span v-if="index > 0">,</span>{{ ant }}</span
          >
        </div>
        <div class="section" v-if="item.synonyms.length">
          <span class="subtitle">Synonyms: </span
          ><span v-for="(syn, index) of item.synonyms" v-bind:key="index"
            ><span v-if="index > 0">,</span>{{ syn }}</span
          >
        </div>
      </li>
    </ol>
  </div>
</template>

<script>
export default {
  name: "WordDescription",
  props: {
    word: Object,
  },
};
</script>

<style scoped>
.description{
  min-width: 420px;
}
h6 {
  margin: 0;
  display: inline-block;
}
p {
  margin: 0 0 10px;
  display: inline-block;
  font-size: 12px;
}
.subtitle {
  font-size: 12px;
  font-weight: bold;
}
.section {
  font-size: 12px;
  margin-bottom: 10px;
}
.list {
}
.list-item {
  margin-bottom: 10px;
}
.definition {
  border-top: 1px solid grey;
  padding-top: 5px;
}
</style>
