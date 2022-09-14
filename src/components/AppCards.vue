<template>
  <section>
    <div class="card" v-for="item in cardsArray" :key="item.id">
      <h3>{{ item.title }}</h3>
      <p>{{ item.text }}</p>
      <svg
        xmlns="http://www.w3.org/2000/svg"
        fill="none"
        viewBox="0 0 24 24"
        stroke-width="1.5"
        stroke="currentColor"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          d="M8.25 4.5l7.5 7.5-7.5 7.5"
        />
      </svg>
      <div class="card-gradient"></div>
    </div>
  </section>
</template>

<script setup>
const cardsArray = [
  {
    id: 1,
    title: "Эффективность",
    text: "Доказана многочисленными клиническими и лабораторными исследованиями",
  },
  {
    id: 2,
    title: "Безопасность",
    text: "Не содержит гормонов, ферментов, витаминов и других биогенных стимуляторов",
  },
  {
    id: 3,
    title: "Высокие технологии",
    text: "При производстве используются самые передовые технологии отбора, хранения и очистки",
  },
  {
    id: 4,
    title: "Уникальный состав",
    text: "Сбалансированный состав биомолекул, так как соотношение компонентов создано природой, характерно для здоровой ткани и не просто стопроцентно усваивается, а встраивается в собственный метаболизм пациента",
  },
];
</script>

<style lang="scss" scoped>
section {
  display: flex;
  gap: 2.5vw;
  padding: 50px;
  margin-bottom: 50px;
  font-family: "Nunito Sans", sans-serif;

  .card {
    position: relative;
    min-height: 400px;
    width: 20vw;
    padding: 25px 25px 125px 25px;
    background: #1e5aaf;
    border-radius: 10px;
    box-shadow: 0px 0px 10px rgba(6, 31, 67, 0.3);
    overflow: hidden;
    isolation: isolate;
    cursor: pointer;

    h3 {
      font-size: 35px;
      color: #e9e9e9;
      word-break: break-all;
      margin-bottom: 15px;
    }

    p {
      font-size: 20px;
      color: #c0c0c0;
    }

    svg {
      position: absolute;
      height: 30px;
      right: 50px;
      bottom: 50px;
      color: #e9e9e9;
    }
  }

  .card:hover .card-gradient {
    opacity: 1;
    transition: ease-in-out 200ms;
  }

  .card-gradient {
    position: absolute;
    top: 0;
    left: 0;
    height: 100%;
    width: 100%;
    background: linear-gradient(0deg, transparent 0%, rgb(9, 46, 98) 100%);
    opacity: 0;
    z-index: -1;
    transition: ease-in-out 200ms;
  }
}
</style>
