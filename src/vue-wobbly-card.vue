<template>
  <div
    :id="generateId"
    class="vue-wobbly-card"
    @mousemove="wobble($event)"
    @mouseleave="defaultPosition"
  >
    <div class="container">
      <slot />
    </div>
  </div>
</template>

<script>
export default /*#__PURE__*/ {
  name: "VueWobblyCard",
  data: () => ({
    cardId: null,
  }),
  computed: {
    generateId() {
      this.cardId = `vwc-${Date.now()}${Math.floor(Math.random() * 255)}`;
      return this.cardId;
    },
    getOuterElement() {
      return document.getElementById(`${this.generateId}`);
    },
    getInnerElement() {
      return document.querySelector(`#${this.generateId} .container`);
    },
    getWidthAndHeight() {
      const { width, height } = this.getOuterElement.getBoundingClientRect();
      return { width, height };
    },
  },
  methods: {
    defaultPosition() {
      this.getInnerElement.style.transition = "all 0.5s ease-in-out";
      this.getInnerElement.style.setProperty("--x-pos", 0);
      this.getInnerElement.style.setProperty("--y-pos", 0);
    },
    wobble(event) {
      const { width, height } = this.getWidthAndHeight;
      const { layerX, layerY } = event;
      this.getInnerElement.style.transition = "all 0.0s ease-in-out";

      this.getInnerElement.style.setProperty("--x-pos", layerX / width - 0.5);
      this.getInnerElement.style.setProperty("--y-pos", layerY / height - 0.5);
    },
  },
};
</script>

<style scoped>
.vue-wobbly-card {
  width: max-content;
  height: max-content;
}

.container {
  width: 100%;
  height: 100%;
  /* background: linear-gradient(to bottom right, #9847ff 0%, #c447ff 100%); */

  --x-pos: 0;
  --y-angle: calc(var(--x-pos) * 5deg);

  --y-pos: 0;
  --x-angle: calc(var(--y-pos) * 5deg);

  transform: perspective(200px) rotateX(var(--y-angle)) rotateY(var(--x-angle));
}
</style>
