<template>
  <p>Test001</p>
  <button @click="plus">+1</button>
  <p>now count is : {{ count }}</p>
</template>

<script>
export default {
  name: "MyTest001",
  data() {
    return { count: 0 };
  },
  methods: {
    plus() {
      //訪問 data() 中的 count
      return this.count++;
    },
  },
};
</script>
