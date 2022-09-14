<template>
  <div class="buttons">
    <a id="buttons-original" href="#">Проверить оригинальность</a>
    <a id="buttons-buy" href="#">Купить</a>
  </div>
</template>

<script setup></script>

<style lang="scss">
a {
  font-family: "Nunito Sans", sans-serif;
  text-decoration: none;
  transition: ease-in-out 200ms;
}

.buttons {
  display: flex;
  gap: 15px;

  #buttons-original {
    border: 3px solid #df0050;
    border-radius: 999px;
    padding: 10px 20px;
    color: #e9e9e9;
  }

  #buttons-buy {
    border: 3px solid #e9e9e9;
    border-radius: 999px;
    padding: 10px 20px;
    color: #151515;
    background: #e9e9e9;
  }
}
</style>
