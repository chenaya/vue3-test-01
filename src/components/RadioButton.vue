<template>
  <div class="radio-buttons">
    <label v-for="option in options" :key="option.value">
      <input
        type="radio"
        :value="option.value"
        :name="name"
        :checked="option.value === value"
        @change="$emit('update:modelValue', option.value)"
      />
      <span>{{ option.label }}</span>
    </label>
  </div>
</template>

<script>
export default {
  name: "RadioButton",
  props: {
    value: {
      type: [String, Number],
      required: true,
    },
    options: {
      type: Array,
      required: true,
    },
    name: {
      type: String,
      default: "radio-button",
    },
  },
};
</script>
