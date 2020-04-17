---
id: version-0.56-stylesheet
title: StyleSheet
original_id: stylesheet
---
##### 本文档贡献者：[sunnylqm](https://github.com/search?q=sunnylqm%40qq.com+in%3Aemail&type=Users)(100.00%)

StyleSheet 提供了一种类似 CSS 样式表的抽象。

创建一个样式表：

```
const styles = StyleSheet.create({
  container: {
    borderRadius: 4,
    borderWidth: 0.5,
    borderColor: '#d6d7da',
  },
  title: {
    fontSize: 19,
    fontWeight: 'bold',
  },
  activeTitle: {
    color: 'red',
  },
});
```

使用一个样式表：

```
<View style={styles.container}>
  <Text style={[styles.title, this.props.isActive && styles.activeTitle]} />
</View>
```

从代码质量角度：

- 从 render 函数中移除具体的样式内容，可以使代码更清晰易懂。
- 给样式命名也可以对 render 函数中的组件增加语义化的描述。

从性能角度：

- 创建一个样式表，就可以使得我们后续更容易通过 ID 来引用样式，而不是每次都创建一个新的对象。
- 它还使得样式只会在 JavaScript 和原生之间传递一次，随后的过程都可以只传递一个 ID（这个优化还未实现）。

### 查看方法

- [`setStyleAttributePreprocessor`](stylesheet.md#setstyleattributepreprocessor)
- [`create`](stylesheet.md#create)
- [`flatten`](stylesheet.md#flatten)

### 查看常量

- [`hairlineWidth`](stylesheet.md#hairlinewidth)
- [`absoluteFill`](stylesheet.md#absolutefill)
- [`absoluteFillObject`](stylesheet.md#absolutefillobject)

---

# 文档

## 方法

### `setStyleAttributePreprocessor()`

```jsx
static setStyleAttributePreprocessor(property, process)
```

WARNING: EXPERIMENTAL. Breaking changes will probably happen a lot and will not be reliably announced. The whole thing might be deleted, who knows? Use at your own risk.

Sets a function to use to pre-process a style property value. This is used internally to process color and transform values. You should not use this unless you really know what you are doing and have exhausted other options.

---

### `create()`

```jsx
static create(obj)
```

Creates a StyleSheet style reference from the given object.

---

### `flatten`

```jsx
static flatten(style)
```

Flattens an array of style objects, into one aggregated style object. Alternatively, this method can be used to lookup IDs, returned by `StyleSheet.register`.

> _NOTE_: Exercise caution as abusing this can tax you in terms of optimizations. IDs enable optimizations through the bridge and memory in general. Refering to style objects directly will deprive you of these optimizations.

Example:

```jsx
var styles = StyleSheet.create({
  listItem: {
    flex: 1,
    fontSize: 16,
    color: "white"
  },
  selectedListItem: {
    color: "green"
  }
});

StyleSheet.flatten([styles.listItem, styles.selectedListItem]);
// returns { flex: 1, fontSize: 16, color: 'green' }
```

Alternative use:

```jsx
var styles = StyleSheet.create({
  listItem: {
    flex: 1,
    fontSize: 16,
    color: "white"
  },
  selectedListItem: {
    color: "green"
  }
});

StyleSheet.flatten(styles.listItem);
// return { flex: 1, fontSize: 16, color: 'white' }
// Simply styles.listItem would return its ID (number)
```

This method internally uses `StyleSheetRegistry.getStyleByID(style)` to resolve style objects represented by IDs. Thus, an array of style objects (instances of `StyleSheet.create()`), are individually resolved to, their respective objects, merged as one and then returned. This also explains the alternative use.

## 常量

### `hairlineWidth`

```jsx
var styles = StyleSheet.create({
  separator: {
    borderBottomColor: "#bbb",
    borderBottomWidth: StyleSheet.hairlineWidth
  }
});
```

这一常量始终是一个整数的像素值（线看起来会像头发丝一样细），并会尽量符合当前平台最细的线的标准。可以用作边框或是两个元素间的分隔线。然而，你不能把它“视为一个常量”，因为不同的平台和不同的屏幕像素密度会导致不同的结果。

如果模拟器缩放过，可能会看不到这么细的线。

---

### `absoluteFill`

A very common pattern is to create overlays with position absolute and zero positioning, so `absoluteFill` can be used for convenience and to reduce duplication of these repeated styles.

---

### `absoluteFillObject`

Sometimes you may want absoluteFill but with a couple tweaks - absoluteFillObject can be used to create a customized entry in a StyleSheet, e.g.:

```jsx
const styles = StyleSheet.create({
  wrapper: {
    ...StyleSheet.absoluteFillObject,
    top: 10,
    backgroundColor: "transparent"
  }
});
```

---
