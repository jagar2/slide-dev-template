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
  headerHeight: {
    type: [String, Number],
    default: 15,
  },
  mainHeight: {
    type: [String, Number],
    default: 55,
  },
  footerHeight: {
    type: [String, Number],
    default: 15,
  },
  spacerHeight: {
    type: [String, Number],
    default: 10,
  },
})
</script>

<template>
  <div class="slidev-layout custom-layout">
    <!-- Title and Subtitle Area -->
    <div class="header">
      <h1 class="title">{{ titleText }}</h1>
      <h2 class="subtitle">{{ subtitleText }}</h2>
    </div>

    <!-- Main Content Area -->
    <div class="main-content">
        <div class="w-1/2 flex justify-center items-center p-8 max-h-md object-cover" :class="imageOrder">
            <img v-if="image" :src="image"  class="rounded-2xl border-image h-full object-cover" />
            <slot v-else />
        </div>
    </div>

    <!-- Footer Text Area -->
    <div class="footer-content">
      <slot name="text" />
    </div>

    <!-- Spacer Area -->
    <div class="spacer"></div>
  </div>
</template>

<style lang="postcss">
.slidev-layout.custom-layout {
  @apply h-full w-full grid gap-4 px-10 py-6;
  background-image: url("../assets/full-branding.png");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;

  /* Create 4 rows: Header, Main, Footer, Spacer */
  grid-template-rows: v-bind('`${headerHeight}% ${mainHeight}% ${footerHeight}% ${spacerHeight}%`');
}

/* Header: Title + Subtitle */
.header {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
  gap: 0.25rem;
}

/* Title */
.title {
  font-size: 2.8rem; /* relative size - safe */
  font-weight: bold;
  margin: 0;
  padding: 0;
  line-height: 1.1; /* tight line height */
  color: #24527a;
}

/* Subtitle */
.subtitle {
  font-size: 1.5rem;
  font-weight: 500;
  margin: 0;
  padding: 0;
  color: #2B90B6;
  line-height: 1.2;
}

/* Main Content */
.main-content {
  @apply flex justify-center items-center;
  overflow: hidden;
}

/* Footer Content */
.footer-content {
  text-align: left;
  font-size: 1rem;
  line-height: 1.2;
  padding: 0;
  margin: 0;
  display: block;
}

.footer-content p, .footer-content li {
  margin: 0;
  padding: 0;
  line-height: 1.2;
}

/* Spacer */
.spacer {
  /* This section is a flexible spacer */
}
</style>
