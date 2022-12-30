<template>
  <li
    @click="selectVehicle(index)"
    v-if="vehicle.name"
    class="border-default"
    :class="{ 'selected-car': selected }"
  >
    <div class="column">
      <p>{{ vehicle.name }}</p>
      <p class="p-thin-grey">{{ vehicle.code }}</p>
    </div>
    <img class="car-img" :src="vehicle.imgSrc" />
  </li>
  <li v-if="!vehicle.name" class="border-default empty column">
    <p>Laisva vieta</p>
    <p class="p-thin-grey">Transportui</p>
  </li>
</template>

<script>
export default {
  name: "vehicleCard",
  props: ["vehicle", "selected", "index"],
  emits: ["select-vehicle"],
  methods: {
    selectVehicle(index) {
      this.$emit("select-vehicle", index);
    },
  },
};
</script>

<style>
li {
  display: flex;
  padding: 1.5vh 1vw;
  height: 5vh;
  width: 16vw;
  align-items: center;
  gap: 1vw;
  margin-bottom: 1vh;
  justify-content: end;
}

li > .car-img {
  width: 90px;
  height: 50px;
  object-fit: contain;
}

li.selected-car {
  background: #ffffff;
  color: rgba(0, 0, 0, 1);
}

li.empty {
  background: rgba(157, 157, 157, 0.1);
  color: rgba(157, 157, 157, 1);
  gap: 0.2vh;
  justify-content: center;
}
</style>
