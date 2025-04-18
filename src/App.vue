<template>
  <div id="app">
    <Sidebar @update-settings="updateSettings" />
    <div id="main">
      <MainView
        :drones="drones"
        :groundStation="groundStation"
        @detect="handleDetect"
        @sendToGround="handleSendToGround"
      />
    </div>
  </div>
</template>

<script>
import Sidebar from "./components/Sidebar.vue";
import MainView from "./components/MainView.vue";

export default {
  name: "App",
  components: { Sidebar, MainView },
  data() {
    return {
      settings: {
        imagePath: "",
        yoloVersion: "v3",
      },
      drones: [
        { id: 1, name: "Drone 1", rawImage: null, processedImage: null },
        { id: 2, name: "Drone 2", rawImage: null, processedImage: null },
        { id: 3, name: "Drone 3", rawImage: null, processedImage: null },
      ],
      groundStation: {
        receivedImages: [],
      },
    };
  },
  methods: {
    updateSettings(settings) {
      this.settings = settings;
    },
    handleDetect(droneId) {
      const drone = this.drones.find((d) => d.id === droneId);
      drone.processedImage = `processed-${droneId}.jpg`; // 模拟检测逻辑
    },
    handleSendToGround(droneId) {
      const drone = this.drones.find((d) => d.id === droneId);
      if (drone.processedImage) {
        this.groundStation.receivedImages.push(drone.processedImage);
      }
    },
  },
};
</script>

<style>
#app {
  display: flex;
  height: 100vh;
}
#main {
  flex: 1;
  display: flex;
  flex-direction: column;
}
</style>