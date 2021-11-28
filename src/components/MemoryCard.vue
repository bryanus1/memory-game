<template>
  <b-card
    class="memory-card m-5"
    :border-variant="card.isDisabled ? 'secondary' : 'primary'"
  >
    <h5>{{ isOpen ? card.name : card.name }}</h5>

    <b-button
      @click="open"
      :variant="card.isDisabled ? 'secondary' : 'primary'"
      :disabled="card.isDisabled"
    >
        Girar
      </b-button>
  </b-card>
</template>

<script>
export default {
  name: 'MemoryCard',
  props: {
    card: {
      type: Object,
      required: true,
    },
    number: {
      type: Number,
      required: true,
    },
  },
  data() {
    return {
      isOpen: false,
    };
  },
  methods: {
    open() {
      this.isOpen = true;
      if (!this.card.isDisabled) {
        this.$emit('open', this.card);
      }
    },
  },
};
</script>

<style scoped>
.memory-card {
  max-width: 200px;
}
</style>
