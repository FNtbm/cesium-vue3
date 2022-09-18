<script setup>
import * as Cesium from "cesium";
import "cesium/Build/Cesium/Widgets/widgets.css";

window.CESIUM_BASE_URL = "/src/assets";

const KEY =
  "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJqdGkiOiJmM2FiYzA4OS04MWIyLTQyNGYtOWIxMy1iM2E1ZmNjNzVhMGYiLCJpZCI6MTA4MzIxLCJpYXQiOjE2NjM0MDgyNjl9.vO4ecGWpvhHYYtGiHi9VaV4j4KZoqPXYvigWcXckGJY";
Cesium.Ion.defaultAccessToken = KEY;

onMounted(() => {
  const viewer = new Cesium.Viewer("container", {
    terrainProvider: Cesium.createWorldTerrain(),
  });
  // Add Cesium OSM Buildings, a global 3D buildings layer.
  viewer.scene.primitives.add(Cesium.createOsmBuildings());
  // Fly the camera to San Francisco at the given longitude, latitude, and height.
  viewer.camera.flyTo({
    destination: Cesium.Cartesian3.fromDegrees(-122.4175, 37.655, 400),
    orientation: {
      heading: Cesium.Math.toRadians(0.0),
      pitch: Cesium.Math.toRadians(-15.0),
    },
  });
});
</script>

<template>
  <div id="container"></div>
</template>
<style scoped>
#container {
  height: 80vh;
  width: 80vw;
}
</style>
