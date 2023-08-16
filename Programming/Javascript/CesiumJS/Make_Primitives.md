# Create Primitives
+ Create Pillar Primitive
```js
const longitude = 127.12;
const latitude = 127.34;

const height = 1000;
const topRadius = 500;
const bottomRadius = 500;
const slices = 64;

const fromGround = 100;

const color = Cesium.Color.fromCssColorString('#123456');
const alpha = 0.5;

const pillarGeometry = new Cesium.CylinderGeometry({
    length: height,
    topRadius: topRadius,
    bottomRadius: bottomRadius,
    slices: slices,
    vertexFormat: Cesium.PerInstanceColorAppearance.VERTEX_FORMAT
});

const pillarGeometryInstance = new Cesium.GeometryInstance({
    geometry: pillarGeometry,
    modelMatrix: Cesium.Transforms.eastNorthUpToFixedFrame(
        Cesium.Cartesian3.fromDegrees(longitude, latitude, fromGround + height / 2)),
    attributes: {
        color: Cesium.ColorGeometryInstanceAttribute.fromColor(
            color.withAlpha(alpha)),
    },
}); 

const pillarPrimitive = new Cesium.Primitive({
    geometryInstances: pillarGeometryInstance,
    appearance: new Cesium.PerInstanceColorAppearance(),
    allowPicking: false,
    asynchronous: false,
});

viewer.scene.primitives.add(pillarPrimitive);
```


+ Create PolylineVolume Primitive
  + Rectangle Volume
```js
const degreeHeightArr = [
    127.23, 34.61, 100,
    127.25, 34.62, 150,
    127.27, 34.64, 200,
];
const cartesianPositionArr = Cesium.Cartesian3.fromDegreesArrayHeights(degreeHeightArr);

const thickness = 50;   /* Path Thickness */
const polylineVolumeGeometry = new Cesium.PolylineVolumeGeometry({
    vertexFormat: Cesium.PolylineVolumeGeometry.VERTEX_FORMAT,
    polylinePositions: cartesianPositionArr,
    shapePositions: [
        new Cesium.Cartesian2(-thickness, -thickness),
        new Cesium.Cartesian2(thickness, -thickness),
        new Cesium.Cartesian2(thickness, thickness),
        new Cesium.Cartesian2(-thickness, thickness),
    ]
});

const polylineGeometryInstance = new Cesium.GeometryInstance({
    geometry: volume,
    attributes: {
        color: Cesium.ColorGeometryInstanceAttribute.fromColor(color)
    }
});

const polylinePrimitive = viewer.scene.primitives.add(new Cesium.Primitive({
    geometryInstances: [polylineGeometryInstance],
    appearance: new Cesium.PerInstanceColorAppearance(),
    allowPicking: false
}));

```

# Delete Primitives
```js
viewr.scene.primitives.remove(primitive);
```
