---
id: version-0.61-transforms
title: Transforms
original_id: transforms
---

##### 本文档贡献者：[sunnylqm](https://github.com/search?q=sunnylqm%40qq.com+in%3Aemail&type=Users)(100.00%)

# 文档

## 方法

### `decomposedMatrix`

Deprecated. Use the transform prop instead.

| 类型                     | 必填 |
| ------------------------ | -------- |
| DecomposedMatrixPropType | 否       |

---

### `rotation`

| 类型                                                                         | 必填 |
| ---------------------------------------------------------------------------- | -------- |
| deprecatedPropType(ReactPropTypes.number, 'Use the transform prop instead.') | 否       |

---

### `scaleX`

| 类型                                                                         | 必填 |
| ---------------------------------------------------------------------------- | -------- |
| deprecatedPropType(ReactPropTypes.number, 'Use the transform prop instead.') | 否       |

---

### `scaleY`

| 类型                                                                         | 必填 |
| ---------------------------------------------------------------------------- | -------- |
| deprecatedPropType(ReactPropTypes.number, 'Use the transform prop instead.') | 否       |

---

### `transform`

`transform` accepts an array of transformation objects. Each object specifies the property that will be transformed as the key, and the value to use in the transformation. Objects should not be combined. Use a single key/value pair per object.

The rotate transformations require a string so that the transform may be expressed in degrees (deg) or radians (rad). For example:

`transform([{ rotateX: '45deg' }, { rotateZ: '0.785398rad' }])`

The skew transformations require a string so that the transform may be expressed in degrees (deg). For example:

`transform([{ skewX: '45deg' }])`

| 类型                                                                                                                                                                                                                                                                                                                                                    | 必填 |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| array of object: {perspective: number}, ,object: {rotate: string}, ,object: {rotateX: string}, ,object: {rotateY: string}, ,object: {rotateZ: string}, ,object: {scale: number}, ,object: {scaleX: number}, ,object: {scaleY: number}, ,object: {translateX: number}, ,object: {translateY: number}, ,object: {skewX: string}, ,object: {skewY: string} | 否       |

---

### `transformMatrix`

Deprecated. Use the transform prop instead.

| 类型                    | 必填 |
| ----------------------- | -------- |
| TransformMatrixPropType | 否       |

---

### `translateX`

| 类型                                                                         | 必填 |
| ---------------------------------------------------------------------------- | -------- |
| deprecatedPropType(ReactPropTypes.number, 'Use the transform prop instead.') | 否       |

---

### `translateY`

| 类型                                                                         | 必填 |
| ---------------------------------------------------------------------------- | -------- |
| deprecatedPropType(ReactPropTypes.number, 'Use the transform prop instead.') | 否       |
