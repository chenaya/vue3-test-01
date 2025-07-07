# vue-demo

## Project setup

```
npm install
```

### Compiles and hot-reloads for development

```
npm run serve
```

### Compiles and minifies for production

```
npm run build
```

### Lints and fixes files

```
npm run lint
```

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).

# 使用生命週期的好處

就是可以分門別類要處理的邏輯，例如如果有呼叫 Server API 的話，通常會放在 created() {} 來呼叫。

或者有 UI 的相關邏輯處理，會放在 mounted() {} 。

### Composition API

# 宣告變數

使用 Composition 宣告變數要用 ref 來初始化，而這個 ref 必須要先 import 才可以使用。

所以一開始 import { ref } from 'vue'; 引用 ref 來使用。

使用 setup() {} 把變數放在此內部。

使用 const name = ref(''); 來進行變數的宣告，並且用 ref 來初始化這個變數為空白。

如果要修改這個變數的話，要使用 .value

<template>
  {{ name }}
</template>

<script>
import { ref } from 'vue';

export default {
  name: 'App',
  setup() {
    const name = ref('');
    
    //設定值要使用 value
    name.value = 'Jake';
    
    return {
      name,
    };
  },
};
</script>

# 宣告結構變數

如果要宣告結構變數的話就必須要使用 reactive ，然後將變數放在裡面，

而初始化的時候就不用 ref 了。而這個 reactive 也必須要 import 才可以使用。

reactive 設定值就不需要使用 value 了。

<template>
  {{ user.id }} {{ user.name }}
</template>

<script>
import { reactive } from 'vue';

export default {
  name: 'App',
  setup() {
    const user = reactive({
      id: 0,
      name: '',
    });

    user.id = 1;
    user.name = 'Allan';

    return {
      user,
    };
  },
};
</script>

card: https://bootstrap5.hexschool.com/docs/5.0/components/card/
