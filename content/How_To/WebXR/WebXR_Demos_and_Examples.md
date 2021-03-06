## Basic scene

This is a step-by-step guide on how to add XR features to a basic scene

### Basic Scene with XR Support

Here we just add an environment, a sphere, and XR support

``` javascript
const xrHelper = await scene.createDefaultXRExperienceAsync();
```

[Basic scene with XR support](https://playground.babylonjs.com/#9K3MRA)

### Adding teleportation

To get teleportation enabled, we want to provide the experience helper with an array of floor meshes:

``` javascript
const xrHelper = await scene.createDefaultXRExperienceAsync({
    // define floor meshes
    floorMeshes: [environment.ground]
});
```

[Basic example with teleportation](https://playground.babylonjs.com/#9K3MRA#1)

### Adding a color picker to the basic scene

Add a color picker (from our GUI library) and use it to change the sphere's color.

Notice that no changes were made in the XR code, and that the scene works perfectly well outside VR as well.

``` javascript
// GUI
var plane = BABYLON.Mesh.CreatePlane("plane", 1);
plane.position = new BABYLON.Vector3(1.4, 1.5, 0.4)
var advancedTexture = BABYLON.GUI.AdvancedDynamicTexture.CreateForMesh(plane);
var panel = new BABYLON.GUI.StackPanel();
advancedTexture.addControl(panel);
var header = new BABYLON.GUI.TextBlock();
header.text = "Color GUI";
header.height = "100px";
header.color = "white";
header.textHorizontalAlignment = BABYLON.GUI.Control.HORIZONTAL_ALIGNMENT_CENTER;
header.fontSize = "120"
panel.addControl(header);
var picker = new BABYLON.GUI.ColorPicker();
picker.value = sphere.material.diffuseColor;
picker.horizontalAlignment = BABYLON.GUI.Control.HORIZONTAL_ALIGNMENT_CENTER;
picker.height = "350px";
picker.width = "350px";
picker.onValueChangedObservable.add(function(value) {
    sphere.material.diffuseColor.copyFrom(value);
});
panel.addControl(picker);
```

[WebXR color picker](https://playground.babylonjs.com/#9K3MRA#2)

## Babylon.js scenes with XR support

* [Mansion](https://www.babylonjs-playground.com/#JA1ND3#161)
* [Hill Valley](https://www.babylonjs-playground.com/#JA1ND3#182)
* [Espilit](https://www.babylonjs-playground.com/#JA1ND3#164)
* [Skull-Pickup](https://playground.babylonjs.com/#ZNX043#15)
