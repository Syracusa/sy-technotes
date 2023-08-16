# Make GLTF Entity in CesiumJS
## Static Position
```js
const longitude = 127.41;
const latitude = 34.19;
const height = 400;

const heading = Math.PI / 3;
const pitch = 0;
const roll = 0;

const hpr = new Cesium.HeadingPitchRoll(heading, pitch, roll);

const cartesianPosition = Cesium.Cartesian3.fromDegrees(longitude, latitude, height);
const orientation = Cesium.Transforms.headingPitchRollQuaternion(cartesianPosition, hpr);

const entity = viewer.entities.add({
    name: "test-entity",
    position: cartesianPosition,
    orientation: orientation,
    model: {
        uri: "./Model.glb",
        scale: 6
    }
});
```
## Updatable Position
```js

const entity = viewer.entities.add({
    /* ... */
    position: 
        new Cesium.CallbackProperty(function (time, result) {
            const cartesianPosition = Cesium.Cartesian3.fromDegrees(longitude, latitude, height);
            return cartesianPosition;
        }, false),
    orientation:
        new Cesium.CallbackProperty(function (time, result) {            
            const hpr = new Cesium.HeadingPitchRoll(heading, pitch, roll);
            const cartesianPosition = Cesium.Cartesian3.fromDegrees(longitude, latitude, height);
            const orientation = Cesium.Transforms.headingPitchRollQuaternion(cartesianPosition, hpr);
            return orientation;
        }, false),
    /* ... */
});
```

## Scenario based position
```js
const timedPostion = [
    ["2023-01-01T00:00:00Z", 127.23, 34.61, 100],
    ["2023-01-01T00:01:00Z", 127.25, 34.62, 150],
    ["2023-01-01T00:02:00Z", 127.27, 34.64, 200]
];
const positionProperty = new Cesium.SampledPositionProperty();
timedPostion.forEach((timedPos) => {
    const time = Cesium.JulianDate.fromIso8601(timedPos[0]);
    const pos = Cesium.Cartesian3.fromDegrees(timedPos[1], timedPos[2], timedPos[3]);
    positionProperty.addSample(time, pos);
});

const entity = viewer.entities.add({
    /* ... */
    position: positionProperty,
    orientation: new Cesium.VelocityOrientationProperty(positionProperty),
    /* ... */
});
```

## Delete Entity
```js
viewer.entities.remove(entity);
```

## Toggle Visibility
```js
entity.show = !entity.show;
```

## Add Label
```js
const entity = viewer.entities.add({
    /* ... */
    description: '<div> Entity Description Test </div>'
    /* ... */
});
```


# Make Pillar Entity
```js
function createPillar(viewer, lon, lat, height, fromGround, radius, color, alpha) {

const longitude = 127.12; 
const latitude = 34.34;
const height = 1000;
const fromGround = 100;
const radius = 1000;
const color = Cesium.Color.fromCssColorString('#123456');
const alpha = 0.5;

const entity = viewer.entities.add({
    position: Cesium.Cartesian3.fromDegrees(
        longitude, latitude, height / 2 + fromGround),
    cylinder: {
        length: height,
        topRadius: radius,
        bottomRadius: radius,
        material: color.withAlpha(alpha),
    },
});

```

# Line Between Two Position
```js
const p1 = Cesium.Cartesian3.fromDegrees(longitude1, latitude1, height1);
const p2 = Cesium.Cartesian3.fromDegrees(longitude2, latitude2, height2);
const color = Cesium.Color.RED.withAlpha(0.5);
const width = 5;

const polyline = viewer.entities.add({
    polyline: {
        positions: [p1, p2],
        width: width,
        material: color,
    }
});
```