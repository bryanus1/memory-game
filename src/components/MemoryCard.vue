<template>
  <div class="flip-card">
    <div class="flip-card-inner" :style="rotate">
      <div class="flip-card-front justify-content-center d-flex align-items-center">
        <b-row>
          <b-col sm="12">
            <img
              :src="require(`../assets/images/numeros/NUMEROS-MUJERES-${this.number}.png`)"
              :alt="`NUMEROS-MUJERES-${this.number}`"
            >
            <div class="button" :style="hideButton">
              <b-button
                @click="open"
                pill
                variant="outline-light"
                :disabled="card.isDisabled"
              >
                Girar
              </b-button>
            </div>
          </b-col>
        </b-row>
      </div>
      <div class="flip-card-back justify-content-center d-flex align-items-center">
        <img
          :src="require(`../assets/images/mujeres/MUJERES-${this.card.id}.png`)"
          :alt="`MUJERES-${this.card.id}`"
        >
      </div>
    </div>
  </div>
</template>

<script>
export default {
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
  computed: {
    hideButton() {
      if (this.card.isOpened || this.card.isDisabled) {
        return { display: 'none' };
      }

      return { display: 'block' };
    },
    rotate() {
      // Rotate the card when it's opened or card is disabled
      if (this.card.isOpened || this.card.isDisabled) {
        return { transform: 'rotateY(180deg)' };
      }

      return { transform: 'rotateY(0deg)' };
    },
  },
  methods: {
    open() {
      if (!this.card.isDisabled) {
        this.$emit('open', this.card);
      }
    },
  },
};
</script>

<style scoped>
img {
  width: 7rem;
  height: 9rem;
}

.button {
  position: absolute;
  top: 95%;
  left: 20%;
  z-index: 1;
  -ms-transform: translateY(-95%);
  transform: translateY(-95%);
  justify-content: center;
}

.flip-card {
  background-color: transparent;
  width: 7rem;
  height: 9rem;
  perspective: 1000px;
  border-radius: 10px;
}

.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.6s;
  transform-style: preserve-3d;
}

.flip-card-front, .flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
}

.flip-card-front {
  background-color: transparent;
  color: black;
}

.flip-card-back {
  color: white;
  transform: rotateY(180deg);
}
</style>
