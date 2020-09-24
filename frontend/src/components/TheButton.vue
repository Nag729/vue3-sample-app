<template>
  <button class="button is-primary" @click="handleClick">
    {{ buttonCaption }}
  </button>
</template>

<script lang="ts">
import { computed, defineComponent } from "vue";

type Props = {
  caption: string;
};

export default defineComponent({
  name: "TheButton",

  props: {
    caption: {
      type: String,
      default: "CAPTION",
    },
  },

  setup(props, context) {
    // computed
    const buttonCaption = computed(() => props.caption + " Button!");

    // $emit
    const handleClick = () => {
      context.emit("button-click");
    };

    return { buttonCaption, handleClick };
  },
});
</script>

<style scoped lang="scss"></style>
