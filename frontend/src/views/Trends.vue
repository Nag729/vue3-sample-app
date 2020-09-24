<template>
  <div class="about">
    <figure class="image logo-image">
      <img src="@/assets/google-trends.png" />
    </figure>
    <TheButton :caption="state.caption" @button-click="handleClick"></TheButton>
  </div>
</template>

<script lang="ts">
import { defineComponent, onMounted, reactive } from 'vue';
import TheButton from '@/components/TheButton.vue';
const gta = require('google-trends-api');

export default defineComponent({
  name: 'About',

  components: {
    TheButton
  },

  setup() {
    // reactive data
    const state = reactive<{ caption: string }>({
      caption: 'ABOUT'
    });

    // emitted event
    const handleClick = () => {
      alert('Button Clicked !');
    };

    const today = new Date();

    const obj = {
      keyword: 'Jリーグ',
      startTime: today.setDate(today.getDate() - 10),
      endTime: today,
      geo: 'JP',
      hl: 'ja'
    };

    onMounted(() => {
      gta
        .relatedQueries(obj)
        .then((results: any) => {
          const json = JSON.parse(results);
          console.log(json);
        })
        .catch((err: any) => {
          console.error(err);
        });
    });

    return { state, handleClick };
  }
});
</script>

<style lang="scss" scoped>
.logo-image {
  margin: 0 auto;
  max-width: 15%;
  padding: 2vh 0;
}
</style>
