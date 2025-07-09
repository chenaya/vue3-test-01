<template>
  <div>
    <button
      v-for="option in options"
      :key="option"
      :class="{ selected: selectedOption === option }"
      @click="toggleOption(option)"
    >
      {{ option }}
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      options: ["A", "B", "C"],
      selectedOption: null,
    };
  },
  methods: {
    toggleOption(option) {
      if (this.selectedOption === option) {
        // 如果已選中，再點一次取消選中
        this.selectedOption = null;
      } else {
        this.selectedOption = option;
      }
    },
  },
};
</script>

<style>
button {
  padding: 10px;
  margin: 5px;
}

.selected {
  background-color: #42b983;
  color: white;
}
</style>
