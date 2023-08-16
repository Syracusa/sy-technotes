# Get direction vector from orientation
```js
function getDirection(orientation) {
    const direction =
        Cesium.Matrix3.multiplyByVector(
            Cesium.Matrix3.fromQuaternion(orientation),
            Cesium.Cartesian3.UNIT_X,
            new Cesium.Cartesian3());
    return direction;
}
```