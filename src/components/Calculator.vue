<template>
  <div id="calculator">

    <div class="bill">
      <p>Bill</p>
      <input class="classInput" type="number" name="" id="inputBill">
    </div>

    <div class="selectTip">
      <p class="textTip">Select Tip %</p>
      <div class="buttons">
        <input class="five" type="button" value="5%">
        <input class="ten" type="button" value="10%">
        <input class="quinze" type="button" value="15%">
        <input class="vinteCinco" type="button" value="25%">
        <input class="cinquenta" type="button" value="50%">
        <input class="custom" type="button" value="Custom">
      </div>
    </div>

    <div class="numberOfPeople">
      <p class="textTip">Number of People</p>
      <input class="classInput" type="number" name="" id="inputPeople">
    </div>

    <div class="result">
      <div class="tipAmount">
        <div>
          <h2>Tip Amount</h2>
          <p>/ person</p>
        </div>
        <div>
          <p>$0.00</p>
        </div>

        <div>
          <h2>Total</h2>
          <p>/ person</p>
        </div>
        <div>
          <p>$00.00</p>
        </div>
      </div>

      <div class="reset">
        <input type="button" value="RESET">
      </div>
    </div>

  </div>
</template>

<script>
export default {
  name: "Calculator",
}
</script>

<style scoped>
  /* Setas Input */
  input[type=number]::-webkit-inner-spin-button,
    input[type=number]::-webkit-outer-spin-button {
      -webkit-appearance: none;
      margin: 0;
    }

  /* Estilização */
  #calculator {
    background: hsl(0, 0%, 100%);
    border-radius: 20px;
    padding: 2rem;
  }

  .classInput {
    background-color: hsl(189, 41%, 97%);
    border: none;
    border-radius: 5px;
    font-size: 24px;
    text-align: right;
    color: hsl(183, 100%, 15%);
    width: 100%;
    padding: 0 0.5rem 0 0.5rem;
    cursor: pointer;
  }

  /* Bill */
  .bill {
    padding-bottom: 1.5rem;
  }

  .bill p {
    color: hsl(183, 100%, 15%);
    padding-bottom: 0.5rem;
  }

  /* Select Tip */
  .selectTip {
    padding-bottom: 1.5rem;
  }

  .textTip {
    color: hsl(186, 14%, 43%);
    padding-bottom: 0.7rem;
  }

  .buttons {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-template-areas: "five ten" 
                         "quinze vinteCinco"
                         "cinquenta custom";

    grid-row-gap: 15px;
    grid-column-gap: 15px;
  }

  .buttons input {
    border: none;
    border-radius: 5px;
    background-color: hsl(183, 100%, 15%);
    color: hsl(189, 41%, 97%);
    font-size: 24px;
    padding: 0.25rem 0 0.25rem 0;
  }

  .buttons input.custom {
    background-color: hsl(189, 41%, 97%);
    color: hsl(186, 14%, 43%);
  }

  /* Number of People */
  .numberOfPeople {
    border: 1px solid red;
    padding: 0.5rem 0 1.5rem 0;
  }

</style>