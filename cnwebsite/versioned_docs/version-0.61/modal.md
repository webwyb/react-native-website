---
id: version-0.61-modal
title: Modal
original_id: modal
---

##### 本文档贡献者：[sunnylqm](https://github.com/search?q=sunnylqm%40qq.com+in%3Aemail&type=Users)(98.92%), [hqwlkj](https://github.com/search?q=hqwlkj%40outlook.com+in%3Aemail&type=Users)(1.08%)

Modal 组件是一种简单的覆盖在其他视图之上显示内容的方式。

```jsx
import React, { Component } from "react";
import { Modal, Text, TouchableHighlight, View } from "react-native";

class ModalExample extends Component {
  state = {
    modalVisible: false
  };

  setModalVisible(visible) {
    this.setState({ modalVisible: visible });
  }

  render() {
    return (
      <View style={{ marginTop: 22 }}>
        <Modal
          animationType="slide"
          transparent={false}
          visible={this.state.modalVisible}
          onRequestClose={() => {
            alert("Modal has been closed.");
          }}
        >
          <View style={{ marginTop: 22 }}>
            <View>
              <Text>Hello World!</Text>

              <TouchableHighlight
                onPress={() => {
                  this.setModalVisible(!this.state.modalVisible);
                }}
              >
                <Text>Hide Modal</Text>
              </TouchableHighlight>
            </View>
          </View>
        </Modal>

        <TouchableHighlight
          onPress={() => {
            this.setModalVisible(true);
          }}
        >
          <Text>Show Modal</Text>
        </TouchableHighlight>
      </View>
    );
  }
}
```

---

# 文档

## Props

### `visible`

`visible`属性决定 modal 是否显示。

| 类型 | 必填 |
| ---- | ---- |
| bool | 否   |

---

### `supportedOrientations`

`supportedOrientations`用于指定在设备切换横竖屏方向时，modal 会在哪些屏幕朝向下跟随旋转。在 iOS 上，除了本属性外，还会受到应用的 Info.plist 文件中`UISupportedInterfaceOrientations`的限制。如果还设置了`presentationStyle`属性为`pageSheet`或`formSheet`，则在 iOS 上本属性将被忽略。

| 类型                                                                                                | 必填 | 平台 |
| --------------------------------------------------------------------------------------------------- | ---- | ---- |
| array of enum('portrait', 'portrait-upside-down', 'landscape', 'landscape-left', 'landscape-right') | 否   | iOS  |

---

### `onRequestClose`

`onRequestClose`回调会在用户按下 Android 设备上的后退按键或是 Apple TV 上的菜单键时触发。请务必注意本属性在 Android 平台上为必填，且会在 modal 处于开启状态时阻止`BackHandler`事件。

| 类型     | 必填 | 平台                     |
| -------- | ---- | ------------------------ |
| function | 是   | Android, Platform.isTVOS |
| function | 否   | (Others)                 |

---

### `onShow`

`onShow`回调函数会在 modal 显示时调用。

| 类型     | 必填 |
| -------- | ---- |
| function | 否   |

---

### `transparent`

`transparent` 属性是指背景是否透明，默认为白色，将这个属性设为：true 的时候弹出一个透明背景层的modal。

| 类型 | 必填 |
| ---- | ---- |
| bool | 否   |

---

### `animationType`

`animationType`指定了 modal 的动画类型。

* `slide` 从底部滑入滑出。
* `fade` 淡入淡出。
* `none` 没有动画，直接蹦出来。

默认值为`none`。

| 类型                          | 必填 |
| ----------------------------- | ---- |
| enum('none', 'slide', 'fade') | 否   |

---

### `hardwareAccelerated`

`hardwareAccelerated`属性决定是否强制启用硬件加速来绘制弹出层。

| 类型 | 必填 | 平台    |
| ---- | ---- | ------- |
| bool | 否   | Android |

---

### `statusBarTranslucent`

The `statusBarTranslucent` prop determines whether your modal should go under the system statusbar.

| 类型 | 必填 | 平台 |
| ---- | -------- | -------- |
| bool | 否       | Android  |

---

### `onDismiss`

`onDismiss`回调会在 modal 被关闭时调用。

| 类型     | 必填 | 平台 |
| -------- | ---- | ---- |
| function | 否   | iOS  |

---

### `onOrientationChange`

模态窗显示的时候，当设备方向发生更改时，将调用`onOrientationChange`回调方法。 提供的设备方向仅为“竖屏”或“横屏”。 无论当前方向如何，也会在初始渲染时调用此回调方法。

| 类型     | 必填 | 平台 |
| -------- | ---- | ---- |
| function | 否   | iOS  |

---

### `presentationStyle`

`presentationStyle`决定 modal（在较大屏幕的设备比如 iPad 或是 Plus 机型）如何展现。更多细节请参阅<https://developer.apple.com/reference/uikit/uimodalpresentationstyle>。

* `fullScreen`完全盖满屏幕。
* `pageSheet`竖直方向几乎盖满，水平居中，左右留出一定空白（仅用于大屏设备）。
* `formSheet`竖直和水平都居中，四周都留出一定空白（仅用于大屏设备）。
* `overFullScreen`完全盖满屏幕，同时允许透明。

默认会根据`transparent`属性而设置为`overFullScreen`或是`fullScreen`。

| 类型                                                           | 必填 | 平台 |
| -------------------------------------------------------------- | ---- | ---- |
| enum('fullScreen', 'pageSheet', 'formSheet', 'overFullScreen') | 否   | iOS  |
