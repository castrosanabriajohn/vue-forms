<template>
  <ul>
    <li :class="{ active: activeRating === 'poor' }">
      <button @click="activateRating('poor')" type="button">Poor</button>
    </li>
    <li :class="{ active: activeRating === 'average' }">
      <button @click="activateRating('average')" type="button">Average</button>
    </li>
    <li :class="{ active: activeRating === 'great' }">
      <button @click="activateRating('great')" type="button">Great</button>
    </li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      activeRating: null,
    };
  },
  methods: {
    activateRating(option) {
      this.activeRating = option;
    },
  },
};
</script>

<style scoped>
.active {
  border-color: blueviolet;
}

.active button {
  color: blueviolet;
}

ul {
  list-style: none;
  margin: 0.5rem 0;
  padding: 0;
  display: flex;
}

li {
  margin: 0 1rem;
  border: 1px solid #ccc;
  padding: 1rem;
  display: flex;
  justify-content: center;
  align-items: center;
}

button {
  font: inherit;
  border: none;
  background-color: transparent;
  cursor: pointer;
}
</style>
