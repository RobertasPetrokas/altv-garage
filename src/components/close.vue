<template>
  <div class="esc">
    <div class="content">
      <h4>Uždaryti</h4>
      <p>ESC</p>
    </div>

    <div class="icon">
      <svg
        width="15"
        height="15"
        viewBox="0 0 15 15"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          d="M7.85547 5.29889L13.0885 0.0195644L14.8328 1.77934L9.5998 7.05867L14.8328 12.338L13.0885 14.0978L7.85547 8.81845L2.62247 14.0978L0.878138 12.338L6.11114 7.05867L0.878138 1.77934L2.62247 0.0195644L7.85547 5.29889Z"
          fill="white"
        />
      </svg>
    </div>
  </div>
</template>
<style scoped>
.esc {
  display: flex;
  align-items: center;
  position: absolute;
  right: 5%;
  top: 5vh;
  font-family: "Overpass", sans-serif;
}

.esc > .icon {
  width: 45.6px;
  height: 46px;
  background: rgba(255, 255, 255, 0.19);
  border-radius: 8px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.esc > .content > h4 {
  font-weight: 700;
  font-size: 14px;
  color: #ffffff;
  margin: 0;
}

.esc > .content {
  text-align: right;
  margin-right: 15px;
}

.esc > .content > p {
  color: rgba(255, 255, 255, 0.6);
  font-weight: 400;
  font-size: 14px;
  margin-top: 2px;
}
</style>
<script>
export default {
  name: "close_element",
};
</script>
