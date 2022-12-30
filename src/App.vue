<script setup>
import GarageHeader from "./components/GarageHeader.vue";
import VehicleList from "./components/VehicleList.vue";
import VehicleInfo from "./components/VehicleInfo.vue";
</script>

<template>
  <GarageHeader />
  <div class="main">
    <VehicleList
      :garageLevel="6"
      :vehicles="[
        {
          name: 'Tempasta',
          code: 'T1084DA',
          imgSrc: 'src\\assets\\images\\car1.png',
        },
        {
          name: 'Coquette D10',
          code: 'T1084DA',
          imgSrc: `src\\assets\\images\\car2.png`,
        },
        {
          name: 'Tempasta',
          code: 'T1084DA',
          imgSrc: 'src\\assets\\images\\car1.png',
        },
        {
          name: 'Tempasta',
          code: 'T1084DA',
          imgSrc: 'src\\assets\\images\\car1.png',
        },
        {
          name: 'Tempasta',
          code: 'T1084DA',
          imgSrc: 'src\\assets\\images\\car1.png',
        },
        {
          name: 'Coquette D10',
          code: 'T1084DA',
          imgSrc: `src\\assets\\images\\car2.png`,
        },
        {},
        {},
        {},
        {},
      ]"
    />
    <VehicleInfo
      :feePayDate="new Date('January 17, 2023 03:24:00')"
      :fee="1300"
      :fuelLeft="120"
      :specs="{ engine: 64, brakes: 34, clutch: 84, transmission: 64 }"
    />
  </div>
</template>

<style scoped>
.main {
  display: flex;
  justify-content: space-between;
  padding: 3vh 0;
  margin: 0 2vw 0 1vw;
}
</style>
