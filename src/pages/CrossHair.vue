<template>
  <q-page padding class="flex flex-center">
    <div class="row q-col-gutter-md">
      <div class="col-12 col-md-6">
        <q-card style="min-width: 500px;">
          <q-card-section>
            <q-list>
              <q-item-section>
                <div class="text-h6 text-center q-pb-md">偏好设置</div>
              </q-item-section>
              <q-item-section>
                <q-input
                  v-model.number="defaultWidth"
                  type="number"
                  filled
                  label="宽度"
                />
              </q-item-section>
              <q-item-section>
                <q-input
                  v-model.number="defaultHeight"
                  type="number"
                  filled
                  label="高度"
                  class="q-mt-md"
                />
              </q-item-section>
              <q-item-section>
                <q-input
                  v-model.number="hidpi"
                  type="number"
                  filled
                  label="HiDPI"
                  class="q-mt-md"
                />
              </q-item-section>
              <q-item-section>
                <q-slider
                  class="q-mt-lg"
                  label-always
                  :label-value="'长度：' + size"
                  v-model="size"
                  :min="0"
                  :max="128"
                />
              </q-item-section>
              <q-item-section>
                <q-slider
                  class="q-mt-md"
                  label-always
                  :label-value="'线宽：' + lineWidth"
                  v-model="lineWidth"
                  :min="0"
                  :max="64"
                />
              </q-item-section>
              <q-item-section>
                <q-slider
                  class="q-mt-md"
                  label-always
                  :label-value="'间隙：' + gap"
                  v-model="gap"
                  :min="0"
                  :max="64"
                />
              </q-item-section>
              <q-item-section>
                <q-slider
                  class="q-mt-md"
                  label-always
                  :label-value="'透明度：' + alpha"
                  v-model="alpha"
                  :min="0"
                  :max="255"
                />
              </q-item-section>
              <q-item-section>
                <q-slider
                  class="q-mt-md"
                  label-always
                  :label-value="'R：' + r"
                  v-model="r"
                  :min="0"
                  :max="255"
                />
              </q-item-section>
              <q-item-section>
                <q-slider
                  class="q-mt-md"
                  label-always
                  :label-value="'G：' + g"
                  v-model="g"
                  :min="0"
                  :max="255"
                />
              </q-item-section>
              <q-item-section>
                <q-slider
                  class="q-mt-md"
                  label-always
                  :label-value="'B：' + b"
                  v-model="b"
                  :min="0"
                  :max="255"
                />
              </q-item-section>
              <div class="flex flex-center">
                <q-btn
                  color="primary"
                  label="生成"
                  class="text-center"
                  @click="generate"
                />
              </div>
            </q-list>
          </q-card-section>
        </q-card>
      </div>
      <div class="col-12 col-md-6">
        <q-card style="min-width: 500px;">
          <q-card-section>
            <div class="text-h6 text-center">预览</div>
            <div class="flex flex-center">
              <svg
                version="1.1"
                xmlns="http://www.w3.org/2000/svg"
                width="300px"
                height="200px"
              >
                <path
                  :d="
                    'M' +
                      (150 - gap / 2) +
                      ' ' +
                      100 +
                      ' L' +
                      (150 - gap / 2 - size) +
                      ' ' +
                      100 +
                      ' ' +
                      'M' +
                      (150 + gap / 2) +
                      ' ' +
                      100 +
                      ' L' +
                      (150 + gap / 2 + size) +
                      ' ' +
                      100 +
                      ' ' +
                      'M' +
                      150 +
                      ' ' +
                      (100 - gap / 2) +
                      ' L' +
                      150 +
                      ' ' +
                      (100 - gap / 2 - size) +
                      ' ' +
                      'M' +
                      150 +
                      ' ' +
                      (100 + gap / 2) +
                      ' L' +
                      150 +
                      ' ' +
                      (100 + gap / 2 + size)
                  "
                  fill="none"
                  :stroke-width="lineWidth"
                  :stroke="'rgba(' + r + ',' + g + ',' + b + ',' + alpha + ')'"
                />
              </svg>
            </div>
          </q-card-section>
        </q-card>
      </div>
    </div>
    <div
      id="Crosshair"
      v-show="generating"
      :style="'width:' + defaultWidth + 'px;height:' + defaultHeight + 'px;clear:both'"
    >
      <svg
        version="1.1"
        xmlns="http://www.w3.org/2000/svg"
        :width="defaultWidth + 'px'"
        :height="defaultHeight + 'px'"
      >
        <path
          :d="
            'M' +
              (defaultWidth / 2 - gap / 2) +
              ' ' +
              defaultHeight / 2 +
              ' L' +
              (defaultWidth / 2 - gap / 2 - size) +
              ' ' +
              defaultHeight / 2 +
              ' ' +
              'M' +
              (defaultWidth / 2 + gap / 2) +
              ' ' +
              defaultHeight / 2 +
              ' L' +
              (defaultWidth / 2 + gap / 2 + size) +
              ' ' +
              defaultHeight / 2 +
              ' ' +
              'M' +
              defaultWidth / 2 +
              ' ' +
              (defaultHeight / 2 - gap / 2) +
              ' L' +
              defaultWidth / 2 +
              ' ' +
              (defaultHeight / 2 - gap / 2 - size) +
              ' ' +
              'M' +
              defaultWidth / 2 +
              ' ' +
              (defaultHeight / 2 + gap / 2) +
              ' L' +
              defaultWidth / 2 +
              ' ' +
              (defaultHeight / 2 + gap / 2 + size)
          "
          fill="none"
          :stroke-width="lineWidth"
          :stroke="'rgb(' + r + ',' + g + ',' + b + ')'"
          :opacity="alpha"
        />
      </svg>
    </div>
  </q-page>
</template>

<script>
import html2canvas from "html2canvas";

export default {
  name: "CrossHair",
  data() {
    return {
      defaultHeight: 1080,
      defaultWidth: 1920,
      size: 8,
      lineWidth: 2,
      gap: 6,
      outline: 0,
      alpha: 255,
      r: 0,
      g: 255,
      b: 0,
      hidpi: 1,
      generating: false
    };
  },
  methods: {
    generate() {
      // 先显示outputDiv，再延迟50ms生成图片
      this.generating = true;
      setTimeout(this.html2canvas, 50);
    },
    html2canvas() {
      // html2canvas获取元素、生成图片、并跳转下载
      const e = document.getElementById("Crosshair");
      // 滚动条置顶解决生成图片不全的问题
      window.pageYOffset = 0;
      document.documentElement.scrollTop = 0;
      document.documentElement.scrollLeft = 0;
      document.body.scrollTop = 0;

      const hidpi = this.hidpi; // 缩放倍率，不随浏览器缩放改变
      html2canvas(e, {
        allowTaint: false,
        useCORS: false,
        backgroundColor: "rgba(0,0,0,0)",
        scale: hidpi
      }).then(canvas => {
        const dataURL = canvas.toDataURL("image/png");
        this.imgUrl = dataURL;
        if (this.imgUrl !== "") {
          const link = document.createElement("a");
          const context = canvas.getContext("2d");
          // [重要]关闭抗锯齿
          context.mozImageSmoothingEnabled = false;
          context.webkitImageSmoothingEnabled = false;
          context.msImageSmoothingEnabled = false;
          context.imageSmoothingEnabled = false;
          link.href = canvas.toDataURL();
          // !文件名设置
          link.setAttribute("download", "准星生成.png");
          link.style.display = "none";
          document.body.appendChild(link);
          link.click();

          this.generating = false;
        }
      });
    }
  },
  beforeDestroy () {
    if (this.timer !== void 0) {
      clearTimeout(this.timer)
      this.$q.loading.hide()
    }
  }
};
</script>

<style scoped>
#Crosshair {
  background-color: rgba(0, 0, 0, 0);
}
</style>
