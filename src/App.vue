<template class="app-template">
  <header class="top-menu">
    <nav>
      <menu>
        <li v-for="(name, idx) in menuHeaders" :key="idx">
          <a href="">{{ name }}</a>
        </li>
      </menu>
    </nav>
    <div class="menu-buttons">
      <ol>
        <li><img src="./img/sun.png" alt="" /></li>
        <li><button>Войти</button></li>
      </ol>
    </div>
  </header>
  <section class="main-carousel">
    <div class="carousel-info">
      <h1>Проблемы в университете?</h1>
      <p>
        Подай заявку в систему LIFT, обрати внимание администрации ВУЗа на
        сложившуюся ситуацию и помоги измененить среду вокруг.
      </p>
      <button>Подать заявку</button>
    </div>
    <img src="./img/phones_dark.png" alt="" />
  </section>
  <section class="stats">
    <div class="stat-card" v-for="(stat, idx) in statsInfo" :key="idx">
      <div class="number">{{ stat.number }}</div>
      <div class="header">{{ stat.title }}</div>
    </div>
  </section>
  <section class="already-done">
    <img src="./img/left_arrow.png" alt="" />
    <img
      v-for="(imgPath, idx) in lowCarousel"
      :key="idx"
      :src="itemImage(imgPath)"
      class="rectangle"
    />
    <img @click="spin()" src="./img/rigth_arrow.png" alt="" />
  </section>
  <section class="how-it-works">
    <h1>How it works?</h1>
    <div>
      <div v-for="(step) in workingSteps" :key="step.num">
        <div class="image-number">
          <div class="number">{{ step.num }}</div>
          <img :src="itemImage(step.img)" alt="" />
        </div>
        <p>{{ step.text }}</p>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "App",

  data() {
    return {
      menuHeaders: [
        "LIFT",
        "Подать заявку",
        "Как это работает",
        "Новости",
        "Статистика",
      ],

      statsInfo: [
        {
          number: 255,
          title: "Актуальных заявок",
        },
        {
          number: 569,
          title: "Пользователей сервиса",
        },
        {
          number: 155,
          title: "Изменений благодаря LIFT",
        },
        {
          number: 56,
          title: "Активных операторов",
        },
      ],

      lowCarousel: [
        "./img/101Artboard_7-100_1.png",
        "./img/101Artboard_7-100_1.png",
        "./img/101Artboard_7-100_1.png",
      ],

      workingSteps: [
        {
          num: 1,
          text: "Подача заявки в сервис LIFT через любую доступную платформу",
          img: "./img/101Artboard_7-100_1.png",
        },
        {
          num: 2,
          text: "Обработка заявки оператором и измение статуса заявки",
          img: "./img/101Artboard_7-100_1.png",
        },
        {
          num: 3,
          text: "Передача заявки в уполномоченные инстанци и исправление ситуации",
          img: "./img/101Artboard_7-100_1.png",
        },
      ],
    };
  },

  methods: {
    itemImage(path) {
      return require(`${path}`);
    },

    spin() {
      console.log("spin");

      for (let item of this.workingSteps) {
        item.num++;
      }
    }
  },
};
</script>

<style src="./styles.css"></style>
