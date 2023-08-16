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

