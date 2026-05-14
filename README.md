# gl-matrix

[
![npm version](https://img.shields.io/npm/v/gl-matrix.svg)
](https://www.npmjs.com/package/gl-matrix)
[
![Build Status](https://travis-ci.org/toji/gl-matrix.svg?branch=master)
](https://travis-ci.org/toji/gl-matrix)
[
![License](https://img.shields.io/npm/l/gl-matrix.svg)
](https://github.com/toji/gl-matrix/blob/master/LICENSE)

> 日本語のREADMEはこちらです: [README.ja.md](README.ja.md)

**gl-matrix** is a JavaScript matrix and vector library that is designed to perform well in high-performance WebGL applications.

## Features

*   **High Performance:** Optimized for situations where performance is critical.
*   **Comprehensive Math:** Supports a wide range of vector, matrix, and quaternion operations.
    *   `vec2`, `vec3`, `vec4`
    *   `mat2`, `mat2d`, `mat3`, `mat4`
    *   `quat`, `quat2` (Dual Quaternions)
*   **Modern JavaScript:** Distributed as ES6 modules.
*   **Tree-Shakable:** Import only the functions you need, minimizing your bundle size.
*   **Zero Dependencies:** A lightweight library with no external dependencies.
*   **Fully Typed:** Includes TypeScript definitions.

## Installation

Install via npm:

```bash
npm install gl-matrix
```

## Usage

`gl-matrix` is designed for efficiency, and as such, most functions write their results to a dedicated `out` parameter. This allows you to reuse existing objects and avoid unnecessary memory allocations.

### ES Modules (Recommended)

Import the specific modules you need. This is the best approach for production applications as it allows bundlers like Webpack or Rollup to "tree-shake" the library, resulting in a smaller final bundle.

```javascript
import { mat4, vec3 } from 'gl-matrix';

// Create a mat4 for our model-view matrix
const modelViewMatrix = mat4.create();

// Translate it
mat4.translate(modelViewMatrix,     // destination matrix
               modelViewMatrix,     // matrix to translate
               [-0.0, 0.0, -6.0]);  // amount to translate

// Create a vec3 for scaling
const scaleVector = vec3.fromValues(2, 2, 2);

// Scale the matrix
mat4.scale(modelViewMatrix, modelViewMatrix, scaleVector);
```

### Browser (UMD build)

You can also use the UMD build directly in the browser. A global `glMatrix` object will be available.

```html
<script src="node_modules/gl-matrix/dist/gl-matrix.js"></script>
<script>
  const { mat4, vec3 } = glMatrix;

  const matrix = mat4.create();
  mat4.rotate(matrix, matrix, Math.PI / 4, [0, 0, 1]);

  console.log(matrix);
</script>
```

## API Documentation

For a complete list of all available functions, see the **[API Documentation](http://glmatrix.net/docs/)**.

## Contributors

*   **Brandon Jones** ([@toji](https://github.com/toji))
*   **Colin MacKenzie IV** ([@sinisterchipmunk](https://github.com/sinisterchipmunk))

## License

gl-matrix is licensed under the **[MIT License](LICENSE)**.