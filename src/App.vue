<!-- template：相關 html 標籤語法放置的地方 -->
<template>
  <button @click="openModal">Modal example</button>
  <Modal :show="showModal" @close="closeModal">
    <div v-for="(c, index) in colorOptions.slice(0, 10)" :key="c.value">
      <p>{{ index }}_{{ c.label }}</p>
    </div>
  </Modal>

  <div><BaseButton /></div>
  <!-- 而要把這個變數 message 顯示在 <template></template> 內的話，
    就必須要使用雙層大括號 {{ message }} -->
  <!-- {{ message }} -->

  <!-- v-show 跟 v-if 會有一樣的效果 -->
  <!-- v-show 與 v-if 的差別在於，v-show 無法像 v-if 一樣可以寫多重的 if 判斷 -->
  <!-- <p v-if="isShow">Hello World</p> -->
  <!-- <p v-shwo="isShow">Hello World</p> -->

  <!-- <p v-for="(str, index) in lists" :key="str">{{ index }}__{{ str }}</p> -->
  <!-- <p v-for="(user, index) in users2" :key="user.email">
    {{ index }}: {{ user.name }} & {{ user.email }}
  </p> -->
  <!-- 
  <div v-for="(str, index) in lists" :key="str">
    <p v-if="str === 'abc'">{{ index }} {{ str }}</p>
  </div> -->

  <!-- <div>
    <p>Question: 你喜歡哪個顏色？</p>
    <RadioButton v-model="selectedAnswer" :options="colorOptions" />
    <p>你選的是：{{ selectedAnswer }}</p>
  </div> -->

  <div>
    <CardView />
  </div>

  <AppHeader :name="name" />
  <input type="text" v-model="name" /><br />
  <p></p>
  <FormView @viewText="getViewText" />
  <!-- 註冊事件並呼叫父元件的方法 -->
  <p>從子元件傳資料給上層: {{ text }}</p>

  <AppInput v-model="inputName" />
  <p>inputName : {{ inputName }}</p>

  <!-- <CardView> -->
  <!-- <h2>Content from CardView</h2> -->
  <!-- 這裡傳入 <h2> 標籤，元件就會顯示這個 <h2> 標籤 -->
  <!-- </CardView> -->

  <button @click="show('tab1')">Test001</button>
  <button @click="show('tab2')">Test002</button>
  <Test001 v-if="tab === 'tab1'" />
  <Test002 v-if="tab === 'tab2'" />
  <!-- 假設Component3有輸入框， -->
  <!-- 當切換這個按鈕去輸入內容到 input 時，然後又切換到另外一個 Component1 或者 Component2，
    當再度切換到 Component3 時，會發現這個 input 的內容會被清空。
所以這邊如果要實現元件不會被清空，就要使用 keep alive 來實現 -->
  <keep-alive>
    <!-- <Component3 v-if="tab === 'tab3'" /> -->
  </keep-alive>

  <!-- 將按鈕按下去時，要去呼叫函式，在 Vue3 呼叫函式的方法會使用 v-on:click 這個方式 -->
  <p></p>
  <input type="text" v-model="formData.name" /><br />
  <!-- v-model.lazy 可以在輸入完畢才會將內容儲存起來，
    換句話說就是將游標跳出，input 輸入框才會將值寫入到變數內 -->
  <p>this is your input : {{ formData.name }}</p>

  <select v-model="formData.selectValue">
    <option value="">select</option>
    <option value="1">1</option>
    <option value="2">2</option>
    <option value="3">3</option>
  </select>
  <p>this is your select : {{ formData.selectValue }}</p>
  <!-- 多選 checkbox、、單選 radio -->
  <input type="checkbox" value="run" v-model="formData.checkbox" /> run
  <input type="checkbox" value="swim" v-model="formData.checkbox" /> swim
  <input type="checkbox" value="hike" v-model="formData.checkbox" /> hike
  <input type="checkbox" value="yoga" v-model="formData.checkbox" /> yoga
  <p>I love : {{ formData.checkbox }}</p>

  <button @click="submit">送出</button>
</template>

<!-- script：程式邏輯放置的地方 -->
<script>
import AppHeader from "./components/AppHeader.vue";
import FormView from "./components/FormView.vue";
import AppInput from "./components/AppInput.vue";
import CardView from "./components/CardView.vue";
import Test001 from "./components/Test001.vue";
import Test002 from "./components/Test002.vue";
// import RadioButton from "./components/RadioButton.vue";
import BaseButton from "./components/BaseButton.vue";
import Modal from "./components/ModalView.vue";

export default {
  //所有程式邏輯都必須要寫在 export default {} 裡頭
  name: "App", //name: 'App' 宣告這個 .vue 的名稱
  components: {
    AppHeader,
    FormView,
    AppInput,
    CardView,
    Test001,
    Test002,
    // RadioButton,
    BaseButton,
    Modal,
  },
  data() {
    //data() {} 是宣告變數的地方，在裡面使用 return 來輸出一個變數message
    //輸出的意思就是將變數輸出給 <template></template> 可以來使用

    //在 Vue3 要使用函式，必須要使用 methods: {} 來宣告函式
    return {
      // message: "HelloWorld",
      // isShow: true,
      // lists: ["123", "abc", "456", "def"],
      //物件陣列
      // users2: [
      //   { name: "Jake", email: "jake@gmail.com" },
      //   { name: "Allan", email: "allan@gmail.com" },
      //   { name: "Eason", email: "eason@gmail.com" },
      // ],

      //name: "", //要讓變數 name 與 input 產生連結，需要使用 v-model 來產生綁定

      //在這邊宣告一個結構變數 formData 來儲存所有的表單欄位變數
      formData: {
        name: "",
        selectValue: "",
        checkbox: [],
      },
      name: "",
      text: "", //宣告一個變數 text 來接收元件傳出來的資料
      inputName: "",
      tab: "",
      selectedAnswer: "",
      colorOptions: [
        { label: "紅色", value: "red" },
        { label: "綠色", value: "green" },
        { label: "藍色", value: "blue" },
        { label: "紅色", value: "red" },
        { label: "綠色", value: "green" },
        { label: "藍色", value: "blue" },
        { label: "紅色", value: "red" },
        { label: "綠色", value: "green" },
        { label: "藍色", value: "blue" },
        { label: "紅色", value: "red" },
        { label: "綠色", value: "green" },
        { label: "藍色", value: "blue" },
      ],
      showModal: false,
    };
  },
  // methods 與 computed 的差別:
  // computed 不管呼叫多少次，都只會執行一次，而 methods 呼叫幾次就會執行幾次
  // 什麼時候會需要用到 computed => computed 可以用在一開始網頁執行時需要的判斷
  // 如果只需要單一次的複雜運算，官方會是建議使用 computed 來執行的
  methods: {
    //函式的寫法必須要使用一個名稱
    //注意在這邊要用 this 來取得定義在 data() 內的變數

    submit() {
      // console.log(this.formData);
      console.log(JSON.parse(JSON.stringify(this.formData)));
    },
    getViewText(text) {
      //函式 getViewText，來接收資料
      this.text = text;
    },
    show(index) {
      // 按鈕按下會呼叫 show 這個函式，然後帶入參數會去更新變數 tab。
      this.tab = index;
    },
    openModal() {
      this.showModal = true;
    },
    closeModal() {
      this.showModal = false;
    },
  },
  watch: {
    count: {
      handler(newValue, oldValue) {
        console.log(newValue, oldValue);
      },
      deep: true, //要監聽物件時，要設定才會起作用
    },
  },
};
</script>

<!-- style：相關 css 標籤語法放置的地方 -->
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
