<template>
  <div class="game-cell" :class="setClass()">
    <div v-if="cell.isOpen && cell.bombCount">
      {{ cell.bombCount }}
    </div>
    <div v-if="cell.hasFlag"></div>
  </div>
</template>

<script>
export default {
  name: "game-cell",
  props: {
    cell: {
      type: Object,
      required: true,
    },
  },
  methods: {
    setClass() {
      const { cell } = this;
      if (cell.isOpen && cell.hasBomb) {
        return "game-bomb";
      }
      if (cell.isOpen) {
        return "game-open";
      }
      if (cell.hasFlag) {
        return "game-flag";
      }
      return "";
    },
  },
};
</script>

<style lang="scss">
.game {
  &-cell {
    display: flex;
    font-size: 1.3em;
    justify-content: center;
    min-height: 35px;
    min-width: 35px;
    align-items: center;
    background: rgba(30, 60, 0, 0.2);
    border: 1px white solid;
    color: #2c3e50;
    cursor: pointer;

    &:hover {
      background: rgba(0, 0, 0, 0.3);
    }
  }

  &-bomb {
    background: #c0392b;
    &:hover {
      background: rgba(192, 57, 43, 0.7);
    }
  }

  &-open {
    background: rgba(0, 0, 0, 0.05);
    &:hover {
      background: rgba(0, 0, 0, 0.1);
    }
  }

  &-flag {
    background: #eb8444;
    &:hover {
      background: rgba(235, 132, 68, 0.7);
    }
  }
}
</style>
