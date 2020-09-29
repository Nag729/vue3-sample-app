<template>
  <div class="field">
    <label class="label">{{ label }}</label>
    <div class="control">
      <input
        class="input"
        type="text"
        :placeholder="placeholder"
        :value="modelValue"
        @input="handleInput($event.target.value)"
      />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';

export default defineComponent({
  name: 'TheInput',

  props: {
    label: {
      type: String as PropType<string>,
      default: 'label'
    },
    modelValue: String as PropType<string>,
    placeholder: {
      type: String as PropType<string>,
      default: 'Type Here'
    }
  },

  setup(props, { emit }) {
    // type
    type HandleInput = (value: string) => void;

    // $emit
    const handleInput: HandleInput = (value) => {
      emit('update:modelValue', value);
    };

    return { handleInput };
  }
});
</script>

<style scoped lang="scss"></style>
