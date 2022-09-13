<template>
  <footer>
    <h2>Путь к богатству и могуществу</h2>
    <div class="info">
      <p>© «NZT-48», 2022</p>
      <p>Согласие на обработку персональных данных</p>
      <p>Политика конфиденциальности</p>
      <p>Тестовое задание от Country</p>
    </div>
  </footer>
</template>

<script setup></script>

<style lang="scss" scoped>
footer {
  display: flex;
  flex-direction: column;
  height: 150px;
  padding: 50px;
  background: #051a2c;
  font-family: "Nunito Sans", sans-serif;
  h2 {
    width: 20vw;
    font-size: 30px;
    color: #e9e9e9;
    margin-bottom: auto;
  }
  .info {
    display: flex;
    gap: 50px;
    color: #8c8d98;
    p {
      font-size: 15px;
    }
    :last-child {
      margin-left: auto;
    }
  }
}
</style>
