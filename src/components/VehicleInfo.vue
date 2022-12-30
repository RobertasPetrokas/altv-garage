<template>
  <div class="section-right column">
    <div class="content-wrapper column">
      <section>
        <div>
          <p class="p-thin-grey">Mokėstis bus automatiškai nuskaitytas po</p>
          <p class="p-bold green-text">{{ timeLeftText }}</p>
        </div>
        <div class="row fee-wrapper">
          <p class="p-thin-grey">Nekilnojamo turto mokestis per savaite</p>
          <Tag
            :text="'$' + fee.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ' ')"
          />
        </div>

        <button class="secondary">Apmokėti mokesčius</button>
      </section>

      <section>
        <div>
          <h2>Tempasta</h2>
          <p class="p-thin-grey">T1084DA</p>
        </div>

        <div>
          <p class="p-thin-grey">Kuro likutis</p>
          <div class="fuel row">
            <h3>
              <svg
                width="24"
                height="24"
                viewBox="0 0 24 24"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  d="M3.1 20.6V4.1C3.1 3.80826 3.21589 3.52847 3.42218 3.32218C3.62847 3.11589 3.90826 3 4.2 3H14.1C14.3917 3 14.6715 3.11589 14.8778 3.32218C15.0841 3.52847 15.2 3.80826 15.2 4.1V12.9H17.4C17.9835 12.9 18.5431 13.1318 18.9556 13.5444C19.3682 13.9569 19.6 14.5165 19.6 15.1V19.5C19.6 19.7917 19.7159 20.0715 19.9222 20.2778C20.1285 20.4841 20.4083 20.6 20.7 20.6C20.9917 20.6 21.2715 20.4841 21.4778 20.2778C21.6841 20.0715 21.8 19.7917 21.8 19.5V11.8H19.6C19.3083 11.8 19.0285 11.6841 18.8222 11.4778C18.6159 11.2715 18.5 10.9917 18.5 10.7V6.7554L16.6773 4.9327L18.2327 3.3773L23.6777 8.8223C23.78 8.92431 23.8611 9.04553 23.9164 9.17899C23.9718 9.31245 24.0001 9.45553 24 9.6V19.5C24 20.3752 23.6523 21.2146 23.0335 21.8335C22.4146 22.4523 21.5752 22.8 20.7 22.8C19.8248 22.8 18.9854 22.4523 18.3665 21.8335C17.7477 21.2146 17.4 20.3752 17.4 19.5V15.1H15.2V20.6H16.3V22.8H2V20.6H3.1ZM5.3 5.2V11.8H13V5.2H5.3Z"
                  fill="#C1FF3D"
                />
              </svg>
              {{ fuelLeft }} L
            </h3>
          </div>
        </div>

        <div class="column">
          <p class="p-thin-grey">Transporto būsena</p>
          <div class="car-specs row">
            <div class="column align-right">
              <Cycle :percentage="specs.engine" />
              <p class="p-thin-grey">Variklis</p>
            </div>
            <div class="column align-right">
              <Cycle :percentage="specs.brakes" />
              <p class="p-thin-grey">Stabdžiai</p>
            </div>
            <div class="column align-right">
              <Cycle :percentage="specs.clutch" />
              <p class="p-thin-grey">Sankaba</p>
            </div>
            <div class="column align-right">
              <Cycle :percentage="specs.transmission" />
              <p class="p-thin-grey">Transmisija</p>
            </div>
          </div>
        </div>
      </section>
    </div>
    <button class="primary">Išvažiuoti iš garažo</button>
  </div>
</template>

<script>
import Cycle from "./Cycle.vue";
import Tag from "./Tag.vue";

export default {
  name: "VehicleInfo",
  components: { Cycle, Tag },
  props: ["feePayDate", "fee", "fuelLeft", "specs"],
  data() {
    return { timeLeftText: new Date() };
  },
  created() {
    let timeLeft = Math.abs(this.feePayDate - Date.now()) / 1000;
    var days = Math.floor(timeLeft / 86400);
    timeLeft -= days * 86400;
    var hours = Math.floor(timeLeft / 3600) % 24;
    timeLeft -= hours * 3600;
    var minutes = Math.floor(timeLeft / 60) % 60;
    timeLeft -= minutes * 60;

    let text = "";

    if (days) text += days + " dienų, ";
    if (hours) text += hours + " val., ";
    if (minutes) text += minutes + " min";

    this.timeLeftText = text;
  },
};
</script>

<style>
.section-right {
  align-items: flex-end;
  justify-content: space-between;
}

.section-right > .content-wrapper {
  text-align: right;
  gap: 6vh;
  align-items: flex-end;
  width: 14vw;
}

.section-right > .content-wrapper > section {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  gap: 2vh;
}

.section-right > .content-wrapper > section > .fuel {
  display: flex;
  align-items: baseline;
}

.section-right > .content-wrapper > section > .fee-wrapper {
  gap: 0.6vw;
}

.car-specs {
  gap: 0.6vw;
}
</style>
