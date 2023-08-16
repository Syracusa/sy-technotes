# Get longitude and latitude of mouse position
```js
new Cesium.ScreenSpaceEventHandler(viewer.canvas)
    .setInputAction((movement) => {
        const cartesian = viewer.camera.pickEllipsoid(
            new Cesium.Cartesian3(
                movement.endPosition.x,
                movement.endPosition.y),
            viewer.scene.globe.ellipsoid);

        if (!cartesian)
            return;

        const cartographic = this.globe.ellipsoid.cartesianToCartographic(cartesian);
        console.log(Cesium.Math.toDegrees(cartographic.longitude));
        console.log(Cesium.Math.toDegrees(cartographic.latitude));
    }, Cesium.ScreenSpaceEventType.MOUSE_MOVE);
```

# Screen Click
```js
new Cesium.ScreenSpaceEventHandler(viewer.canvas)
    .setInputAction((e) => {
        console.log(e.position.x, e.position.y);
    }, Cesium.ScreenSpaceEventType.LEFT_CLICK);
```

# Tick Handler
```js
viewer.clockViewModel.clock.onTick.addEventListener(
    (clock) => { /* Write your own callback */ }
);
```

# Override default home button callback
```js
viewer.homeButton.viewModel.command.beforeExecute.addEventListener(
    function (e) {
        e.cancel = true; /* Cancel default */
        /* Write your own callback below */  
        // ...
    }
);
```