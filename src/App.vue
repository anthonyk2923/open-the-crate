<template>
  <h1 align=center id="phoneError" class="text-primary p-5">Sorry, but this application is unavailble on your device,
    please
    switch to a computer</h1>
  <div id="appz">
    <Reveal :randomNumber="randomNumber" v-show="randomNumber !== 0.000000000129" />
    <Sidebar @submitForm="submitForm" />
    <div id="outer">
      <div id="container" ref="container" class="shadow-lg bg-body-tertiary rounded">
        <Rows v-for="row in Number(rows)" :key="row" :row_length="row_length" @getImageSize="getImageSize"
          @pickNumber="pickNumber" class="rows" :className="className" />
        <Rows />
      </div>
    </div>
  </div>
</template>

<script>
import Rows from "./components/Rows"
import Sidebar from './components/Sidebar'
import Reveal from "./components/Reveal"
import swal from 'sweetalert';
export default {
  name: 'App',
  data() {
    return {
      height: '',
      width: '',
      row_length: 1,
      rows: 1,
      minimum: 0,
      maximum: 100,
      randomNumber: 0.000000000129,
      className: "eight",
    }
  },
  components: {
    Rows,
    Sidebar,
    Reveal,
  },
  methods: {
    getImageSize() {
      const img = document.getElementById('img')
      this.width = img.width
      this.height = img.height
      let screenWidth = this.$refs.container.offsetWidth
      let screenHeight = this.$refs.container.offsetHeight
      this.rows = Math.floor(screenHeight / this.height)
      this.row_length = Math.floor(screenWidth / this.width)
    },
    intToEnglish(number) {

      var NS = [
        { value: 10, str: "ten" },
        { value: 9, str: "nine" },
        { value: 8, str: "eight" },
        { value: 7, str: "seven" },
        { value: 6, str: "six" },
        { value: 5, str: "five" },
        { value: 4, str: "four" },
        { value: 3, str: "three" },
        { value: 2, str: "two" },
        { value: 1, str: "one" }
      ];

      var result = '';
      for (var n of NS) {
        if (number >= n.value) {
          if (number <= 20) {
            result += n.str;
            number -= n.value;
            if (number > 0) result += ' ';
          } else {
            var t = Math.floor(number / n.value);
            var d = number % n.value;
            if (d > 0) {
              return this.intToEnglish(t) + ' ' + n.str + ' ' + this.intToEnglish(d);
            } else {
              return this.intToEnglish(t) + ' ' + n.str;
            }

          }
        }
      }
      this.className = result;
    },
    async submitForm() {
      if (document.getElementById('minimum').value >= document.getElementById('maximum').value) {
        swal('OOPS', 'Make sure the minimum value is less than the maximum value, both values are real numbers and either number starts with zero, default values assumed. ', 'error')
      }
      else {
        this.minimum = document.getElementById('minimum').value
        this.maximum = document.getElementById('maximum').value
        this.className = document.getElementById('size').value
        await this.intToEnglish(this.className)
        await this.getImageSize()
      }
    },
    getRandomIntInclusive(min, max) {
      min = Math.ceil(min);
      max = Math.floor(max);
      return Math.floor(Math.random() * (max - min + 1) + min);
    },
    pickNumber() {
      this.randomNumber = this.getRandomIntInclusive(this.minimum, this.maximum)

    },

  },
  mounted() {
    window.addEventListener("resize", this.getImageSize);
  },
}  
</script>

<style>
#container {
  position: absolute;
  margin: auto;
  height: 100%;
  top: 0;
  bottom: 0;
  text-align: center;
}

#outer {
  padding-left: 20%;
  height: 50%;
  margin: 10%;
}

body {
  background-color: rgb(33, 37, 41)
}

#phoneError {
  display: none;
}

@media (max-width: 978px) {
  #appz {
    display: none;
  }

  body {
    background-color: firebrick;
  }

  #phoneError {
    display: block;
  }

  .swal-button {
    padding: 7px 19px;
    border-radius: 2px;
    background-color: #4962B3;
    font-size: 12px;
    border: 1px solid #3e549a;
    text-shadow: 0px -1px 0px rgba(0, 0, 0, 0.3);
  }
}
</style>
