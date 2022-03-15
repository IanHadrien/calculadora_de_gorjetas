<template>
  <div id="container">

    <div class="title">
      <h2>
        SPLI <br>
        TTER
      </h2>
    </div>

    <Calculator />

  </div>
</template>

<script>
import Calculator from "./Calculator.vue";

export default {
  name: 'HelloWorld',
  components: {
    Calculator
  }
}
</script>

<style scoped>
  #container {
    background: hsl(185, 41%, 84%);
    padding: 2rem 0 2rem 0;
    height: 100vh;
  }

  .title {
    font-size: 24px;
    color: hsl(183, 100%, 15%);
    text-align: center;
    padding-bottom: 1.5rem;
  }
</style>