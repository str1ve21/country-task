<template>
  <div class="menu">
    <span class="menu-info" v-for="item in menuItems" :key="item.id">
      {{ item.text }}
      <svg
        v-if="item.isSvg"
        xmlns="http://www.w3.org/2000/svg"
        fill="none"
        viewBox="0 0 24 24"
        stroke-width="1.5"
        stroke="currentColor"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          d="M19.5 8.25l-7.5 7.5-7.5-7.5"
        />
      </svg>
    </span>
    <svg
      xmlns="http://www.w3.org/2000/svg"
      fill="none"
      viewBox="0 0 24 24"
      stroke-width="1.5"
    >
      <path
        stroke-linecap="round"
        stroke-linejoin="round"
        d="M21 21l-5.197-5.197m0 0A7.5 7.5 0 105.196 5.196a7.5 7.5 0 0010.607 10.607z"
      />
    </svg>
  </div>
</template>

<script setup>
import { ref } from "vue";

const menuItems = ref([
  {
    id: 1,
    text: "Врачу",
    isSvg: true,
  },
  {
    id: 2,
    text: "Пациенту",
    isSvg: true,
  },
  {
    id: 3,
    text: "О препарате",
    isSvg: true,
  },
  {
    id: 4,
    text: "Журнал",
    isSvg: false,
  },
  {
    id: 5,
    text: "Контакты",
    isSvg: false,
  },
]);
</script>

<style lang="scss">
.menu {
  display: flex;
  gap: 20px;
  justify-content: space-between;
}

.menu-info {
  display: flex;
  gap: 5px;
  font-family: "Nunito Sans", sans-serif;
  font-size: 20px;
  color: #e9e9e9;
  cursor: pointer;
  transition: ease-in-out 200ms;
}

.menu svg {
  height: 20px;
  margin: auto 0;
  stroke: #e9e9e9;
  transition: ease-in-out 200ms;
}
</style>
