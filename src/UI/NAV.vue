<template>
  <div class="Nav">
    <span class="Nav__header dm-sans">Demo Test</span>
    <span class="Nav__item dm-sans"><img class="Nav__icon" src="./res/user.svg" alt="UserPic">Profile</span>
    <span class="Nav__item dm-sans"><img class="Nav__icon" src="./res/rim.svg" alt="VehPic">Vehicles</span>
    <span class="Nav__item dm-sans"><img class="Nav__icon" src="./res/settings.svg" alt="SettingsPic">Setting</span>
  </div>
</template>

<script>
export default {

}
</script>

<style scoped>
.dm-sans {
  font-family: "DM Sans", sans-serif;
  font-weight: 700;
  font-style: normal;
}
.Nav{
  width: 15%;
  min-height: 145%;
  overflow: hidden;
  background-color: rgba(40, 40, 40, 1);
  text-align: center;
  color: #FFF;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.Nav__header{
  font-size: 24pt;
  margin-bottom: 14vh;
  padding-top: 15px;
}
.Nav__item{
  display: flex;
  align-items: center;
  justify-content: center;
  height: 48px;
  width: 100%;
  font-size: 16pt;
  color: rgba(255, 255, 255, 0.2);
  line-height: 20px;
  font-weight: 500;
}
.Nav__item:hover{
  border-left: red solid;
  color: #fff;
  background-color:rgba(255, 255, 255, 0.2) ;
  cursor: pointer;
}
.Nav__icon{
  height: 24px;
  width: 24px;
  padding-right: 15px;
}

</style>