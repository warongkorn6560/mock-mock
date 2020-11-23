<template>
  <div>
    <div>
      <div>
        <canvas id="canvas" height="550" width="1440"></canvas>
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

    const ImgURL = new fabric.Image.fromURL("iconnetflix.png", function (
      urlImg
    ) {
      urlImg.scale(0.5).set("flipX", true);
      canvas.add(urlImg);
    });

    // canvas.add(rect).setActiveObject(rect);
  },
};
</script>

<style lang="scss" scoped>
#canvas {
  background-color: rgba(255, 255, 255, 0);
}
</style>