<template>
  <div
    :class="isAlive.isAlive ? 'alive' : 'dead'"
    class="cell"
    @mousedown="reborn(true)"
    @mouseover="reborn(isMouseDown)"
  />
</template>
<script>
export default {
  props: {
    statusObj: {
      default: function () {
        return { isAlive: false };
      },
      type: Object,
    },
    xPos: {
      default: -1,
      type: Number,
    },
    yPos: {
      default: -1,
      type: Number,
    },
    isMouseDown: {
      default: false,
      type: Boolean,
    },
  },
  data() {
    return {
      isAlive: this.statusObj,
    };
  },
  methods: {
    reborn: function (bool) {
      if (bool) {
        this.isAlive.isAlive = !this.isAlive.isAlive;
        this.$emit("wasUpdated", this.isAlive.isAlive);
      }
    },
  },
};
</script>

<style scoped>
.cell {
  flex: 1;
  user-select: none;
  border-right: 1px solid #1a0707;
  border-bottom: 1px solid #1a0707;
  padding-bottom: 100%;
}

.alive {
  background-color: #50fa7b !important;
}
</style>