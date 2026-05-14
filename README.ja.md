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

**gl-matrix** は、パフォーマンスが要求される WebGL アプリケーションで高速に動作するように設計された、JavaScript の行列およびベクトル演算ライブラリです。

## 特徴

*   **高いパフォーマンス:** パフォーマンスが重要となる状況に向けて最適化されています。
*   **包括的な数学演算:** ベクトル、行列、クォータニオンの幅広い演算をサポートします。
    *   `vec2`, `vec3`, `vec4`
    *   `mat2`, `mat2d`, `mat3`, `mat4`
    *   `quat`, `quat2` (デュアルクォータニオン)
*   **モダンな JavaScript:** ES6 モジュールとして配布されています。
*   **ツリーシェイキング対応:** 必要な関数のみをインポートできるため、バンドルサイズを最小限に抑えることができます。
*   **依存関係ゼロ:** 外部依存関係のない軽量なライブラリです。
*   **完全な型付け:** TypeScript の型定義が含まれています。

## インストール

npm を使用してインストールします:

```bash
npm install gl-matrix
```

## 使用方法

`gl-matrix` は効率性を重視して設計されており、ほとんどの関数は結果を専用の `out` パラメータに書き込みます。これにより、既存のオブジェクトを再利用し、不要なメモリ割り当てを避けることができます。

### ES モジュール (推奨)

必要な特定のモジュールをインポートします。これは、Webpack や Rollup などのバンドラーがライブラリを「ツリーシェイキング」し、最終的なバンドルサイズを小さくできるため、本番環境のアプリケーションにとって最適なアプローチです。

```javascript
import { mat4, vec3 } from 'gl-matrix';

// モデルビュー行列として mat4 を作成
const modelViewMatrix = mat4.create();

// 平行移動（Translate）
mat4.translate(modelViewMatrix,     // 出力先の行列
               modelViewMatrix,     // 平行移動する行列
               [-0.0, 0.0, -6.0]);  // 平行移動量

// スケーリング用の vec3 を作成
const scaleVector = vec3.fromValues(2, 2, 2);

// 行列をスケーリング
mat4.scale(modelViewMatrix, modelViewMatrix, scaleVector);
```

### ブラウザ (UMD ビルド)

ブラウザ上で直接 UMD ビルドを使用することもできます。グローバルな `glMatrix` オブジェクトが利用可能になります。

```html
<script src="node_modules/gl-matrix/dist/gl-matrix.js"></script>
<script>
  const { mat4, vec3 } = glMatrix;

  const matrix = mat4.create();
  mat4.rotate(matrix, matrix, Math.PI / 4, [0, 0, 1]);

  console.log(matrix);
</script>
```

## API ドキュメント

利用可能なすべての関数の完全なリストについては、**[API ドキュメント](http://glmatrix.net/docs/)** を参照してください。

## コントリビューター

*   **Brandon Jones** ([@toji](https://github.com/toji))
*   **Colin MacKenzie IV** ([@sinisterchipmunk](https://github.com/sinisterchipmunk))

## ライセンス

gl-matrix は **[MIT License](LICENSE)** のもとで公開されています。
