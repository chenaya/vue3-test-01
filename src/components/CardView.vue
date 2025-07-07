<!-- 元件可以幫助我們將一些共用的畫面來切割並且可以重複使用，讓維護成本降低，
    但是有得時候雖然使用了元件，但還是會需要一些畫面的微調。

    使用 slot 可以讓上層傳入 html 標籤。 -->

<template>
  <div>
    <!-- 使用 slot 可以讓外部 HTML 傳入 -->
    <!-- slot 帶入 name 就可以宣告這一個 slot 的名稱 -->
    <!-- <slot></slot> -->
    <div
      style="
        display: flex;
        /* flex-wrap: wrap; 重點 */
        flex-wrap: wrap;
        justify-content: center;
        gap: 0.75rem;
      "
    >
      <div class="card" style="width: 18rem; border-color: green">
        <img :src="cardImg" class="card-img-top" />
        <div class="card-body">
          <h4 class="card-title">Card title</h4>
          <!-- 放radio button -->
          <a href="#" class="btn btn-primary">Go somewhere</a>
        </div>
      </div>

      <div class="card" style="width: 18rem; border-color: green">
        <img :src="cardImg" class="card-img-top" />
        <div class="card-body">
          <h4 class="card-title">Card title2</h4>
          <!-- 放radio button -->
          <a href="#" class="btn btn-primary">Go somewhere</a>
        </div>
      </div>

      <div class="card" style="width: 18rem; border-color: green">
        <img :src="cardImg" class="card-img-top" />

        <div class="card-body">
          <h4 class="card-title">Card title3</h4>
          <!-- 放radio button -->
          <a href="#" class="btn btn-primary">Go somewhere</a>
        </div>
      </div>

      <div class="card" style="width: 18rem; border-color: green">
        <img :src="cardImg" class="card-img-top" />

        <div class="card-body">
          <h4 class="card-title">Card title4</h4>
          <!-- 放radio button -->
          <a href="#" class="btn btn-primary">Go somewhere</a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import cardImg from "../assets/001.png";
export default {
  name: "CardView",
  setup() {
    return { cardImg };
  },
};
</script>

<style>
.card {
  position: relative;
  display: flex;
  flex-direction: column;
  min-width: 0;
  word-wrap: break-word;
  background-color: #fff;
  background-clip: border-box;
  border: 1px solid rgba(0, 0, 0, 0.125);
  border-radius: 0.25rem;
}

.card-img-top {
  width: 100%; /* 圖片寬度填滿卡片 */
  border-top-left-radius: 0.25rem;
  border-top-right-radius: 0.25rem;
}

.btn {
  display: inline-block;
  font-weight: 400;
  text-align: center;
  padding: 0.375rem 0.75rem;
  font-size: 1rem;
  border-radius: 0.375rem;
  text-decoration: none;
  margin-bottom: 1rem;
}

.btn-primary {
  color: #fff;
  background-color: #0d6efd;
  border-color: #0d6efd;
}
</style>
