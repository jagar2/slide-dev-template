<script setup>
const props = defineProps({
  titleText: {
    type: String,
    default: 'Default Title',
  },
})
</script>

<template>
  <div class="slidev-layout mainer">
   
    <!-- Title Section -->
    <div
      style="
        position: absolute;
        z-index: 100;
        left: 2.5%;
        top: 1%;
        width: 95%;
        height: 10%;
        transform-origin: left left;
        border: 1px solid black;
      "
    >
      <div class="title-large">
        {{  titleText }}
      </div>
    </div>

    <!-- Main Content Section (2/3 Height) -->
    <div class="main-content">
      <slot />
    </div>

    <!-- Footer Content Section (1/3 Height) -->
    <div class="footer-content">
      <slot name="text" />
    </div>
  </div>
</template>

<style lang="postcss">
.slidev-layout.mainer {
  @apply h-full w-full relative;
  background-image: url("../assets/full-branding.png");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  display: grid;
  grid-template-rows: 10% 60% 30%;
}

/* Title Section */
.title-section {
  position: absolute;
  top: 1%;
  left: 2.5%;
  width: 95%;
  height: 10%;
  z-index: 100;
  transform-origin: left left;
  border: 1px solid black;
  display: flex;
  align-items: center;
  justify-content: left;
  text-align: center;
}

/* Main Content Section */
.main-content {
  grid-row: 2;
  @apply px-10 py-5 border-b border-black overflow-auto;
  border: 1px solid black;
}

/* Footer Content Section */
.footer-content {
  grid-row: 3;
  @apply px-10 py-5 overflow-auto;
  border: 1px solid black;

}
</style>
