<!-- 元件可以幫助我們將一些共用的畫面來切割並且可以重複使用，讓維護成本降低，
    但是有得時候雖然使用了元件，但還是會需要一些畫面的微調。

    使用 slot 可以讓上層傳入 html 標籤。 -->

<template>
  <div>
    <!-- 使用 slot 可以讓外部 HTML 傳入 -->
    <!-- slot 帶入 name 就可以宣告這一個 slot 的名稱 -->
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: "CardView",
};
</script>
