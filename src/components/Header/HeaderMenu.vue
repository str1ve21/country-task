<template>
  <div class="menu">
    <div
      v-for="item in menuItems"
      :key="item.id"
      class="menu-info"
      :id="`menu-item-${item.id}`"
      @click="toggleMenu(item.id)"
    >
      <span>{{ item.text }}</span>
      <svg
        v-if="item.isSvg"
        :class="`item-svg item-svg-${item.id}`"
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
    </div>
    <svg
      xmlns="http://www.w3.org/2000/svg"
      fill="none"
      viewBox="0 0 24 24"
      stroke-width="1.5"
      class="item-svg"
    >
      <path
        stroke-linecap="round"
        stroke-linejoin="round"
        d="M21 21l-5.197-5.197m0 0A7.5 7.5 0 105.196 5.196a7.5 7.5 0 0010.607 10.607z"
      />
    </svg>
    <!-- Не вышло использовать v-for в v-for, поэтому повторение кода -->
    <div class="link-menu link-menu-1" @click="toggleMenu(1)">
      <div class="link-menu-layout">
        <a href="#" v-for="text in linkMenuItems[0]" :key="text">
          {{ text }}
        </a>
      </div>
    </div>
    <div class="link-menu link-menu-2" @click="toggleMenu(2)">
      <div class="link-menu-layout">
        <a href="#" v-for="text in linkMenuItems[1]" :key="text">
          {{ text }}
        </a>
      </div>
    </div>
    <div class="link-menu link-menu-3" @click="toggleMenu(3)">
      <div class="link-menu-layout">
        <a href="#" v-for="text in linkMenuItems[2]" :key="text">
          {{ text }}
        </a>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

function toggleLogic(clickedElement, elementToggle, propElemId) {
  const clickedElementSelector = document.querySelectorAll(
    `.${clickedElement}`
  );
  clickedElementSelector.forEach((nodeItem) => {
    if (nodeItem.classList.contains(`${clickedElement}-${propElemId}`)) {
      document
        .querySelector(`.${clickedElement}-${propElemId}`)
        .classList.toggle(elementToggle);
    } else {
      nodeItem.classList.remove(elementToggle);
    }
  });
}

function toggleMenu(elemId) {
  toggleLogic("link-menu", "link-menu-visible", elemId);
  toggleLogic("item-svg", "item-svg-rotated", elemId);
}

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

const linkMenuItems = [
  [
    "Материалы для изучения",
    "Эффективность и безопасность",
    "Вопрос/Ответ",
    "Мнения специалистов",
    "Информированное согласие",
    "Дистрибьюторы",
    "Обучение",
    "Исследования и публикации",
  ],
  [
    "Эффективность и безопасность",
    "Просто о сложном",
    "Клиники",
    "Мнения специалистов",
    "Вопрос/Ответ",
    "Аптеки",
  ],
  [
    "История",
    "Состав препарата",
    "Инструкция",
    "Механизм действия",
    "Регистрационное удостоверение",
    "Технология производства",
  ],
];
</script>

<style lang="scss">
.menu {
  display: flex;
  gap: 20px;
  justify-content: space-between;
  font-family: "Nunito Sans", sans-serif;
}

.menu-info {
  display: flex;
  gap: 5px;
  font-size: 20px;
  color: #e9e9e9;
  cursor: pointer;
  user-select: none;
  transition: ease-in-out 200ms;
}

.item-svg {
  height: 20px;
  margin: auto 0;
  stroke: #e9e9e9;
  transition: ease-in-out 200ms;
}

.item-svg-rotated {
  transform: rotate(180deg);
}

.link-menu {
  position: fixed;
  top: 100px;
  left: 0;
  height: max-content;
  width: 100%;
  background: #e9e9e9;
  z-index: 100;
  visibility: hidden;
  opacity: 0;
  transition: ease-in-out 200ms;

  .link-menu-layout {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-auto-rows: auto;
    height: 100%;
    padding: 50px;

    a {
      font-size: 20px;
      color: #151515;
      margin: 25px 0;
    }
  }
}

.link-menu-visible {
  visibility: visible;
  opacity: 1;
  transition: ease-in-out 200ms;
}
</style>
