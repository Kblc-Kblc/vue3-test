<template>
  <div class="container">
    <h1>Тестовые задачи</h1>

    <ul>
      <li>
        1. Сделайте форк репозитория
        <a href="https://gitlab.com/artem.r/vue3-test" target="_blank"
          >с заданиями</a
        >
      </li>
      <li>2. Выполните задание и сделайте коммит в свой форк</li>
      <li>3. Пришлите ссылку на ваш репозиторий</li>
    </ul>

    <h2>Задача 1. Вёрстка</h2>
    <div>
      <div class="logo-container">
        <the-logo :src="logo" v-for="logo in logos" class="the-logo" />
      </div>

      <p>
        Необходимо расположить логотипы компаний сеткой. Сетка должна
        адаптироваться к экрану по следующему правилу:
      </p>
      <ul>
        <li>
          &lt; 600px:
          <a
            target="_blank"
            href="https://img.otcstores.com/644/snimok_ekrana_2023_02_10_v_11_45_52-6444ba26b8.png"
            >2 лого в ряд</a
          >
        </li>
        <li>
          &ge; 600px:
          <a
            target="_blank"
            href="https://img.otcstores.com/1ba/snimok_ekrana_2023_02_10_v_11_45_37-1baec56f4e.png"
            >3 лого в ряд</a
          >
        </li>
        <li>
          &ge; 1024px:
          <a
            target="_blank"
            href="https://img.otcstores.com/ba0/snimok_ekrana_2023_02_10_v_11_45_19-ba0b19265b.png"
            >6 лого в ряд</a
          >
        </li>
      </ul>
    </div>

    <h2>Задача 2. Связь компонентов</h2>
    <div class="bordered-two">
      <the-counter :count="count" @count-incremented="incrementCount" />
      <the-clicker @count-incremented="incrementCount" />
    </div>
    <p>
      Оптимальным образом модифицировать код проекта так, чтобы кнопка в
      компоненте <code>TheClicker</code> тоже увеличивала счётчик компонента
      <code>TheCounter</code>
    </p>

    <h2>Задача 3. Модификация вывода</h2>
    <div class="bordered-two">
      <the-counter :count="count" @count-incremented="incrementCount">
        <template #default="{ count }">
          <p>
            Count:
            <input type="text" :value="count" @input="e => setCount(parseInt(e.target.value))" />
          </p>
        </template>
      </the-counter>
    </div>

    <p>
      Сделать так, чтоб input, переопределяющий вывод информации из компонента
      через слот, заработал (то есть отображал значение счётчика)
    </p>

    <h2>Задача 4. Синхронизация</h2>
    <p>
      Сделать так, чтобы значения всех экземпляров TheCounter на странице
      работали синхронно.
    </p>
  </div>
</template>
<script setup>
import TheClicker from './components/TheClicker.vue'
import TheCounter from './components/TheCounter.vue'
import TheLogo from './components/TheLogo.vue'
import { ref } from 'vue'

const count = ref(0)
const incrementCount = () => {
  count.value++
}

const setCount = (value) => {
  count.value = value
}

const logos = [
  'https://img.otcstores.com/4a3/leaf-4a36b846ec.png',
  'https://img.otcstores.com/bfa/lighting-bfa45a1663.png',
  'https://img.otcstores.com/e93/solaytic-e937233d42.png',
  'https://img.otcstores.com/f7a/aven-f7a55213a9.png',
  'https://img.otcstores.com/8c3/volicity_9-8c3bf4b399.png',
  'https://img.otcstores.com/016/treva-0164a0a05d.png',
  'https://img.otcstores.com/d09/hexa-d0922eddd9.png',
  'https://img.otcstores.com/456/kyan-45643c8de4.png',
  'https://img.otcstores.com/f5f/tvit-f5fcf2b948.png',
  'https://img.otcstores.com/001/towers-001e56f3e9.png',
  'https://img.otcstores.com/616/hex_lab-616d885202.png',
  'https://img.otcstores.com/ac4/fossa-ac4ac5b9ac.png',
]
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
}

ul {
  list-style: none;
  padding: 0;
  text-align: left;
  margin: 0 auto;
  max-width: 600px;
}

/* .logo-container {
  max-width: 600px;
  margin: 0 auto;
  display: flex;
} */

.bordered-two {
  display: flex;
  justify-content: center;
}
.bordered-two > div {
  border: 2px solid #42b983;
  padding: 10px;
  margin: 10px;
}
a {
  color: #42b983;
}

.logo-container {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 10px;
}

@media screen and (min-width: 600px) {
  .logo-container {
    grid-template-columns: repeat(3, 1fr);
  }
}

@media screen and (min-width: 1024px) {
  .logo-container {
    grid-template-columns: repeat(6, 1fr);
  }
}
</style>
