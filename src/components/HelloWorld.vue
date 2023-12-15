<template>
  <v-stage :config="configKonva">
    <v-layer>
      <v-rect
        :config="configRect"
        @mouseenter="showRects()">
      </v-rect>
    </v-layer>
    <v-layer
      ref="layer"
      @mouseout="delRects()"></v-layer>
  </v-stage>
</template>

<script>
import Konva from 'konva';

var width = 800;
var height = 800;

export default {
  data() {
    return {
      layer: null,
      configKonva: {
        width: width,
        height: height,
      },
      configRect: {
        x: width / 2,
        y: height / 2,
        width: width / 3,
        height: height / 3,
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
      rects: '',
    };
  },
  methods: {
    showRects() {
      let group = new Konva.Group({
        clip: {
          x: this.configRect.x,
          y: this.configRect.y,
          width: this.configRect.width,
          height: this.configRect.height,
        },
      });
      for (
        let i = 0;
        i * this.layeredRect.height < this.configRect.height;
        i++
      ) {
        let y = i * this.layeredRect.height;
        for (
          let j = 0;
          j * this.layeredRect.width < this.configRect.width;
          j++
        ) {
          let x = j * this.layeredRect.width;
          let rect = new Konva.Rect({
            x: this.configRect.x + x,
            y: this.configRect.y + y,
            width: this.layeredRect.width,
            height: this.layeredRect.height,
            fill: 'blue',
            stroke: 'black',
            strokeWidth: 4,
          });
          group.add(rect);
        }
      }
      this.layer.add(group);
    },
    delRects() {
      this.layer.destroyChildren();
    },
  },
  mounted() {
    this.layer = this.$refs.layer.getNode();
  },
};
</script>
