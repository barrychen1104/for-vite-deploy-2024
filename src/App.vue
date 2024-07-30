<script setup>
import { ref } from 'vue';

const num = ref(2);
function clickMe() {
  num.value++;
}

const htmlTemplate = `<h1>我是HTML標題</h1>`;
const text = ref('Hello, Vite!');
const city = ref('台北市');
const isChecked = ref(true);
const arrayCheckbox = ref([]);
const radioValue = ref('男');

const imgSrc = ref('https://plus.unsplash.com/premium_photo-1721979418255-e8a6abd40358?q=80&w=400&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D');

// v-on
const handleClick = () => {
  'handle click'
  console.log('我被觸發了');
}
const submitForm = () => {
  console.log('表單被觸發了');
}

const text2 = ref('一段文字');

</script>

<template>
  <div>
    {{ htmlTemplate }}
    <div v-text="htmlTemplate"></div>
    <div v-html="htmlTemplate"></div>

    {{ num }}
    <button type="button" v-on:click="clickMe">點我</button>

    <h1>{{ text }}</h1>
    <input type="text" v-model="text" />

    <!-- 表單 -->
    {{ city }}
    <select name="" id="" v-model="city">
      <option value="台北市">台北市</option>
      <option value="台中市">台中市</option>
      <option value="高雄市">高雄市</option>
    </select>

    <!-- checkbox 1. true false, 2. array value -->
    <hr />
    {{ isChecked }}
    <input type="checkbox" v-model="isChecked" />
    <hr />
    {{ arrayCheckbox }}
    <input type="checkbox" value="漂亮阿姨" v-model="arrayCheckbox" />
    <input type="checkbox" value="小明" v-model="arrayCheckbox" />
    <input type="checkbox" value="杰倫" v-model="arrayCheckbox" />

    <!-- radio 單一值 -->
    <hr />
    {{ radioValue }}
    <input type="radio" value="男" v-model="radioValue" />
    <input type="radio" value="女" v-model="radioValue" />

    <hr />
    <div>
      <img :src="imgSrc" alt="">
      <h2>可套用在任何屬性上</h2>
      {{ isChecked }}
      <input type="checkbox" v-model="isChecked">
      <input type="text" :disabled="isChecked">
      <h2>可套用在行內樣式上</h2>
      <div class="box" :style="{ transform: isChecked ? 'rotate(45deg)' : null }"></div>
      <div class="box" :style="{ backgroundColor: isChecked ? 'red' : 'green' }"> </div>

      <h2>class</h2>
      <!-- 需要套用的className, 變數 -->
      <div class="box" :class="{ rotate: isChecked }"></div>

      <br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

      <form action="" @submit.prevent="submitForm">
        <button type="button" v-on:click="handleClick">點我</button>
        <button type="submit">點我</button>
      </form>


      <h2>事件修飾符</h2>
      <a href="#" @click.prevent="handleClick">點我</a>

      <h2>按鍵修飾符</h2>
      <input type="text" @keydown.enter="handleClick" v-model="text2">
    </div>

  </div>
</template>

<style>
.box {
  width: 100px;
  height: 100px;
  background-color: red;
  transition: .5s all;
}

.rotate {
  transform: rotate(45deg);
}
</style>