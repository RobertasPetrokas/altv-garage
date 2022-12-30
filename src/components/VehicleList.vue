<template>
  <div class="section-left column">
    <div class="info-heading">
      <Tag :text="this.usedGarageSpace + '/' + vehicles.length" />
      <p class="p-thin-grey">Transporto priemonių garaže</p>
      <Tag :text="garageLevel" />
      <p class="p-thin-grey">Garažo lygis</p>
    </div>

    <ul>
      <VehicleCard
        v-for="(vehicle, index) in vehicles"
        :key="index"
        :vehicle="vehicle"
        :index="index"
        :selected="this.activeIdx === index"
        @select-vehicle="selectVehicle(index)"
      />
    </ul>
  </div>
</template>

<script>
import Tag from "./tag.vue";
import VehicleCard from "./vehicleCard.vue";

export default {
  name: "VehicleList",
  components: { Tag, VehicleCard },
  props: ["vehicles", "garageLevel"],
  data() {
    return { activeIdx: undefined, usedGarageSpace: 0 };
  },
  methods: {
    selectVehicle(index) {
      this.activeIdx = index;
    },
  },
  created() {
    this.usedGarageSpace = this.vehicles.filter(
      (vehicle) => Object.keys(vehicle).length !== 0
    ).length;
  },
};
</script>

<style>
.section-left {
  display: flex;
  justify-content: flex-start;
  align-items: baseline;
}

.section-left > .info-heading {
  padding-left: 1vw;
  display: flex;
  width: 17vw;
  gap: 1vw;
  align-items: center;
  margin-bottom: 2vh;
}

.section-left > ul {
  height: 64vh;
  padding: 0 0.8vw;
  list-style-type: none;
  overflow: auto;
  direction: rtl;
  text-align: left;
}

::-webkit-scrollbar {
  width: 5px;
  background: rgba(255, 255, 255, 0.05);
  border-radius: 6px;
}

::-webkit-scrollbar-thumb {
  background: rgba(255, 255, 255, 0.05);
  border-radius: 6px;
}
</style>
