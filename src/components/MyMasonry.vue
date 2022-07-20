<template>
  <!--<button @click="addItem">Add</button> -->
  <div class="grid" ref="masonry">
    <div class="grid-item"></div>
    <div v-for="item in items" class="grid-item">
      <img :src="item.src" alt="" />
    </div>
  </div>
</template>

<script>
import Masonry from 'masonry-layout'

/*
const ITEM_CLASSES = ['grid-item--width2 grid-item--height2', 'grid-item--width2', 'grid-item--height2']

const randomInt = (min = 1, max = ITEM_CLASSES.length) => Math.floor(Math.random() * (max - min) + min)

const randItemClass = () => ITEM_CLASSES[randomInt()]

*/

export default {
  data() {
    return {
      items: [
        {
          src: 'https://s3-us-west-2.amazonaws.com/s.cdpn.io/82/orange-tree.jpg',
        },
        {
          src: 'https://s3-us-west-2.amazonaws.com/s.cdpn.io/82/submerged.jpg',
        },
        {
          src: 'https://s3-us-west-2.amazonaws.com/s.cdpn.io/82/look-out.jpg',
        },
        {
          src: 'https://s3-us-west-2.amazonaws.com/s.cdpn.io/82/one-world-trade.jpg',
        },
        {
          src: 'https://s3-us-west-2.amazonaws.com/s.cdpn.io/82/drizzle.jpg',
        },
        {
          src: 'https://s3-us-west-2.amazonaws.com/s.cdpn.io/82/cat-nose.jpg',
        },
        {
          src: 'https://s3-us-west-2.amazonaws.com/s.cdpn.io/82/contrail.jpg',
        },
        {
          src: 'https://s3-us-west-2.amazonaws.com/s.cdpn.io/82/golden-hour.jpg',
        },
        {
          src: 'https://s3-us-west-2.amazonaws.com/s.cdpn.io/82/flight-formation.jpg',
        },
      ],
    }
  },
  mounted() {
    this.$nextTick(() => this.layout())
  },
  updated() {
    this.layout()
  },
  methods: {
    /*
    addItem() {
      this.items.push({ classes: randItemClass() })
    },*/
    layout() {
      this._masonry = new Masonry(this.$refs.masonry, {
        itemSelector: '.grid-item',
        columnWidth: 100,
        percentPosition: true,
      })
    },
  },
}
</script>

<style scoped>
* {
  box-sizing: border-box;
}

/* force scrollbar */
html {
  overflow-y: scroll;
}

body {
  font-family: sans-serif;
}

/* ---- grid ---- */

.grid {
  background: #ddd;
}

/* clear fix */
.grid:after {
  content: '';
  display: block;
  clear: both;
}

/* ---- .grid-item ---- */

.grid-sizer,
.grid-item {
  width: 33.333%;
}

.grid-item {
  float: left;
}

.grid-item img {
  display: block;
  max-width: 100%;
}
</style>
