<template>
  <div class="container flex justify-center align-center">
    <div class="search-app m-12">
      <input
        placeholder="Search"
        v-model="searchWord"
        @keyup.enter="handleSearch"
      />
      <div class="search-app--results max-w-md mx-auto bg-white rounded-xl shadow-md overflow-hidden md:max-w-2xl mt-12" v-if="this.word !== null">
        <word-card
          class="p-4"
          :title='word.word'
          :pronunciation='word.pronunciation'
          :definition="word.definition">
        </word-card>
        <definition-card
          v-for="(definition, index) in definitions"
          :key="index"
          class="p-4"
          :definition='definition.definition'
        />
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import WordCard from '@/components/word-card.vue'
import DefinitionCard from '../components/definition-card.vue'

export default {
  components: { DefinitionCard },
  data() {
    return {
      word: null,
      definitions: [],
      searchWord: ''
    }
  },
  methods:{
    handleSearch() { 
      axios
      .get(`https://owlbot.info/api/v4/dictionary/${this.searchWord}`,{
        headers: {
          'Authorization': `token 2183854d54feca89247cf5335e9a0ec3c9a6a684`
        }
      })
      .then(res => (this.word = res.data, this.definitions = res.data.definitions))
    }
  }
}
</script>

<style scoped lang="stylus">
input {
  width 500px
  height 40px
  border 1px solid #696969
  border-radius 50px
  padding 1rem
}
</style>
