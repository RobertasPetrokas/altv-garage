<template>
  <header>
    <div class="header-left">
      <h1>
        <span class="green-text">Mano</span>
        Garažas
      </h1>
      <p class="subheading1 p-thin-grey">
        Lorem Ipsum is simply dummy text of the printing and typesetting
        industry.
      </p>
    </div>
    <div class="header-right">
      <Close />
    </div>
  </header>
</template>

<script>
import Close from "./Close.vue";

export default {
  name: "GarageHeader",
  components: { Close },
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
  padding: 3vh 0;
  margin: 0 2vw;
}

header > .header-left {
  display: flex;
  gap: 3vw;
}

header > .header-left > .subheading1 {
  align-items: center;
  width: 15vw;
  margin: auto;
}

header > .header-right {
  display: flex;
  gap: 1vw;
  text-align: right;
  align-items: center;
}
</style>
