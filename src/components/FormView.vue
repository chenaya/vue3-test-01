<template>
  <div>
    <input type="text" v-model="text" />
    <!-- 在表單的按鈕呼叫這個 emits 內的變數，並且把資料傳入 -->
    <button @click="$emit('viewText', text)">Send</button>
  </div>
</template>

<script>
export default {
  name: "FromView",
  // 要從元件內傳資料給上層，要先宣告 emits
  // 宣告一個 emits ，給予一個陣列，裡面有一個變數 viewText
  emits: ["viewText"],
  data() {
    return {
      text: "",
    };
  },
};
</script>
