<template>
  <div class="field">
    <label class="label">{{ label }}</label>
    <div class="control">
      <input class="input" type="text" :placeholder="placeholder" />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

type Props = {
  placeholder: string;
};

export default defineComponent({
  name: 'TheInput',

  props: {
    label: {
      type: String,
      default: 'label'
    },
    value: String,
    placeholder: {
      type: String,
      default: 'Type Here'
    }
  },

  setup(props, { emit }) {
    // $emit
    const handleInput = () => {
      emit('button-click');
    };

    return { handleInput };
  }
});
</script>

<style scoped lang="scss"></style>
