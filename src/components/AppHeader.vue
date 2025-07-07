<template>
  <h1>This is Header Component</h1>
  <p>From props : {{ name }}</p>
</template>

<script>
export default {
  name: "AppHeader",
  props: {
    // name: String, //定義型別
    //default 屬性應該是一個函數或類型的構造函數，而不是單純的字串。
    //在定義 props 時，default 應該是一個函數，返回預設值，或是直接設定預設值。
    //這樣 Vue 在沒有傳遞該 prop 時會使用這個預設值。
    // default: "...",
    name: {
      type: String, // 定義型別
      default: "...", // 如果沒有傳入 name，使用預設值 => 有傳入空字串 所以無顯示
    },
  },
};
</script>
