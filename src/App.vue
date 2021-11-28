<template>
  <b-container fluid class="my-5">
    <h1 class="text-center">Memory Game</h1>
    <b-row>
      <b-col
        v-for="index in randomIndexesOne"
        :key="index + 1"
        sm="2"
        lg="2"
      >
        <memory-card
          :card="dataCard[index]"
          :number="index + 1"
          @open="open"
        />
      </b-col>
      <b-col
        v-for="index in randomIndexesTwo"
        :key="index + 1 + dataCard.length"
        sm="2"
        lg="2"
      >
        <memory-card
          :card="dataCard[index]"
          :number="index + 1 + dataCard.length"
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
      if (this.randomIndexesOne.includes(randomNumber)) {
        // eslint-disable-next-line no-plusplus
        i--;
      } else {
        this.randomIndexesOne.push(randomNumber);
      }
    }
    // eslint-disable-next-line no-plusplus
    for (let i = 0; i < this.dataCard.length; i++) {
      const randomNumber = Math.floor(Math.random() * this.dataCard.length);
      if (this.randomIndexesTwo.includes(randomNumber)) {
        // eslint-disable-next-line no-plusplus
        i--;
      } else {
        this.randomIndexesTwo.push(randomNumber);
      }
    }
  },
  data() {
    return {
      cardsSelected: [],
      randomIndexesOne: [],
      randomIndexesTwo: [],
      dataCard: [
        {
          name: 'Rut',
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          name: 'Noemi',
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          name: 'María (Mamá de Jesús)',
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          name: 'Elizabeth',
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          name: 'Ester',
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          name: 'Sara',
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          name: 'Ana',
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          name: 'Debora',
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          name: 'Rebeca',
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          name: 'Agar',
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          name: 'Lea',
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          name: 'María (Hermana de Martha)',
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          name: 'Magdalena',
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          name: 'Raquel',
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
        {
          name: 'Sefora',
          isDisabled: false,
          img: 'https://picsum.photos/200/300/?random',
        },
      ],
    };
  },
  methods: {
    open(card) {
      this.cardsSelected.push(card);

      if (this.cardsSelected.length === 2) {
        if (this.cardsSelected[0].name === this.cardsSelected[1].name) {
          this.cardsSelected[0].isDisabled = true;
          this.cardsSelected[1].isDisabled = true;
          this.cardsSelected = [];
        } else {
          setTimeout(() => {
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
