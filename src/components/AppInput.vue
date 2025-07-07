<template>
  <!-- 宣告 :value 指定這個 modelValue -->
  <!-- 先將 input 內輸入的資料暫存起來 -->
  <!-- @input=...... => 將內容更新給上層 -->
  <input
    type="text"
    :value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
  />
  <!-- $emit 可以在元件內發出事件，而這裡帶入的事件就是 update:modelValue ，
  也就是表示當 modelValue 被更新時，會觸發這個事件，最後再使用 @input 來偵測是否有輸入內容。 -->
</template>

<script>
export default {
  name: "AppInput",
  //要將資料自動傳出，必須要宣告 props
  props: {
    modelValue: String, // modelValue 為系統名稱，不能自由命名
  },
};
</script>
