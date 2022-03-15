<template>
  <div id="calculator">
    <div>
      <div class="bill">
        <p>Bill</p>
        <input class="classInput" type="number" name="" id="inputBill">
      </div>

      <div class="selectTip">
        <p class="textTip">Select Tip %</p>
        <div class="buttons">
          <input @click="buttonFive" class="five button" type="button" value="5%">
          <input @click="buttonTen" class="ten button" type="button" value="10%">
          <input class="quinze button" type="button" value="15%">
          <input class="vinteCinco button" type="button" value="25%">
          <input class="cinquenta button" type="button" value="50%">
          <input class="custom button" type="button" value="Custom">
        </div>
      </div>

      <div class="numberOfPeople">
        <p class="textTip">Number of People</p>
        <input class="classInput" type="number" name="" id="inputPeople">
      </div>
    </div>

    <div>
      <div class="result">
        <div class="tipAmount">
          <div class="tipPerson">
            <div>
              <h2>Tip Amount</h2>
              <p>/ person</p>
            </div>
            <div class="value">
              <p>${{ tipAmount.toFixed(2) }}</p>
            </div>
          </div>

          <div class="tipPerson">
            <div>
              <h2>Total</h2>
              <p>/ person</p>
            </div>
            <div class="value">
              <p>${{ total.toFixed(2) }}</p>
            </div>
          </div>
        </div>

        <div class="reset">
          <input type="button" value="RESET">
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Calculator",

  data() {
    return {
      campovalue: 0,
      campoPerson: 0,
      tipAmount: 0.00,
      total: 0.00,
    }
  },

  methods: {
    // Porcentagem do total 15% de 142,55 = 21,38
    // 21,38 / 5 = 4,27
    // (142,55 / 5 ) + 4,27 = 32,78

    removeClass() {
      const buttonsInput = document.querySelectorAll('input.button');

      for (let index = 0; index < buttonsInput.length; index++) {
        if (buttonsInput[index].classList.contains('activad')) {
          buttonsInput[index].classList.remove('activad')
        }
      }
    },

    campoValue() {
      const value = document.querySelector('#inputBill').value;
      const person = document.querySelector('#inputPeople').value;

      this.campovalue = value;
      this.campoPerson = person;
    },

    buttonFive() {
      this.campoValue();
      this.removeClass();
      const fiveButton = document.querySelector('.five');

      let porcFive = (5 * this.campovalue) / 100;
      this.tipAmount = porcFive / this.campoPerson;
      this.total = (this.campovalue / this.campoPerson) + this.tipAmount;
      console.log(this.total);

      fiveButton.classList.add('activad');
    },

    buttonTen() {
      this.campoValue();
      this.removeClass();
      const tenButton = document.querySelector('.ten');
      let tenButtonValue = document.querySelector('.ten').value;
      console.log(Number(tenButtonValue.slice(0 , -1)));

      let porcTen = (10 * this.campovalue) / 100;
      this.tipAmount = porcTen / this.campoPerson;
      this.total = (this.campovalue / this.campoPerson) + this.tipAmount;
      //console.log(this.total);

      tenButton.classList.add('activad');
    }
  },

  mounted() {
  },
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
    border: 1px solid hsl(189, 41%, 97%);
    border-radius: 5px;
    font-size: 24px;
    text-align: right;
    color: hsl(183, 100%, 15%);
    width: 100%;
    padding: 0 0.5rem 0 0.5rem;
    cursor: pointer;
  }

  .buttons input.activad {
    background: hsl(172, 67%, 45%);
    color: hsl(183, 100%, 15%);
  }

  /* Bill */
  .bill {
    padding-bottom: 1.5rem;
  }

  .bill p {
    color: hsl(183, 100%, 15%);
    padding-bottom: 0.5rem;
  }

  .bill input:host {
    border: 1px solid red;
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
    cursor: pointer;
  }

  .buttons input.custom {
    background-color: hsl(189, 41%, 97%);
    color: hsl(186, 14%, 43%);
  }

  /* Number of People */
  .numberOfPeople {
    padding: 0.5rem 0 1.5rem 0;
  }

  /* Result */
  .result {
    background-color: hsl(183, 100%, 15%);
    border-radius: 20px;
    padding: 2rem 1.5rem;
  }

  .tipPerson {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding-bottom: 1.5rem;
  }

  .tipPerson div h2 {
    color: hsl(0, 0%, 100%);
  }

  .tipPerson div p {
    color: hsl(186, 14%, 43%);
  }

  .tipPerson .value p {
    font-size: 26px;
    color: hsl(172, 67%, 45%);
  }

  .reset input {
    background: hsl(172, 67%, 45%);
    color: hsl(183, 100%, 15%);
    border: none;
    border-radius: 5px;
    font-size: 24px;
    width: 100%;
    padding: 0.5rem 0 0.5rem 0;
  }

  /* Responsividade */
  @media (min-width: 550px) {
    .buttons {
      grid-template-columns: 1fr 1fr 1fr;
      grid-template-areas: "five ten quinze" 
                           "vinteCinco cinquenta custom";
    }
  }

  @media (min-width: 800px) {
    #calculator {
      width: 800px;
      margin: auto;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }

    .result {
      width: 400px;
    }
  }
</style>