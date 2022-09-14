<template>
  <section>
    <div class="link-item" v-for="item in navLinksArray" :key="item.id">
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
    </div>
  </section>
</template>

<script setup>
const navLinksArray = [
  {
    id: 1,
    text: "История",
  },
  {
    id: 2,
    text: "Технология производства",
  },
  {
    id: 3,
    text: "Инструкция",
  },
  {
    id: 4,
    text: "Состав препарата",
  },
  {
    id: 5,
    text: "Механизм действия",
  },
  {
    id: 6,
    text: "Рег. удостоверение",
  },
];
</script>

<style lang="scss" scoped>
section {
  display: grid;
  grid-template-columns: repeat(3, minmax(max-content, 1fr));
  gap: 25px;
  padding: 50px;
  font-family: "Nunito Sans", sans-serif;

  .link-item {
    display: flex;
    align-items: center;
    justify-content: space-between;
    border-top: 2px solid #b9b9b9;
    padding: 25px 0;
    font-size: 25px;
    cursor: pointer;

    svg {
      height: 15px;
      stroke: #1e5aaf;
    }
  }
}
</style>
