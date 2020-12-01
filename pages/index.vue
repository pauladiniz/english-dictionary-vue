<template>
<div class="search-app flex items-center justify-center h-screen">
  <div class="search-app w-full max-w-screen-lg p-10">
    <h3 class="text-center">Dictionary 📙</h3>
    <p class="text-center mb-8">Procure por qualquer palavra da língua inglesa e veja o seu significado, pronuncia e definição.</p>
    <input v-if
      class="w-full mb-8"
      placeholder="Search"
      v-model="searchWord"
      @keyup.enter="handleSearch"
    />
    <div class="rounded-xl shadow-md overflow-hidden" v-if="this.word !== null">
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
        :src="definition.image_url"
      />
      <empty-state/>
    </div>
  </div>
</div>
</template>

<script>
import axios from 'axios'
import WordCard from '@/components/word-card.vue'
import DefinitionCard from '@/components/definition-card.vue'

export default {
  components: { WordCard, DefinitionCard },
  data() {
    return {
      word: null,
      definitions: [],
      searchWord: ''
    }
  },
  methods:{
    async handleSearch() {
      await axios
      .get(`https://owlbot.info/api/v4/dictionary/${this.searchWord}`,{
        headers: {
          'Authorization': `token 2183854d54feca89247cf5335e9a0ec3c9a6a684`
        }
      })
      .then(res => (this.word = res.data, this.definitions = res.data.definitions))
      .catch(err => {
        console.log(err.response.data)
      })
    }
  }
}
</script>

<style scoped lang="stylus">
.search-app
  h3
    font-size 2rem
    font-weight bold
    color #e86868
  p
    font-size 0.90rem
    color #575757
input {
  border 1px solid #696969
  border-radius 50px
  padding 1rem
}
</style>
