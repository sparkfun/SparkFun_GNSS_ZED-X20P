3d_model directory
====================
This folder should contain the 3D model of the product

## Solder Mask - Color Correction Values
Hex: #E0311D
RGB: 224, 49, 29


## File Optimizer
https://glb.babylonpress.org/

- Enable these options
    - `Simplify | MeshoptSimplifier`
    - `Quantize | KHR_mesh_quantization`
    - `Use UASTC Zstandard Supercompression`
- Set these options, to the following values:
    - `ETC1S Quality Level (255 = best)`: 73
    - `ETC1S Compression Level (0 = fastest)`: 5

### VS Code Extension
To reorder the materials for the rendering, use the [GlTF Tools extension](https://marketplace.visualstudio.com/items?itemName=cesium.gltf-vscode) in VS Code

- https://marketplace.visualstudio.com/items?itemName=cesium.gltf-vscode
- https://github.com/AnalyticalGraphicsInc/gltf-vscode


## Model Editor
https://modelviewer.dev/editor/



## Old Methods

### File Converter - `*.wrl` to `*.glb`
https://imagetostl.com/convert/file/wrl/to/glb#convert

### Solder Mask - Color Correction
Open `*.glb` file and locate the `baseColorFactor` parameter with the following values:
```
          0.7027450799942017,
          0.1537254899740219,
          0.0909803956747055,
          0.8313725590705872
```
Replace those values with the following values: `[,,,1]`
```
          0.7418950796127319,
          0.0302486829459667,
          0.0122311776503920,
          1
```

### Solder Mask - Color Correction
https://3deditoronline.com/

### 1st File Optimizer *(Deprecated)*
https://www.loci-labs.com/optimizer

### 2nd File Optimizer *(Deprecated)*
https://xiehangyun.github.io/gltf-optimization/

- Max Texture Size: 512
- Create Unified Palette Texture for Solid Colors and Merge: *(Unselect)*