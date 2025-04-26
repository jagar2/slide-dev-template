<script setup>
const props = defineProps({
  titleText: {
    type: String,
    default: 'Default Title',
  },
  subtitleText: {
    type: String,
    default: 'Default Subtitle',
  },
  image: {
    type: String,
    required: false,
  }
})
</script>

<template>
  <div class="slidev-layout mainer">
    <!-- Title Section (Absolutely Positioned) -->
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
        display: flex;
        align-items: center;
        justify-content: left;
        text-align: center;
      "
    >
      <div class="title-large">
        {{ titleText }}
      </div>
    </div>

    <!-- Subtitle Section -->
    <div class="subtitle-section">
      <div class="subtitle-text">
        {{ subtitleText }}
      </div>
    </div>

    <!-- Main Content Section -->
    <div class="main-content">
      <div class="image-container">
        <img v-if="image" :src="image" class="proportional-image rounded-2xl border-image" />
        <slot v-else></slot>
      </div>
    </div>

    <!-- Footer Content Section -->
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
  grid-template-rows: 10% 65% 25%;
  padding-top: 10%; /* To account for the absolutely positioned title */
}

/* Subtitle Section */
.subtitle-section {
  grid-row: 1;
  @apply px-10 py-2;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
}

.subtitle-text {
  @apply text-2xl font-semibold;
  color: #2B90B6;
}

/* Main Content Section */
.main-content {
  grid-row: 2;
  @apply px-10 py-5 border-b border-black overflow-auto;
  border: 1px solid black;
  display: flex;
  align-items: center;
  justify-content: center;
}

/* Image Container */
.image-container {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

/* Proportional Image */
.proportional-image {
  max-width: 100%;
  max-height: 100%;
  object-fit: contain;
}

/* Footer Content Section */
.footer-content {
  grid-row: 3;
  border: 1px solid black;
  text-align: left;
  display: flex;
  align-items: flex-start;
  justify-content: flex-start;
  padding: 0;
}

/* List styling in footer */
.footer-content ul {
  margin: 0;
  padding: 0;
}

.footer-content li {
  line-height: 1.2;
}
</style>
