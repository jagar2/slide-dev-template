<script setup>
import Layouttextbox from "../components/citation.vue";

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
  textboxHeight: {
    type: [String, Number],
    default: 15,
  },
  spacerHeight: {
    type: [String, Number],
    default: 10,
  },
  reference: {
    type: String,
    default: 'Default Reference',
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
      <div class="relative w-full h-full flex justify-center items-center">
        <img v-if="image"
             :src="image"
             class="max-w-full max-h-full rounded-2xl object-contain block" />
        <slot v-else />
      </div>
    </div>

    <!-- Textbox Content Area -->
    <div class="textbox-content">
      <slot name="text" />
    </div>

    <!-- Spacer Area -->
    <div class="spacer">
      <Layouttextbox :reference="reference" />
    </div>
  </div>
</template>

<style lang="postcss">
/* Layout Grid */
.slidev-layout.custom-layout {
  @apply h-full w-full grid gap-4 px-10 py-6;
  background-image: url("../assets/full-branding.png");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  grid-template-rows: v-bind('`${headerHeight}% ${mainHeight}% ${textboxHeight}% ${spacerHeight}%`');
}

/* Header: Title + Subtitle */
.header {
  @apply flex flex-col justify-center items-start gap-1;
}

.title {
  font-size: 2.8rem;
  font-weight: bold;
  margin: 0;
  padding: 0;
  line-height: 1.1;
  color: #24527a;
}

.subtitle {
  font-size: 1.5rem;
  font-weight: 500;
  margin: 0;
  padding: 0;
  line-height: 1.2;
  color: #2B90B6;
}

/* Main Content (Image Area) */
.main-content {
  @apply flex justify-center items-center w-full h-full overflow-hidden;
  border-width: 0; /* force no borders */
}

/* Textbox Content */
.textbox-content {
  @apply text-left text-base leading-tight;
  margin: 0;
  padding: 0;
}

.textbox-content p,
.textbox-content li {
  margin: 0;
  padding: 0;
  line-height: 1.2;
}

/* Spacer (footer) */
.spacer {
  /* No explicit styles; controlled by layout */
}
</style>
