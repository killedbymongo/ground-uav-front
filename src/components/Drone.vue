<template>
  <div class="drone">
    <!-- 将 drone-icon 替换为图片 -->
    <img
    class="drone-icon"
    :src="require('@/assets/uav.jpg')"
    alt="Drone Icon"
    @click="viewDrone"
    />
    <button @click="$emit('upload')">上传</button>
    <button @click="$emit('sendToGround')">发送到地面站</button>
  </div>
</template>

<script>
export default {
  name: "Drone",
  props: {
    drone: Object,
  },
  methods: {
    viewDrone() {
      alert(
        `查看无人机 ${this.drone.name} 的图片: ${this.drone.processedImage || "无"}`
      );
    },
  },
};
</script>

<style>
.drone {
  text-align: center;
}

.drone-icon {
  width: 50px; /* 设置图片宽度 */
  height: 50px; /* 设置图片高度 */
  border-radius: 50%; /* 让图片变成圆形 */
  margin: 10px auto;
  cursor: pointer;
  object-fit: cover; /* 保持图片比例，裁剪内容以填充空间 */
  display: block; /* 确保 img 居中 */
}
</style>