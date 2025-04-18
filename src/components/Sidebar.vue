<template>
  <div id="sidebar">
    <h3>设置选项</h3>
    <form @submit.prevent="updateSettings">
      <div class="form-row">
        <label for="image-path">识别图片路径:</label>
        <input
          id="image-path"
          v-model="imagePath"
          type="text"
          placeholder="输入图片路径"
        />
      </div>
      <div class="form-row">
        <label for="3D-house">三维模型库:</label>
        <input
          id="3d-house-path"
          v-model="ThousePath"
          type="text"
          placeholder="输入仓库路径"
        />
      </div>
      <div class="form-row">
        <label for="yolo-version">YOLO 模型版本:</label>
        <select id="yolo-version" v-model="yoloVersion">
          <option value="v8">YOLO v8</option>
          <option value="v9">YOLO v9</option>
          <option value="v10">YOLO v10</option>
          <option value="11">YOLO 11</option>
        </select>
      </div>
      <button type="submit">更新设置</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "Sidebar",
  data() {
    return {
      imagePath: "",
      yoloVersion: "v8",
    };
  },
  methods: {
    updateSettings() {
      this.$emit("update-settings", {
        imagePath: this.imagePath,
        yoloVersion: this.yoloVersion,
      });
    },
  },
};
</script>

<style>
#sidebar {
  width: 300px;
  background: #f4f4f4;
  padding: 20px;
}

form {
  display: flex;
  flex-direction: column;
  gap: 15px; /* 设置每行之间的间距 */
}

.form-row {
  display: flex;
  align-items: center; /* 垂直居中 */
  justify-content: space-between; /* 在两端对齐 */
}

label {
  width: 130px; /* 固定宽度 */
  text-align: left; /* 文本右对齐 */
  margin-right: 10px; /* 与输入框的间距 */
}

input,
select {
  flex: 1; /* 输入框占据剩余空间 */
  max-width: 150px; /* 设置输入框的固定宽度 */
  padding: 5px; /* 内边距 */
  box-sizing: border-box; /* 包括内边距和边框在宽度内 */
}

button {
  margin-top: 10px;
  padding: 5px 10px;
  cursor: pointer;
}
</style>