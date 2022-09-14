<template>
  <section>
    <div class="control-buttons">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        fill="none"
        viewBox="0 0 24 24"
        stroke-width="1.5"
        stroke="currentColor"
        id="beforeButtonGallery"
        @click="beforeGallerySlide('#gallery')"
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
        id="nextButtonGallery"
        @click="nextGallerySlide('#gallery')"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          d="M8.25 4.5l7.5 7.5-7.5 7.5"
        />
      </svg>
    </div>
    <div id="gallery">
      <div class="image">
        <img src="../assets/img-gallery-1.png" alt="Gallery image 1" />
        <div class="card">
          <h3>
            Что это за таблетка?! Я был предельно собран. Я не курил уже 6
            часов, я не ел.
          </h3>
          <p>5 апреля</p>
          <a href="#">
            О NZT-48
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
          </a>
          <div class="card-gradient"></div>
        </div>
      </div>
      <div class="image">
        <img src="../assets/img-gallery-2.png" alt="Gallery image 2" />
        <div class="card">
          <h3>
            Я был таким воздержанным и чистым… Что это? Лекарство для тех, кто
            заботиться о банальной чистоте? Я не был обкурен, я не был пьян, я
            был чистым!
          </h3>
          <p>17 апреля</p>
          <a href="#">
            О побочных
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
          </a>
          <div class="card-gradient"></div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { onMounted, ref } from "vue";

let galleryCounetr = ref(0);

function galleryLogic(propElement) {
  propElement.scrollTo({
    top: 0,
    left: propElement.clientWidth * galleryCounetr.value,
    behavior: "smooth",
  });
}

function nextGallerySlide(elem) {
  --galleryCounetr.value;
  const element = document.querySelector(elem);
  if (galleryCounetr.value < 0) {
    galleryCounetr.value = element.childElementCount - 1;
  }
  galleryLogic(element);
}

function beforeGallerySlide(elem) {
  ++galleryCounetr.value;
  const element = document.querySelector(elem);
  if (galleryCounetr.value + 1 > element.childElementCount) {
    galleryCounetr.value = 0;
  }
  galleryLogic(element);
}

onMounted(() => {
  setInterval(() => {
    nextGallerySlide("#gallery");
  }, 10000);
});
</script>

<style lang="scss" scoped>
section {
  padding: 50px;
  font-family: "Nunito Sans", sans-serif;

  .control-buttons {
    display: flex;
    gap: 20px;
    margin-bottom: 20px;

    #nextButtonGallery,
    #beforeButtonGallery {
      height: 30px;
      stroke: #1e5aaf;
      cursor: pointer;
    }
  }

  #gallery {
    display: flex;
    flex-direction: row;
    width: 100%;
    gap: 50px;
    overflow: hidden;
    border-radius: 10px;
    scroll-snap-type: x mandatory;

    .image {
      display: flex;
      min-width: 100%;
      height: 600px;
      overflow: hidden;
      scroll-snap-align: center;

      img {
        width: 70%;
        object-fit: cover;
        object-position: center;
      }

      .card {
        position: relative;
        width: 30%;
        padding: 50px;
        background: #1e5aaf;
        isolation: isolate;

        h3 {
          font-size: 35px;
          font-weight: 400;
          color: #e9e9e9;
          margin-bottom: 15px;
        }

        p {
          font-size: 20px;
          font-weight: 400;
          color: #8ea9d0;
          margin-bottom: 15px;
        }

        a {
          font-size: 20px;
          font-weight: 600;
          color: #e9e9e9;
          svg {
            height: 15px;
          }
        }

        .card-gradient {
          position: absolute;
          top: 0;
          left: 0;
          height: 100%;
          width: 100%;
          background: linear-gradient(
            0deg,
            transparent 0%,
            rgb(9, 46, 98) 100%
          );
          opacity: 0;
          z-index: -1;
          transition: ease-in-out 200ms;
        }
      }
    }

    .image:hover .card-gradient {
      opacity: 1;
      transition: ease-in-out 200ms;
    }
  }
}
</style>
