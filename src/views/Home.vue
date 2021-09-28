<template>
  <div class="home">
    <button @click="enableEyeDropper">スポイト</button>
    <div class="color">
      <div class="preview" :style="{ background: color }"></div>
      <p>color: {{ color }}</p>
    </div>
    <div class="images">
      <img src="@/assets/photo1.jpg" height="800" />
      <img src="@/assets/photo2.jpg" height="800" />
      <img src="@/assets/photo3.jpg" height="800" />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";

export default defineComponent({
  name: "Home",
  setup() {
    const color = ref();
    const enableEyeDropper = async () => {
      // eslint-disable-next-line @typescript-eslint/ban-ts-comment
      // @ts-ignore
      const { sRGBHex } = await new EyeDropper().open();
      console.log(sRGBHex);
      color.value = sRGBHex;
    };
    return {
      enableEyeDropper,
      color,
    };
  },
});
</script>

<style>
.home {
  display: flex;
  flex-flow: column;
  gap: 20px;
  justify-content: center;
  align-items: center;
}
.color {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 10px;
}
.preview {
  width: 30px;
  height: 30px;
  border-radius: 4px;
  border: 1px solid #aaa;
  background: #ffffff;
}
.images {
  display: flex;
  flex-flow: row;
  justify-content: center;
  align-items: center;
  gap: 40px;
}
</style>
