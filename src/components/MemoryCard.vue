<template>
  <div class="flip-card">
    <div class="flip-card-inner" :style="rotate">
      <div class="flip-card-front justify-content-center d-flex align-items-center">
        <b-row>
          <b-col sm="12">
            <h1 class="text-center">{{ number }}</h1>
          </b-col>
          <b-col sm="12">
            <b-button
              @click="open"
              pill
              variant="outline-light"
              :disabled="card.isDisabled"
            >
              Girar
            </b-button>
          </b-col>
        </b-row>
      </div>
      <div class="flip-card-back justify-content-center d-flex align-items-center">
        {{ card.name }}
      </div>
    </div>
  </div>
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
  computed: {
    rotate() {
      // Rotate the card when it's opened or card is disabled
      if (this.card.isOpened || this.card.isDisabled) {
        return { transform: 'rotateY(180deg)' };
      }

      return { transform: 'rotateY(0deg)' };
    },
  },
  data() {
    return {
      degrees: '0deg',
    };
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
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
}

.flip-card-front, .flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
}

.flip-card-front {
  background-color: pink;
  color: black;
}

.flip-card-back {
  background-color: #2980b9;
  color: white;
  transform: rotateY(180deg);
}
</style>
