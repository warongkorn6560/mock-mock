<template>
  <div>
    <div>
      <div>
        <canvas id="canvas" height="720" width="960"></canvas>
        <input value="Save as" type="button" id="save" @click="saveAs()" />
      </div>
    </div>
  </div>
</template>

<script>
// import { fabric } from "fabric";
export default {
  mounted() {
    const canvas = new fabric.Canvas("canvas");
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

    const ImgURL = new fabric.Image.fromURL(
      "https://images.unsplash.com/photo-1503614418835-dc720bf59271?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=633&q=80",
      function (urlImg) {
        urlImg.scale(0.5).set("flipX", true);
        canvas.add(urlImg);
      }
    );

    // canvas.add(rect).setActiveObject(rect);
  },
  methods: {
    saveAs() {
      const canvas = document.getElementById("canvas");
      canvas.toBlob(function (blob) {
        saveAs(blob, "mock-mock.png");
      });
    },
  },
};
</script>

<style lang="scss" scoped>
#canvas {
  background-color: rgba(128, 128, 128, 0.027);
}
</style>