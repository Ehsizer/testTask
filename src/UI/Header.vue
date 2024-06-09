<template>
  <div class="Header">
      <h1 class="dm-sans">Vehicles</h1>
      <div class="Counter">{{cars.length}}</div>
      <div class="rightHead">
        <button class="addVeh"> + </button>
        <div class="NameBlock">
          <img src="./res/Photo.png" alt="Photo">
          <span class="Name">John Doe</span>
        </div>
        <div class="LangSelect">
          <img src="./res/uk.png" alt="Lang">
          <select class="LangSlider">
            <option label="En"></option>
            <option label="Ru"></option>
          </select>
        </div>
      </div>

  </div>


</template>

<script>


export default {
  props:{
    cars:{
      type:Array,
      required:true
    }
  },
}
</script>

<style scoped>
.Header{
  margin-top: 30px;

  border-bottom: rgba(228, 228, 228, 1) solid;
  background-color: #FFF;
  display: flex;

}
.Name{

}
.LangSlider{
  border: none;
  background-color: #fff;
  font-weight: 500;
  font-size: 15px;
}
.dm-sans{
  font-size: 32pt;
  font-weight: 700;
  margin-left: 30px;
}

.Counter{
  background-color: rgba(243, 246, 248, 1);
  margin-left: 18px;
  width: 56px;
  height: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-top: 10px;
}
.rightHead{
  display: flex;
  align-items: stretch;
  margin-left: auto;
  padding-right: 100px;
}
.NameBlock{
  width: 131px;
  align-items: center;
  justify-content: space-between;
  height: 46px;
  margin-right: 15px;
  display: flex;
}
.LangSelect{
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 46px;
  margin-left: 5%;
}
.addVeh{
  font-size: 24pt;
  background-color: #fff;
  border: 1px solid rgba(232, 110, 132, 1);
  color: rgba(232, 110, 132, 1);
  width: 42px;
  height: 42px;
  border-radius: 6px;
  margin-right: 50px;
}
</style>