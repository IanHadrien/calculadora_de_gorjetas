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
  }

  .title {
    font-size: 24px;
    color: hsl(183, 100%, 15%);
    text-align: center;
    padding-bottom: 1.5rem;
  }

 
</style>
- Strong cyan: hsl(172, 67%, 45%)
- Very dark cyan: hsl(183, 100%, 15%)
- Dark grayish cyan: hsl(186, 14%, 43%)
- Grayish cyan: hsl(184, 14%, 56%)
- Light grayish cyan: hsl(185, 41%, 84%)
- Very light grayish cyan: hsl(189, 41%, 97%)
- White: hsl(0, 0%, 100%)