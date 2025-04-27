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
  },
  lineSpacing: {
    type: [String, Number],
    default: 1.2
  },
  titleHeight: {
    type: [String, Number],
    default: 10
  },
  mainHeight: {
    type: [String, Number],
    default: 65
  },
  footerHeight: {
    type: [String, Number],
    default: 25
  },
  showTitle: {
    type: Boolean,
    default: true
  },
  showSubtitle: {
    type: Boolean,
    default: true
  },
  titleFontSize: {
    type: [String, Number],
    default: 28
  }
})
</script>

<template>
  <div class="slidev-layout mainer">
    <!-- Title Section (Absolutely Positioned) -->
    <div v-if="showTitle"
      style="
        position: absolute;
        z-index: 100;
        left: 2.5%;
        top: 2.5%;
        width: 95%;
        height: 30pt;
        transform-origin: left left;
        display: flex;
        /* align-items: center; */
        justify-content: left;
        /* text-align: center; */
        border: 1px solid black;
        overflow: visible;
        margin: 0;
        padding: 0;
      "
    >
      <div class="title-large" :style="{ fontSize: `${titleFontSize}pt`, margin: 0, padding: 0 }">
        {{ titleText }}
      </div>
    </div>

    <!-- Subtitle Section -->
    <div v-if="showSubtitle" class="subtitle-section">
      <div class="subtitle-text">
        {{ subtitleText }}
      </div>
    </div>

    <!-- Main Content Section -->
    <div class="main-content">
      <div class="image-container">
        <img v-if="image" :src="image" class="proportional-image"/>
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
  grid-template-rows: v-bind('`${showSubtitle ? titleHeight : 0}% ${mainHeight}% ${footerHeight}%`');
  padding-top: v-bind('`${showSubtitle ? titleHeight : 0}%`');
}

/* Subtitle Section */
.subtitle-section {
  grid-row: 1;
  @apply px-10 py-2;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  margin: 0pt
}

.subtitle-text {
  @apply text-2xl font-semibold;
  color: #2B90B6;
  border: none; /* Remove any border to prevent a light gray box */
}

/* Main Content Section */
.main-content {
  grid-row: 2;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 3px;
  padding: 0px;
  border: none; /* Remove any border to prevent a light gray box */
}

.image-container img {
  max-width: 100%;
  max-height: 100%;
  object-fit: contain;
  border-radius: 8px; /* Add rounded border to the image */
  border: none; /* Remove any border to prevent a light gray box */
  margin: 1px;
}

/* Image Container */
.image-container {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  border: none; /* Remove any border to prevent a light gray box */
  margin: 10px;
}

/* Proportional Image */
.proportional-image {
  max-width: 100%;
  max-height: 100%;
  object-fit: contain;
  border: none; /* Remove any border to prevent a light gray box */
  margin: 3px;
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
