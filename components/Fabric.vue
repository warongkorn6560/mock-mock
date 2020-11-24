<template>
  <div>
    <div>
      <div>
        <canvas id="canvas" height="550" width="1440"></canvas>
        {{ test() }}
      </div>
    </div>
  </div>
</template>

<script>
// import { fabric } from "fabric";
export default {
  data: () => ({
    canvas: null,
    imgURL: null,
    imgInside: null,
  }),
  props: {
    selectedFrame: {
      type: String,
      default: "ipad-pro-landscape.webp",
    },
    addURL: {
      type: String,
      default: "",
    },
  },
  watch: {
    selectedFrame: {
      handler() {
        this.imgURL = new fabric.Image.fromURL(this.selectedFrame, (urlImg) => {
          this.canvas.clear(urlImg);
          urlImg

            .scaleToHeight(this.canvas.getHeight() * 0.9)
            .setPositionByOrigin(
              {
                x: this.canvas.getWidth() / 2,
                y: this.canvas.getHeight() / 2,
              },
              "center",
              "center"
            );
          this.canvas.add(urlImg);
          // console.log(this.canvas);
        });
        this.imgInside = new fabric.Image.fromURL(this.addURL, (urlImg) => {
          urlImg
            .set({
              id: "unsplash",
            })
            .scaleToHeight(this.canvas.getHeight() * 0.9)
            .setPositionByOrigin(
              {
                x: this.canvas.getWidth() / 2,
                y: this.canvas.getHeight() / 2,
              },
              "center",
              "center"
            );

          this.canvas.add(urlImg);
          this.canvas.sendToBack(urlImg);
          const unsplash = this.canvas
            .getObjects()
            .find((x) => x.id === "unsplash");
          console.log(unsplash);
          unsplash.transformMatrix = [1, 0, 0, 1, 0, 0];
        });
      },
    },
  },
  mounted() {
    this.canvas = new fabric.Canvas("canvas");

    // const rect = new fabric.Rect({
    //   left: 150,
    //   top: 200,
    //   originX: "left",
    //   originY: "top",
    //   width: 150,
    //   height: 120,
    //   angle: -10,
    //   fill: "rgba(255,0,0,0.5)",
    //   transparentCorners: false,
    // });

    // canvas.add(rect).setActiveObject(rect);
  },
  methods: {
    test() {
      console.log(this.selectedFrame);
    },
  },
};
</script>

<style lang="scss" scoped>
</style>