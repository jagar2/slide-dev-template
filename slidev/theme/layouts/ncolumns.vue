<script setup>
const props = defineProps({
  titleText: {
    type: String,
    default: 'Default Title',
  },
  columns: {
    type: Number,
    default: 2,
  },
  images: {
    type: Array,
    default: () => [],
  },
  titles: {
    type: Array,
    default: () => [],
  },
  contentRatio: {
    type: Number,
    default: 80,
    validator: (value) => value > 0 && value < 100
  },
  footerRatio: {
    type: Number,
    default: 10,
    validator: (value) => value > 0 && value < 100
  }
})

// Calculate the header ratio based on content and footer ratios
const headerRatio = 100 - props.contentRatio - props.footerRatio
</script>

<template>
  <div class="slidev-layout ncolumns">
    <!-- Title Section -->
    <div class="title-section">
      <div class="title-large">
        {{ titleText }}
      </div>
    </div>

    <!-- Main Content Section -->
    <div class="main-content">
      <div class="columns-container" :style="{ gridTemplateColumns: `repeat(${columns}, 1fr)` }">
        <div v-for="(image, index) in images" :key="index" class="column">
          <div v-if="titles[index]" class="column-title">
            {{ titles[index] }}
          </div>
          <div class="image-container">
            <img :src="image" class="proportional-image rounded-2xl border-image" />
          </div>
        </div>
      </div>
    </div>

    <!-- Footer Content Section -->
    <div class="footer-content">
      <slot name="text" />
    </div>
  </div>
</template>

<style lang="postcss">
.slidev-layout.ncolumns {
  @apply h-full w-full relative;
  background-image: url("../assets/full-branding.png");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  display: grid;
  grid-template-rows: v-bind('`${headerRatio}% ${props.contentRatio}% ${props.footerRatio}%`');
}

/* Title Section */
.title-section {
  grid-row: 1;
  @apply px-10 py-2;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  border: 1px solid black;
}

.title-large {
  @apply text-3xl font-bold;
  color: #2B90B6;
}

/* Main Content Section */
.main-content {
  grid-row: 2;
  @apply px-10 py-5 overflow-auto;
  border: 1px solid black;
  width: 100%;
}

.columns-container {
  display: grid;
  gap: 1rem;
  height: 100%;
  width: 100%;
}

.column {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  width: 100%;
}

.column-title {
  @apply text-xl font-semibold text-center;
  color: #2B90B6;
}

.image-container {
  flex: 1;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 1px solid #ccc;
  border-radius: 0.5rem;
  overflow: hidden;
  width: 100%;
}

.proportional-image {
  max-width: 100%;
  max-height: 100%;
  object-fit: contain;
}

/* Footer Content Section */
.footer-content {
  grid-row: 3;
  @apply px-10 py-5 overflow-auto;
  border: 1px solid black;
}
</style> 