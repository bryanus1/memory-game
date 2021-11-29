<template>
  <b-container class="my-2">
    <h1 class="text-center">Memory Game</h1>
    <b-row align-v="center" class="justify-content-center mt-3">
      <b-col
        v-for="(i, index) in randomIndexes"
        :key="index + 1"
        sm="6"
        lg="2"
        class="my-3"
      >
        <memory-card
          :card="dataCard[i]"
          :number="index + 1"
          @open="open"
        />
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
import MemoryCard from './components/MemoryCard.vue';

export default {
  name: 'App',
  components: {
    MemoryCard,
  },
  created() {
    // eslint-disable-next-line no-plusplus
    for (let i = 0; i < this.dataCard.length; i++) {
      const randomNumber = Math.floor(Math.random() * this.dataCard.length);
      if (this.randomIndexes.includes(randomNumber)) {
        // eslint-disable-next-line no-plusplus
        i--;
      } else {
        this.randomIndexes.push(randomNumber);
      }
    }
  },
  data() {
    return {
      cardsSelected: [],
      randomIndexes: [],
      dataCard: [
        {
          id: 1,
          name: 'Rut',
          isOpened: false,
          isDisabled: false,
        },
        {
          id: 2,
          name: 'Noemi',
          isOpened: false,
          isDisabled: false,
        },
        {
          id: 3,
          name: 'María (Mamá de Jesús)',
          isOpened: false,
          isDisabled: false,
        },
        {
          id: 4,
          name: 'Elizabeth',
          isOpened: false,
          isDisabled: false,
        },
        {
          id: 5,
          name: 'Ester',
          isOpened: false,
          isDisabled: false,
        },
        {
          id: 6,
          name: 'Sara',
          isOpened: false,
          isDisabled: false,
        },
        {
          id: 7,
          name: 'Ana',
          isOpened: false,
          isDisabled: false,
        },
        {
          id: 8,
          name: 'Debora',
          isOpened: false,
          isDisabled: false,
        },
        {
          id: 9,
          name: 'Rebeca',
          isOpened: false,
          isDisabled: false,
        },
        {
          id: 10,
          name: 'Agar',
          isOpened: false,
          isDisabled: false,
        },
        {
          id: 11,
          name: 'Lea',
          isOpened: false,
          isDisabled: false,
        },
        {
          id: 12,
          name: 'Magdalena',
          isOpened: false,
          isDisabled: false,
        },
        {
          id: 13,
          name: 'María (Hermana de Martha)',
          isOpened: false,
          isDisabled: false,
        },
        {
          id: 14,
          name: 'Raquel',
          isOpened: false,
          isDisabled: false,
        },
        {
          id: 15,
          name: 'Sefora',
          isOpened: false,
          isDisabled: false,
        },
        {
          id: 16,
          name: 'Rut',
          isOpened: false,
          isDisabled: false,
        },
        {
          id: 17,
          name: 'Noemi',
          isOpened: false,
          isDisabled: false,
        },
        {
          id: 18,
          name: 'María (Mamá de Jesús)',
          isOpened: false,
          isDisabled: false,
        },
        {
          id: 19,
          name: 'Elizabeth',
          isOpened: false,
          isDisabled: false,
        },
        {
          id: 20,
          name: 'Ester',
          isOpened: false,
          isDisabled: false,
        },
        {
          id: 21,
          name: 'Sara',
          isOpened: false,
          isDisabled: false,
        },
        {
          id: 22,
          name: 'Ana',
          isOpened: false,
          isDisabled: false,
        },
        {
          id: 23,
          name: 'Debora',
          isOpened: false,
          isDisabled: false,
        },
        {
          id: 24,
          name: 'Rebeca',
          isOpened: false,
          isDisabled: false,
        },
        {
          id: 25,
          name: 'Agar',
          isOpened: false,
          isDisabled: false,
        },
        {
          id: 26,
          name: 'Lea',
          isOpened: false,
          isDisabled: false,
        },
        {
          id: 27,
          name: 'Magdalena',
          isOpened: false,
          isDisabled: false,
        },
        {
          id: 28,
          name: 'María (Hermana de Martha)',
          isOpened: false,
          isDisabled: false,
        },
        {
          id: 29,
          name: 'Raquel',
          isOpened: false,
          isDisabled: false,
        },
        {
          id: 30,
          name: 'Sefora',
          isOpened: false,
          isDisabled: false,
        },
      ],
    };
  },
  methods: {
    open(card) {
      this.cardsSelected.push(card);

      Object.entries(this.dataCard).forEach(([key, value]) => {
        if (value.id === card.id) {
          this.dataCard[key].isOpened = true;
        }
      });

      if (this.cardsSelected.length === 2) {
        if (this.cardsSelected[0].name === this.cardsSelected[1].name) {
          this.cardsSelected[0].isDisabled = true;
          this.cardsSelected[1].isDisabled = true;
          this.cardsSelected = [];
        } else {
          setTimeout(() => {
            this.cardsSelected[0].isOpened = false;
            this.cardsSelected[1].isOpened = false;
            this.cardsSelected[0].isDisabled = false;
            this.cardsSelected[1].isDisabled = false;
            this.cardsSelected = [];
          }, 1000);
        }
      }
    },
  },
};
</script>
