<template>
  <p>Test002-myFunction : {{ myFunction(50) }}</p>
</template>

<script>
export default {
  name: "MyTest002",
  data() {
    return { x: 100, y: 2 };
  },
  methods: {
    myFunction(value) {
      return this.x * this.y + value; //注意在這邊要用 this 來取得定義在 data() 內的變數
    },
  },
};
</script>
