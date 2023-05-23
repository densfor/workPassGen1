<script setup>
import { ref, reactive } from 'vue';

const finalArr = reactive([]); //Важно чтобы пушить (работать с массивом) нужно reactive - потому что typeof пишет, что это обьект,а не массив

function alpha() {
  const newAm = [...Array(4)].map(el => (el = Math.round(Math.random() * 9)));

  const testt = [...Array(4)].map(
    el => (el = String.fromCharCode(97 + Math.floor(Math.random() * 26)))
  );

  const finalArr = [...testt, ...newAm].join('');

  return finalArr;
}

function showRes() {
  for (let i = 0; i < 10; i++) {
    finalArr.push(alpha());
  }

  return finalArr;
}
</script>

<template>
  <div v-for="pass in finalArr" :key="pass" class="wrap">
    {{ pass }}
  </div>
  <button class="btn" @click="showRes">Сгенерировать 10 паролей</button>
  <button class="bob" @click="">ну ты боб</button>
</template>

<style scoped>
.bob {
  font-size: 12px;
  font-family: 'Gotham ProRegular', 'Verdana';

  background: url('https://www.youtube.com/watch?v=dQw4w9WgXcQ');

  display: flex;
  justify-content: center;
  margin: 0px auto;
  margin-top: 30px;

  transition: all 0.6s;
}

.bob:hover {
  transform: rotate(30deg);
  background: rgb(2, 0, 36);
  background: linear-gradient(
    90deg,
    rgba(2, 0, 36, 1) 0%,
    rgba(83, 83, 168, 1) 35%,
    rgba(0, 212, 255, 1) 100%
  );
}
.wrap {
  font-family: 'Gotham ProRegular', 'Verdana';
  background-color: beige;

  text-align: center;
  font-size: 19px;
}

.btn {
  display: flex;
  justify-content: center;
  width: 150px;

  margin: 0px auto;
  margin-top: 30px;

  font-size: 16px;
  font-family: 'Gotham ProRegular', 'Verdana';
  font-weight: bold;

  padding: 10px 5px;
  outline: none;
  border: none;
  transition: all 0.5s;
}

.btn:hover {
  background-color: rgb(204, 170, 170);
  cursor: pointer;
  outline: none;
  border: none;
}
</style>
