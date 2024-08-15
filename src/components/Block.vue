<template>
  <div class="block" v-if="showBlock" @click="stopTimer">Click Me</div>
</template>

<script>
export default {
  name: "Block",

  props: ["delay"],

  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },

  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },

  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },

    stopTimer() {
      clearInterval(this.timer);
      this.$emit("endGame", this.reactionTime);
    },
  },
};
</script>

<style scoped>
.block {
  width: 300px;
  border-radius: 15px;
  background-color: #067272;
  color: white;
  text-align: center;
  padding: 80px 0;
  margin: 50px auto;
  font-size: 1.5rem;
  cursor: pointer;
  transition: transform 0.2s ease, background-color 0.3s ease;
}

.block:hover {
  background-color: #048585;
  transform: scale(1.05);
}
</style>
