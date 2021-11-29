<template>
  <b-container class="my-2">
    <h1 class="text-center">Memory Game</h1>
    <b-row align-v="center" class="justify-content-center mt-3">
      <b-col
        v-for="(i, index) in randomIndexes"
        :key="index + 1"
        sm="2"
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
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          id: 2,
          name: 'Noemi',
          isOpened: false,
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          id: 3,
          name: 'María (Mamá de Jesús)',
          isOpened: false,
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          id: 4,
          name: 'Elizabeth',
          isOpened: false,
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          id: 5,
          name: 'Ester',
          isOpened: false,
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          id: 6,
          name: 'Sara',
          isOpened: false,
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          id: 7,
          name: 'Ana',
          isOpened: false,
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          id: 8,
          name: 'Debora',
          isOpened: false,
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          id: 9,
          name: 'Rebeca',
          isOpened: false,
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          id: 10,
          name: 'Agar',
          isOpened: false,
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          id: 11,
          name: 'Lea',
          isOpened: false,
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          id: 12,
          name: 'María (Hermana de Martha)',
          isOpened: false,
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          id: 13,
          name: 'Magdalena',
          isOpened: false,
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          id: 14,
          name: 'Raquel',
          isOpened: false,
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          id: 15,
          name: 'Sefora',
          isOpened: false,
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          id: 16,
          name: 'Rut',
          isOpened: false,
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          id: 17,
          name: 'Noemi',
          isOpened: false,
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          id: 18,
          name: 'María (Mamá de Jesús)',
          isOpened: false,
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          id: 19,
          name: 'Elizabeth',
          isOpened: false,
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          id: 20,
          name: 'Ester',
          isOpened: false,
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          id: 21,
          name: 'Sara',
          isOpened: false,
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          id: 22,
          name: 'Ana',
          isOpened: false,
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          id: 23,
          name: 'Debora',
          isOpened: false,
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          id: 24,
          name: 'Rebeca',
          isOpened: false,
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          id: 25,
          name: 'Agar',
          isOpened: false,
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          id: 26,
          name: 'Lea',
          isOpened: false,
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          id: 27,
          name: 'María (Hermana de Martha)',
          isOpened: false,
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          id: 28,
          name: 'Magdalena',
          isOpened: false,
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          id: 29,
          name: 'Raquel',
          isOpened: false,
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          id: 30,
          name: 'Sefora',
          isOpened: false,
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
      ],
    };
  },
  methods: {
    open(card) {
      console.log(card);
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
    reset() {
      this.cardsSelected = [];
      this.dataCard.forEach((index) => {
        this.dataCard[index].isDisabled = false;
      });
    },
  },
};
</script>
