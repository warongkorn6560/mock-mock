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
    patternA: null,
    patternB: null,
    patternC: null,
    patternD: null,
    patternE: null,
    patternF: null,
    patternG: null,
    patternH: null,
    patternI: null,
    patternJ: null,
  }),
  props: {
    selectedFrame: {
      type: String,
      default: "iphone-x-2-scr.webp",
    },
    addURL: {
      type: String,
      default: "",
    },
    selectedFrameIndex: {
      type: Number,
      default: null,
    },
  },
  watch: {
    selectedFrame: {
      immediate: true,
      handler() {
        if (!process.client) return;
        if (!this.canvas) return;
        this.imgURL = new fabric.Image.fromURL(this.selectedFrame, (urlImg) => {
          // this.canvas.clear(urlImg);
          // urlImg.lockMovementY = true;
          // urlImg.lockRotation = true;
          // urlImg.lockScalingX = true;
          // urlImg.lockScalingY = true;
          // urlImg.hasControls = false;
          urlImg.selectable = false;
          urlImg.hoverCursor = "crosshair";
          urlImg.perPixelTargetFind = true;
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
          this.canvas.sendToBack(urlImg);
          this.canvas.add(urlImg);
        });

        // Pattern
        this.canvas.clear();
        if (this.selectedFrameIndex === 0) {
          this.patternA = new fabric.Polygon(
            [
              { x: 418, y: 42 },
              { x: 1022, y: 42 },
              { x: 1022, y: 510 },
              { x: 418, y: 510 },
            ],
            {
              fill: "orange",
            }
          );
          this.canvas.add(this.patternA);
          addPattern(this.patternA);
          this.patternA.selectable = false;
          this.patternA.hoverCursor = "crosshair";
        }
        if (this.selectedFrameIndex === 1) {
          this.patternB = new fabric.Polygon(
            [
              { x: 485, y: 35 },
              { x: 1030, y: 80 },
              { x: 890, y: 420 },
              { x: 310, y: 340 },
            ],
            {
              fill: "yellow",
            }
          );
          this.canvas.add(this.patternB);
          addPattern(this.patternB);
          this.patternB.selectable = false;
          this.patternB.hoverCursor = "crosshair";
        }
        if (this.selectedFrameIndex === 2) {
          this.patternC = new fabric.Polygon(
            [
              { x: 549, y: 190 },
              { x: 555, y: 182 },
              { x: 675, y: 162 },
              { x: 685, y: 175 },
              { x: 768, y: 475 },
              { x: 750, y: 495 },
              { x: 645, y: 518 },
              { x: 638, y: 510 },
            ],
            {
              fill: "yellow",
            }
          );
          this.canvas.add(this.patternC);
          addPattern(this.patternC);
          this.patternC.selectable = false;
          this.patternC.hoverCursor = "crosshair";
          this.patternD = new fabric.Polygon(
            [
              { x: 768, y: 38 },
              { x: 778, y: 32 },
              { x: 880, y: 42 },
              { x: 885, y: 55 },
              { x: 800, y: 380 },
              { x: 785, y: 388 },
              { x: 742, y: 380 },
              { x: 710, y: 260 },
            ],
            {
              fill: "yellow",
            }
          );
          this.canvas.add(this.patternD);
          addPattern(this.patternD);
          this.patternD.selectable = false;
          this.patternD.hoverCursor = "crosshair";
        }
        if (this.selectedFrameIndex === 3) {
          this.patternE = new fabric.Polygon(
            [
              { x: 750, y: 38 },
              { x: 778, y: 32 },
              { x: 920, y: 70 },
              { x: 930, y: 90 },
              { x: 680, y: 510 },
              { x: 665, y: 512 },
              { x: 520, y: 450 },
              { x: 510, y: 430 },
            ],
            {
              fill: "red",
            }
          );
          this.canvas.add(this.patternE);
          addPattern(this.patternE);
          this.patternE.selectable = false;
          this.patternE.hoverCursor = "crosshair";
        }
        if (this.selectedFrameIndex === 4) {
          this.patternF = new fabric.Polygon(
            [
              { x: 610, y: 45 },
              { x: 620, y: 38 },
              { x: 810, y: 38 },
              { x: 830, y: 50 },
              { x: 830, y: 500 },
              { x: 820, y: 512 },
              { x: 625, y: 512 },
              { x: 610, y: 500 },
            ],
            {
              fill: "red",
            }
          );
          this.canvas.add(this.patternF);
          addPattern(this.patternF);
          this.patternF.selectable = false;
          this.patternF.hoverCursor = "crosshair";
        }
        if (this.selectedFrameIndex === 5) {
          this.patternG = new fabric.Polygon(
            [
              { x: 460, y: 115 },
              { x: 465, y: 102 },
              { x: 620, y: 35 },
              { x: 643, y: 32 },
              { x: 662, y: 45 },
              { x: 967, y: 350 },
              { x: 960, y: 370 },
              { x: 790, y: 460 },
            ],
            {
              fill: "red",
            }
          );
          this.canvas.add(this.patternG);
          addPattern(this.patternG);
          this.patternG.selectable = false;
          this.patternG.hoverCursor = "crosshair";
        }
        if (this.selectedFrameIndex === 6) {
          this.patternH = new fabric.Polygon(
            [
              { x: 707, y: 72 },
              { x: 720, y: 62 },
              { x: 880, y: 50 },
              { x: 900, y: 60 },
              { x: 720, y: 460 },
              { x: 549, y: 450 },
              { x: 535, y: 438 },
            ],
            {
              fill: "red",
            }
          );
          this.canvas.add(this.patternH);
          addPattern(this.patternH);
          this.patternH.selectable = false;
          this.patternH.hoverCursor = "crosshair";
        }
        if (this.selectedFrameIndex === 7) {
          this.patternI = new fabric.Polygon(
            [
              { x: 250, y: 60 },
              { x: 970, y: 60 },
              { x: 970, y: 470 },
              { x: 250, y: 470 },
            ],
            {
              fill: "red",
            }
          );
          this.canvas.add(this.patternI);
          addPattern(this.patternI);
          this.patternI.selectable = false;
          this.patternI.hoverCursor = "crosshair";

          this.patternJ = new fabric.Polygon(
            [
              { x: 1040, y: 125 },
              { x: 1212, y: 125 },
              { x: 1212, y: 495 },
              { x: 1040, y: 495 },
            ],
            {
              fill: "yellow",
            }
          );
          this.canvas.add(this.patternJ);
          addPattern(this.patternJ);
          this.patternJ.selectable = false;
          this.patternJ.hoverCursor = "crosshair";
        }

        function addPattern(obj) {
          fabric.util.loadImage("testImg.png", function (img) {
            img.selectable = false;
            obj.fill = new fabric.Pattern({
              source: img,
              repeat: "repeat",
              object: "scaling",
            });
            this.canvas.add(img);
          });
        }
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

          unsplash.transformMatrix = [1, 0.4, -0.6, 1, 0, 0];
        });
      },
    },
  },
  mounted() {
    this.canvas = new fabric.Canvas("canvas", {
      isDrawingMode: true,
      // backgroundColor: "green",
    });

    this.canvas.freeDrawingBrush.width = 10;

    // let frame1 = new fabric.Image.fromURL("pixel-duo.webp", (urlImg) => {
    //   urlImg.selectable = false;
    //   urlImg.scaleToHeight(this.canvas.getHeight() * 0.9).setPositionByOrigin(
    //     {
    //       x: this.canvas.getWidth() / 2,
    //       y: this.canvas.getHeight() / 2,
    //     },
    //     "center",
    //     "center"
    //   );

    //   this.canvas.add(urlImg);
    //   this.canvas.sendToBack(urlImg);
    // });
    // this.patternA = new fabric.Polygon(
    //   [
    //     { x: 1040, y: 125 },
    //     { x: 1212, y: 125 },
    //     { x: 1212, y: 495 },
    //     { x: 1040, y: 495 },
    //   ],
    //   {
    //     fill: "blue",
    //   }
    // );
    // this.canvas.add(this.patternA);

    // let patternA = new fabric.Polygon(
    //   [
    //     { x: 485, y: 35 },
    //     { x: 1030, y: 80 },
    //     { x: 890, y: 420 },
    //     { x: 310, y: 340 },
    //   ],
    //   {
    //     fill: "yellow",
    //   }
    // );
    // this.canvas.sendToBack(patternA);
    // this.canvas.add(patternA);
    // addPattern(patternA);

    // let square = new fabric.Rect({
    //   left: 180,
    //   top: 140,
    //   fill: "blue",
    //   width: 400,
    //   height: 400,
    // });
    // this.canvas.add(square);
    // addPattern(square);

    // function addPattern(obj) {
    //   fabric.util.loadImage(
    //     "https://images.unsplash.com/photo-1606122299879-e10b54a6d32f?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=634&q=80",
    //     function (img) {
    //       obj.fill = new fabric.Pattern({
    //         source: img,
    //         repeat: "repeat",
    //         object: "scaling",
    //       });
    //       this.canvas.renderAll();
    //     }
    //   );
    // }

    // let Rect = new fabric.Rect({ width: 100, height: 100, fill: "green" });
    // this.canvas.add(Rect);

    // let Iii = new fabric.Image.fromURL("iphone-xr-right.webp", function (img) {
    //   this.canvas.add(img);
    // });

    //  let Iii = new fabric.Image.fromURL("iphone-xr-right.webp", (img) => {
    //   this.canvas.add(img);
    // });

    // console.log(fabric.util.qrDecompose(matrix));
    // console.log(fabric.Object.prototype.calcTransformMatrix(this.imgURL));

    // fabric.Object.prototype.lockMovementY = true;

    // this.canvas.on("after:render", function (img) {
    //   this.canvas.clear();
    // });

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