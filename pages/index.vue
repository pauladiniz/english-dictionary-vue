<template>
  <div class="container flex justify-center align-center">
    <div class="search-app m-12">
      <input placeholder="Search"/>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      word: null
    }
  },
  mounted() {
    axios
      .get('https://owlbot.info/api/v4/dictionary/banana', {
        headers: {
          'Authorization': `token 2183854d54feca89247cf5335e9a0ec3c9a6a684`
        }
      })
      .then(response => (this.word = response.data))
  },
};
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 30vh;
  text-align: center;
}

</style>
