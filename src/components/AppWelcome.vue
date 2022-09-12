<template>
  <section>
    <div class="content">
      <h1>Путь к богатству и могуществу</h1>
      <a href="#"
        >О препарате
        <svg
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 24 24"
          stroke-width="1.5"
          stroke="currentColor"
          style="height: 20px"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            d="M8.25 4.5l7.5 7.5-7.5 7.5"
          />
        </svg>
      </a>
    </div>
    <img id="welcome-bg" src="../assets/header.png" alt="NZT 48" />
  </section>
</template>

<script setup></script>

<style lang="scss" scoped>
section {
  position: relative;
  top: 0;
  left: 0;
  display: flex;
  align-items: flex-end;
  max-width: 100vw;
}

#welcome-bg {
  position: relative;
  top: 0;
  left: 0;
  height: 75vh;
  width: 100%;
  object-fit: cover;
}

.content {
  position: absolute;
  width: 50vw;
  padding: 80px 50px;
  font-family: "Nunito Sans", sans-serif;
  color: #e9e9e9;
  z-index: 10;
}

.content h1 {
  font-size: 100px;
  letter-spacing: 5px;
}

.content a {
  color: #e9e9e9;
  font-size: 40px;
  text-decoration: none;
}
</style>
