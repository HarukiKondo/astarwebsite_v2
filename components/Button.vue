<template>
  <a v-if="href !== ''" :class="classes" :href="href">
    <span><slot>Button</slot></span>
  </a>
  <button v-else :class="classes" type="button">
    <span><slot>Button</slot></span>
  </button>
</template>

<script setup lang="ts">
import { computed } from "vue";

const props = defineProps({
  href: {
    type: String,
    default: "",
  },
  color: {
    type: String,
    default: "primary",
  },
  variant: {
    type: String,
    default: "contained",
  },
  size: {
    type: String,
    default: "md",
  },
});

const classes = computed(() => ({
  btn: true,
  primary: props.color === "primary",
  secondary: props.color === "secondary",
  [`${props.size || "md"}`]: true,
  contained: props.variant === "contained",
  outlined: props.variant === "outlined",
}));
</script>

<style lang="postcss">
.btn {
  @apply shadow font-medium transition-all inline-block hover:cursor-pointer;
}
.btn span {
  @apply flex items-center justify-center;
}
.btn.sm {
  @apply text-sm px-3 py-1;
}
.btn.md {
  @apply px-4 py-2;
}
.btn.lg {
  @apply text-lg px-10 py-3;
}
.btn.xl {
  @apply text-lg sm:text-xl px-10 py-4 sm:px-14 sm:py-5;
}
.btn.xxl {
  @apply text-xl px-14 py-5 sm:text-2xl sm:px-20 sm:py-6;
}
.btn.contained.primary {
  @apply text-white rounded-xl;
  background: linear-gradient(
    120deg,
    #e6007a -5.88%,
    #703ac2 15.42%,
    #0070eb 40.77%,
    #0297fb 72.21%,
    #0ae2ff 95.53%
  );
}
.btn.contained.primary:hover {
  background: linear-gradient(
    120deg,
    #ff1994 -5.88%,
    #8e4fee 15.42%,
    #3091f9 40.77%,
    #3db1ff 72.21%,
    #3fe9ff 95.53%
  );
}
.btn.outlined.primary {
  border-radius: 0.625rem;
  position: relative;
  background: linear-gradient(
    120deg,
    #ffebf6 -5.88%,
    #ebdeff 15.42%,
    #d3e8ff 40.77%,
    #bee5ff 72.21%,
    #bef7ff 95.53%
  );
}
.btn.outlined.primary:hover {
  background: linear-gradient(
    120deg,
    #e6007a -5.88%,
    #703ac2 15.42%,
    #0070eb 40.77%,
    #0297fb 72.21%,
    #0ae2ff 95.53%
  );
}
.btn.outlined.primary::after {
  @apply rounded-xl;
  content: "";
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: -1;
  margin: -2px;
  background-image: linear-gradient(
    120deg,
    #e6007a -5.88%,
    #703ac2 15.42%,
    #0070eb 40.77%,
    #0297fb 72.21%,
    #0ae2ff 95.53%
  );
}
.btn.outlined.primary span {
  background: linear-gradient(
    90deg,
    #e6007a -5.88%,
    #703ac2 15.42%,
    #0070eb 40.77%,
    #0297fb 72.21%,
    #0ae2ff 95.53%
  );
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  @apply text-space-sky;
}
.btn.outlined.primary:hover span {
  color: white;
  -webkit-text-fill-color: white;
}
.btn.contained.secondary {
  @apply border-2 border-white rounded-xl text-space-gray-dark bg-white bg-opacity-80 hover:bg-opacity-100;
}
.btn.outlined.secondary {
  @apply border border-white rounded-xl bg-white/20 hover:bg-white/60 hover:text-space-gray-dark;
}
</style>
