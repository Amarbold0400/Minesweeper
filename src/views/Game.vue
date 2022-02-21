<template>
  <div>
    <div class="container pb-3">
      <div class="row justify-content-md-center">
        <div class="col col-md-9 col-lg-7">
          <mine-game :rows="rows" :cols="cols" :bombs="bombs"></mine-game>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import MineGame from "../components/MineGame.vue";
export default {
  components: {
    MineGame,
  },
  name: "game",
  data() {
    return {
      rows: 8,
      cols: 10,
      bombs: 10,
    };
  },
  mounted() {
    this.initParams(this.$route.params);
  },
  methods: {
    initParams(params) {
      const { rows, cols, bombs } = params;
      this.rows = parseInt(rows) || 8;
      this.cols = parseInt(cols) || 10;
      this.bombs = parseInt(bombs) || 10;
    },
  },
  watch: {
    $route(to) {
      this.initParams(to.params);
    },
  },
};
</script>
