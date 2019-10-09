<template>
    <h1 class="routeSkipHeading">
        <button id="skip-link" tabindex="-1" class="routeSkipLink" @click="focusTargetId" :aria-label="'Skip to ' + targetId">«</button>
        <slot />
    </h1>
</template>

<style>
.routeSkipHeading {
  position: relative;
}

.routeSkipLink {
  position: absolute;
  display: inline-block;
  margin-left: -1em;
  opacity: 0;
  text-decoration: none;
  border: none;
  background: transparent;
  -webkit-appearance: none;
  font: inherit;
  color: #096073;
}

[data-whatinput="keyboard"] .routeSkipLink:focus {
  opacity: 1;
}
</style>

<script>
export default {
  props: ["targetId"],
  methods: {
    focusTargetId() {
      const target = document.querySelector(`#${this.targetId}`);

      if (target) {
        target.focus();
      }
    }
  }
};
</script>
