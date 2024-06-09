<template>
  <div class="BodyLayout">
  <Header :cars="cars" class="head"/>
  <div class="Container">
    <NAV class="nav"/>
    <Content class="Content"
             :cars = "cars"
             :vehCounter = "vehiclesCount"
             @click="vehiclesCount = $event"
             :totalCars = "totalCars"
    />
  </div>
  </div>
</template>
<script>
import NAV from "@/UI/NAV";
import Content from "@/UI/Content";
import Header from "@/UI/Header";
import axios from "axios";
export default {
  components: {Content, Header, NAV},
  data(){
    return{
      cars:[],
      vehiclesCount: 9,
      totalCars: 0,
    }
  },
  methods:{
    toggle(event){
      this.vehiclesCount = event;
      console.log(event, this.vehiclesCount)
    },
    async fetchCars(vehiclesCount){
      try{
        const responseTotal = await axios.get('https://api.caiman-app.de/api/cars-test?');
        console.log(responseTotal.data.data.length)
        const response = await axios.get('https://api.caiman-app.de/api/cars-test?per_page=' + vehiclesCount +'&page=1&');
        this.cars = response.data.data;
        this.totalCars = responseTotal.data.data.length
      }
      catch (e){
        alert('Ошибка')
      }
    },
  },
  mounted(){
    this.fetchCars(this.vehiclesCount);
  },
  watch:{
    vehiclesCount: {
      handler(val, oldVal) {
        this.fetchCars(val)
      },
      deep: true
    },
  }
}
</script>
<style lang="scss">
*{
  margin: 0;
  padding: 0;
}
.BodyLayout{
  display: flex;
  flex-direction: column;
  width: 100%;
  height: 100%;

}
.Container{
  margin: auto auto;
  align-self: flex-start;
  display: flex;


}
.Content{

}

.dm-sans {
  font-family: "DM Sans", sans-serif;
  font-weight: 700;
  font-style: normal;
}
.head{
  width: 85%;
  height: 6vh;
  margin-left: 15%;
}
.nav{
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
}

</style>
