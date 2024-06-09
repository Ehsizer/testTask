<template>
  <div class="control">
    <input
        class="vinSearch"
        type="text"
        placeholder="Search VIN"
    >
    <img src="./res/zoom.png" alt="search" @click = "vinSearchFunc">
    <div class = "rightControl">
      <p><strong>Select vehicles per page: </strong></p>
      <select class="LangSlider" v-model = "vehCounter">
       <option v-bind:value="9" @click = "$emit('click', 9)" selected>9</option>
       <option v-bind:value="8" @click = "$emit('click', 8)">8</option>
        <option v-bind:value="7" @click = "$emit('click', 7)">7</option>
        <option v-bind:value="6" @click = "$emit('click', 6)">6</option>
        <option v-bind:value="5" @click = "$emit('click', 5)">5</option>
        <option v-bind:value="4" @click = "$emit('click', 4)">4</option>
     </select>
    </div>
  </div>
  <div class="content">
    <cars-cars
        v-if="carsVin == 0"
        v-for = "car in cars"
        :car = "car"
        :key = "car.id"
    />
    <cars-cars
        v-if="carsVin !== 0 && idForVinSearch !== null"
        :car = "idForVinSearch"
        :key = "idForVinSearch.id"
    />
        <!--v-model = "carsVin" -->
    <span>Showing {{vehCounter}} out of {{totalCars}}</span>
</div>

</template>

<script>

import CarsCars from "@/UI/CarsCars";

export default {
  inheritAttrs: false,
  emits: ["click"],
  components: {CarsCars},
  props:{
    cars:{
      type:Array,
      required:true
    },
    totalCars:0
  },
  data(){
    return{
      carsVin: 0,
      idForVinSearch: 0,
      vehCounter: 9,
    }
  },
  methods:{
    vinSearchFunc(){
      this.carsVin = document.getElementsByTagName("input")[0].value
      if(this.carsVin === ""){
        this.idForVinSearch = null;
      }else {
        for (this.car in this.cars) {
          //console.log("------------" + this.cars[this.car].id);
          if (this.cars[this.car].vin === this.carsVin) {
            this.idForVinSearch = this.cars[this.car]
          }
        }
      }
    },

  },
}

</script>

<style scoped>
.content{
  display: grid;
  grid-template-columns: 33% 33% 33%;
  margin-top: 8vh;
  margin-left: 17vw;
  height: 100vh;
  width: 83vw;
}
.control{
  position: absolute;
  top:13vh;
  left: 17.5vw;
}
.control input{
  width: 15vw;
  height: 42px;
  border-radius: 8px;
}
.control img{
  width: 24px;
  height: 24px;
  position: absolute;
  top:1.3vh;
  left: 13.5vw;
  cursor: pointer;
}
.rightControl{
  text-align: center;
  width: 25vw;
  position: absolute;
  display: flex;
  flex-direction: row;
  top:1.3vh;
  left: 16vw;
}
.rightControl p{
  font-size: 16px;
  padding-right: 15px;
}
.rightControl select{
  width: 85px;
  height: 42px;
  position: absolute;
  left: 12vw;
  top: -1vh;
  background-color: #FFF;
  border: 1px solid rgba(228, 228, 228, 1);
  text-align: center;
}
span{
  margin-top: 10px;
}
</style>