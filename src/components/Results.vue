<template>
  <div class="result">
    <p>
      <i class="fas fa-stopwatch"></i> Your Score: <strong>{{ score }} ms</strong>
    </p>
    <p>
      <i class="fas fa-trophy"></i> Your Rank: <strong>{{ rank }}</strong>
    </p>
  </div>
</template>

<script>
export default {
  name: "Result",

  props: ["score"],

  data() {
    return {
      rank: null,
    };
  },

  mounted() {
    this.assignRank();
  },

  methods: {
    assignRank() {
      if (this.score < 250) {
        this.rank = "Mizerave";
      } else if (this.score < 400) {
        this.rank = "Rapidin";
      } else {
        this.rank = "Lerdo";
      }
    },
  },
};
</script>

<style scoped>
.result {
  width: 320px;
  border-radius: 15px;
  background-color: #2c3e50;
  color: #ecf0f1;
  text-align: center;
  padding: 60px 20px;
  margin: 50px auto;
  font-size: 1.5rem;
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.result:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
}

.result p {
  margin: 15px 0;
  font-size: 1.25rem;
  display: flex;
  align-items: center;
  justify-content: center;
}

.result i {
  margin-right: 10px;
  color: #f39c12;
}

.result strong {
  font-weight: bold;
  color: #f1c40f;
}
</style>
