<template>
  <div id="ground-station">
    <h3>地面站</h3>
    <div v-if="receivedImages.length === 0">暂无接收图片</div>
    <div v-else>
      <div
        class="received-image"
        v-for="(image, index) in receivedImages"
        :key="index"
      >
        <img :src="image" :alt="'Received ' + index" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "GroundStation",
  props: {
    receivedImages: Array,
  },
};
</script>

<style>
#ground-station {
  width: 200px;
}
.received-image img {
  width: 100px;
  margin: 5px;
}
</style>