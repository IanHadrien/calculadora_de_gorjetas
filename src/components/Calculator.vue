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
          <input @click="buttonQuinze" class="quinze button" type="button" value="15%">
          <input @click="buttonVinCin" class="vinteCinco button" type="button" value="25%">
          <input @click="buttonCinq" class="cinquenta button" type="button" value="50%">
          <input class="custom button" type="button" value="Custom">
        </div>
      </div>

      <div class="numberOfPeople">
        <p class="textTip">Number of People</p>
        <p id="Erro"></p>
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

      const elementErro = document.querySelector('#Erro');
      const elementPerson = document.querySelector('#inputPeople');

      if(person === '') {
        elementPerson.style.border = '2px solid rgb(228, 72, 72)';
        console.log('erro 1');
      } else if(person == 0) {
        elementErro.innerHTML = 'Cant be zero';
        elementPerson.style.border = '2px solid rgb(228, 72, 72)';
        console.log('erro 2')
      } else {
        elementErro.innerHTML = '';
        elementPerson.style.border = '1px solid hsl(189, 41%, 97%)';
        this.campovalue = value;
        this.campoPerson = person;
      }
    },

    calculateTimAmount(value) {
      let porcTen = (value * this.campovalue) / 100;
      this.tipAmount = porcTen / this.campoPerson;
      this.total = (this.campovalue / this.campoPerson) + this.tipAmount;
    },

    buttonFive() {
      this.campoValue();
      this.removeClass();
      const fiveButton = document.querySelector('.five');
      let fiveButtonValue = document.querySelector('.five').value;
      const valuePorc = Number(fiveButtonValue.slice(0 , -1));
      
      this.calculateTimAmount(valuePorc);

      fiveButton.classList.add('activad');
    },

    buttonTen() {
      this.campoValue();
      this.removeClass();
      const tenButton = document.querySelector('.ten');
      let tenButtonValue = document.querySelector('.ten').value;
      const valuePorc = Number(tenButtonValue.slice(0 , -1));

      this.calculateTimAmount(valuePorc);

      tenButton.classList.add('activad');
    },

    buttonQuinze() {
      this.campoValue();
      this.removeClass();
      const quinzeButton = document.querySelector('.quinze');
      let quinzeButtonValue = document.querySelector('.quinze').value;
      const valuePorc = Number(quinzeButtonValue.slice(0 , -1));

      this.calculateTimAmount(valuePorc);

      quinzeButton.classList.add('activad');
    },

    buttonVinCin() {
      this.campoValue();
      this.removeClass();
      const VinCinButton = document.querySelector('.vinteCinco');
      let VinCinButtonValue = document.querySelector('.vinteCinco').value;
      const valuePorc = Number(VinCinButtonValue.slice(0 , -1));

      this.calculateTimAmount(valuePorc);

      VinCinButton.classList.add('activad');
    },

    buttonCinq() {
      this.campoValue();
      this.removeClass();
      const CinqButton = document.querySelector('.cinquenta');
      let CinqButtonValue = document.querySelector('.cinquenta').value;
      const valuePorc = Number(CinqButtonValue.slice(0 , -1));

      this.calculateTimAmount(valuePorc);

      CinqButton.classList.add('activad');
    },
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

  #Erro {
    color: rgb(228, 72, 72);
    font-size: 15px;
    text-align: right;
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