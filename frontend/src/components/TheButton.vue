<template>
  <div class="control">
    <button class="button is-link" @click="handleClick">
      {{ buttonCaption }}
    </button>
  </div>
</template>

<script lang="ts">
import { computed, defineComponent, PropType } from 'vue';

export default defineComponent({
  name: 'TheButton',

  props: {
    value: {
      type: String as PropType<string>,
      default: 'VALUE'
    }
  },

  setup(props, { emit }) {
    // computed
    const buttonCaption = computed(() => props.value + ' Button!');

    // type
    type HandleClick = () => void;

    // $emit
    const handleClick: HandleClick = () => {
      emit('button-click');
    };

    return { buttonCaption, handleClick };
  }
});
</script>

<style scoped lang="scss"></style>
