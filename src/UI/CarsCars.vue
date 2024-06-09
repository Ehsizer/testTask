<template>
  <div class="CarCard">
    <img :src="car.placeholder">
    <div class="CarPlacegolder">
      <p><strong>{{car.vehicle_name}}</strong></p>
      <p>{{car.vin}}</p>
    </div>
    <div class="CarInfo">
      <p class = "CarCount Green" v-if="car.angles_count.value === 30"> {{car.angles_count}}/30</p>
      <p class="CarCount default" v-else>{{car.angles_count}}/30</p>
      <p>3 days left</p>
    </div>
  </div>
</template>

<script>
export default {
  props:{
    car:{
      type: Object,
      required: true
    },
  },
  methods:{

    },

  mounted(){

  }
  }
</script>

<style scoped>
.CarCard{
  margin: 10px;
  height: 38vh;
  width: 25vw;
  background-color: rgba(243, 246, 248, 1);
  text-align: center;

}
.Green{
  background-color: rgba(228, 245, 221, 1);
}
.CarCard img{
  height: 25vh;
  width: 15vw;
  object-fit: cover; /* Вписываем фотографию в область */
  image-rendering: -moz-crisp-edges; /* Firefox */
  -ms-interpolation-mode: nearest-neighbor;  /* IE */
  image-rendering: crisp-edges; /* Стандартное свойство */
}
.CarPlacegolder{
  text-align: left;
  font-size: 20px;
  margin-top: 15px;
  width: 90%;
  border-bottom: rgba(228, 228, 228, 1) solid 1px;
  padding-left: 25px ;
}
.CarInfo{
  display: flex;
  justify-items: stretch;
  justify-content: space-between;;
  margin-top: 15px;
  padding-left: 25px;
  padding-right: 25px;
}
.CarCount{
  border-radius: 6px;

}
.default{
  background-color:rgba(237, 237, 237, 1)
}
</style>