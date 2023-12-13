<template>
  <v-stage :config="configKonva">
    <v-layer>
      <v-rect
        @mouseover="fillWithRects"
        :config="configRect">
      </v-rect>
    </v-layer>
    <v-layer :id="insideRect"> </v-layer>
  </v-stage>
</template>

<script>
var width = 800;
var height = 800;

export default {
  data() {
    return {
      insideRect: '#insideRect',
      configKonva: {
        width: width,
        height: height,
      },
      configRect: {
        x: width / 2,
        y: height / 2,
        width: width / 2,
        height: height / 2,
        fill: 'red',
        stroke: 'black',
        strokeWidth: 4,
      },
      layeredRect: {
        x: 0,
        y: 0,
        width: 100,
        height: 50,
        fill: 'blue',
        stroke: 'black',
        strokeWidth: 4,
      },
    };
  },
  methods: {
    fillWithRects() {
      console.log('hello');
      /*  for (
        let j = 0;
        j * this.layeredRect.height < this.configRect.height;
        j++
      ) {
        for (
          let i = 0;
          i * this.layeredRect.width < this.configRect.width;
          i++
        ) {
          this.$refs.insideRect.innerHTML += `<v-rect :config={
          x: ${100 * i},
          y: ${100 * j},
          width: 100,
          height: 50,
          fill: 'blue',
          stroke: 'black',
          strokeWidth: 4,
        }`;
        }
      } */
    },
  },
};
</script>
