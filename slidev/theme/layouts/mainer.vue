<script setup>
defineProps({
  title: {
    type: String,
    default: 'test of what is would like to be a very long title',
  },
})
</script>

<template>
  <div class="slidev-layout mainer">
    <div
      style="position: absolute; z-index: 100; left: 2.5%; top: 1%; width: 95%; height: 10%; transform-origin: left left; transform: rotate(0deg); border: 1px solid black;"
    >
    <div class="title-large">
        {{ title }}
    </div>    
    </div>
    <div class="main-body" style="position: absolute; top: 13%; left: 2.5%; width: 95%; height: 75%; border: 1px solid black; text-align: left;">
      <slot />
    </div>
  </div>
</template>

<style lang="postcss">
.slidev-layout.mainer {
  background-image: url("../assets/full-branding.png");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;

  @apply text-center py-15 h-full grid;

  h1 {
    @apply text-6xl leading-15;
  }
}

.title-large {
  @apply text-left text-5xl font-bold leading-tight tracking-tight text-primary;
  font-family: var(--slidev-font-sans, sans-serif);
  margin-bottom: 1.5rem;
}
</style>
