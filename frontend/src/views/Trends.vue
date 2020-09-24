<template>
  <div class="trends">
    <figure class="card image logo-image">
      <img src="@/assets/qiita.png" />
    </figure>
    <div class="search-form">
      <div class="field">
        <TheInput v-model="state.keywords" label="Keywords"></TheInput>
      </div>
      <div class="field search-button">
        <TheButton value="Search" @button-click="handleClick"></TheButton>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
/* eslint-disable @typescript-eslint/camelcase */
import axios from 'axios';
import { defineComponent, onMounted, reactive } from 'vue';
import TheButton from '@/components/TheButton.vue';
import TheInput from '@/components/TheInput.vue';

export default defineComponent({
  name: 'About',

  components: {
    TheButton,
    TheInput
  },

  setup() {
    // reactive data
    const state = reactive<{ keywords: string; info: object }>({
      keywords: '',
      info: {}
    });

    // emitted event
    const handleClick = () => {
      alert('Button Clicked !');
    };

    // mounted
    onMounted(() => {
      axios
        .get('https://qiita.com/api/v2/items', {
          params: {
            page: 1,
            per_page: 20,
            query: 'Vue.js'
          }
        })
        .then(response => {
          state.info = response;
          console.log(response);
        });
    });

    return { state, handleClick };
  }
});
</script>

<style lang="scss" scoped>
.card {
  overflow: hidden;
  border-radius: 8px;
  border-left: solid 1px #ddd;
  border-right: solid 1px #ddd;
  border-bottom: solid 5px #888;
}

.logo-image {
  margin: 2vh auto;
  max-width: 20%;
}

.search-form {
  margin: 2vh auto;
  width: 40%;
}

.search-button {
  text-align: right;
}
</style>
