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

# Get closest point in line from certain position
```js
function closestPointOnLine(onLinePos1, onLinePos2, position) {
    const v = Cesium.Cartesian3.subtract(onLinePos2, onLinePos1, new Cesium.Cartesian3());
    const w = Cesium.Cartesian3.subtract(position, onLinePos1, new Cesium.Cartesian3());
    const c1 = Cesium.Cartesian3.dot(w, v);
    const c2 = Cesium.Cartesian3.dot(v, v);
    const b = c1 / c2;
    const pb = Cesium.Cartesian3.multiplyByScalar(v, b, new Cesium.Cartesian3());
    const closestPoint = Cesium.Cartesian3.add(onLinePos1, pb, new Cesium.Cartesian3());
    return closestPoint;
}
```
