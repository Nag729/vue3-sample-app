<template>
  <div class="control">
    <button class="button is-primary" @click="handleClick">
      {{ buttonCaption }}
    </button>
  </div>
</template>

<script lang="ts">
import { computed, defineComponent } from 'vue';

type Props = {
  value: string;
};

export default defineComponent({
  name: 'TheButton',

  props: {
    value: {
      type: String,
      default: 'VALUE'
    }
  },

  setup(props, { emit }) {
    // computed
    const buttonCaption = computed(() => props.value + ' Button!');

    // $emit
    const handleClick = () => {
      emit('button-click');
    };

    return { buttonCaption, handleClick };
  }
});
</script>

<style scoped lang="scss"></style>
