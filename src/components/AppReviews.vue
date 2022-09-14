<template>
  <section>
    <h2>
      Мы изучаем и принимаем во внимание все мнения ведущих специалистов отрасли
    </h2>
    <div class="control-buttons">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        fill="none"
        viewBox="0 0 24 24"
        stroke-width="1.5"
        stroke="currentColor"
        id="beforeButtonReviews"
        @click="beforeGallerySlide('#slider')"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          d="M15.75 19.5L8.25 12l7.5-7.5"
        />
      </svg>
      <svg
        xmlns="http://www.w3.org/2000/svg"
        fill="none"
        viewBox="0 0 24 24"
        stroke-width="1.5"
        stroke="currentColor"
        id="nextButtonReviews"
        @click="nextGallerySlide('#slider')"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          d="M8.25 4.5l7.5 7.5-7.5 7.5"
        />
      </svg>
      <a href="#">Мнения специалистов</a>
    </div>
    <div id="slider">
      <div class="review-card" id="item-0">
        <img src="../assets/avatar.png" alt="Person avatar" />
        <h3>Эдди морро</h3>
        <p class="about-person">
          Сенатор, заслуженный деятель науки РФ, профессор, доктор медицинских
          наук, руководитель отдела патоморфологии ФГБНУ «НИИАГиР им. Д.О.
          Отта», г.Санкт-Петербург
        </p>
        <p class="card-text">
          Правовое государство фактически интегрирует культ личности. Социализм,
          на первый взгляд, заставляет бесцветный культ личности.
        </p>
        <a href="#">
          Смотреть видео
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
        </a>
      </div>
      <div class="review-card" id="item-1">
        <img src="../assets/avatar.png" alt="Person avatar" />
        <h3>Эдди морро</h3>
        <p class="about-person">
          Сенатор, заслуженный деятель науки РФ, профессор, доктор медицинских
          наук, руководитель отдела патоморфологии ФГБНУ «НИИАГиР им. Д.О.
          Отта», г.Санкт-Петербург
        </p>
        <p class="card-text">
          Правовое государство фактически интегрирует культ личности. Социализм,
          на первый взгляд, заставляет бесцветный культ личности.
        </p>
        <a href="#">
          Смотреть видео
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
        </a>
      </div>
    </div>
  </section>
</template>

<script setup>
import { onMounted, ref } from "vue";
let reviewsCounter = ref(0);
function sliderLogic(propElement) {
  propElement.childNodes.forEach((child) => {
    if (child === propElement.children[`item-${reviewsCounter.value}`]) {
      child.style.background = "#1e5aaf";
    } else {
      child.style.background = "#0f3974";
    }
  });
  propElement.scrollTo({
    top: 0,
    left: propElement.clientWidth * reviewsCounter.value,
    behavior: "smooth",
  });
}
function nextGallerySlide(elem) {
  --reviewsCounter.value;
  const element = document.querySelector(elem);
  if (reviewsCounter.value < 0) {
    reviewsCounter.value = element.childElementCount - 1;
  }
  sliderLogic(element);
}
function beforeGallerySlide(elem) {
  ++reviewsCounter.value;
  const element = document.querySelector(elem);
  if (reviewsCounter.value + 1 > element.childElementCount) {
    reviewsCounter.value = 0;
  }
  sliderLogic(element);
}
onMounted(() => {
  document.querySelector("#slider").children[
    `item-${reviewsCounter.value}`
  ].style.background = "#1e5aaf";
  setInterval(() => {
    nextGallerySlide("#slider");
  }, 7500);
});
</script>

<style lang="scss" scoped>
section {
  padding: 50px;
  margin-bottom: 50px;
  font-family: "Nunito Sans", sans-serif;

  h2 {
    width: 60vw;
    font-size: 50px;
    color: #252627;
    margin-bottom: 25px;
  }

  .control-buttons {
    display: flex;
    align-items: center;
    gap: 20px;
    margin-bottom: 20px;

    #nextButtonReviews,
    #beforeButtonReviews {
      height: 30px;
      stroke: #1e5aaf;
      cursor: pointer;
    }

    a {
      margin-left: auto;
      color: #1e5aaf;
    }
  }

  #slider {
    display: flex;
    flex-direction: row;
    width: 100%;
    gap: 50px;
    overflow: hidden;
    border-radius: 10px;
    scroll-snap-type: x mandatory;
  }

  .review-card {
    position: relative;
    display: flex;
    flex-direction: column;
    height: 600px;
    min-width: 50vw;
    padding: 50px 100px;
    background: #0f3974;
    border-radius: 10px;
    overflow: hidden;
    isolation: isolate;
    scroll-snap-align: start;
    transition: ease-in-out 200ms;

    img {
      position: absolute;
      top: 50px;
      right: 100px;
      height: 150px;
      object-fit: cover;
    }

    h3 {
      width: min-content;
      margin-bottom: 15px;
      text-transform: uppercase;
      font-size: 30px;
      color: #e9e9e9;
    }

    .about-person {
      width: 70%;
      font-size: 20px;
      color: #557eb8;
      margin-bottom: 50px;
    }

    .card-text {
      width: 80%;
      font-size: 35px;
      color: #e9e9e9;
      margin-bottom: auto;
    }

    a {
      display: flex;
      align-items: center;
      justify-content: space-between;
      font-size: 20px;
      color: #e9e9e9;

      svg {
        height: 20px;
      }
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

  .review-card:hover .card-gradient {
    opacity: 1;
    transition: ease-in-out 200ms;
  }
}
</style>
