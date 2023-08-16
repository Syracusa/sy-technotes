# Disable all widget in cesiumJS
```js
const viewer = new Cesium.Viewer("cesiumContainer", {
    /* ... */
    animation: false,
    baseLayerPicker: false,
    fullscreenButton: false,
    vrButton: false,
    geocoder: false,
    homeButton: false,
    infoBox: false,
    sceneModePicker: false,
    selectionIndicator: false,
    timeline: false,
    navigationHelpButton: false,
    /* ... */
});

document.getElementById("cesiumContainer")
    .getElementsByClassName("cesium-viewer-bottom")
    .forEach((elem) => { elem.style.visibility = "hidden"; });
```

# 2D SceneMode
```js
const viewer = new Cesium.Viewer("cesiumContainer", {
    /* ... */
    sceneMode: Cesium.SceneMode.SCENE2D,
    /* ... */
});
```
