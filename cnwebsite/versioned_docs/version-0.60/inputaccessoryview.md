---
id: version-0.60-inputaccessoryview
title: InputAccessoryView
original_id: inputaccessoryview
---

##### 本文档贡献者：[sunnylqm](https://github.com/search?q=sunnylqm%40qq.com+in%3Aemail&type=Users)(100.00%)

A component which enables customization of the keyboard input accessory view on iOS. The input accessory view is displayed above the keyboard whenever a `TextInput` has focus. This component can be used to create custom toolbars.

To use this component wrap your custom toolbar with the InputAccessoryView component, and set a `nativeID`. Then, pass that `nativeID` as the `inputAccessoryViewID` of whatever `TextInput` you desire. A simple example:

```ReactNativeWebPlayer
import React, { Component } from 'react';
import { View, ScrollView, TextInput, InputAccessoryView, Button } from 'react-native';

export default class UselessTextInput extends Component {
  constructor(props) {
    super(props);
    this.state = {text: 'Placeholder Text'};
  }

  render() {
    const inputAccessoryViewID = "uniqueID";
    return (
      <View>
        <ScrollView keyboardDismissMode="interactive">
          <TextInput
            style={{
              padding: 10,
              paddingTop: 50,
            }}
            inputAccessoryViewID={inputAccessoryViewID}
            onChangeText={text => this.setState({text})}
            value={this.state.text}
          />
        </ScrollView>
        <InputAccessoryView nativeID={inputAccessoryViewID}>
          <Button
            onPress={() => this.setState({text: 'Placeholder Text'})}
            title="Reset Text"
          />
        </InputAccessoryView>
      </View>
    );
  }
}
```

This component can also be used to create sticky text inputs (text inputs which are anchored to the top of the keyboard). To do this, wrap a `TextInput` with the `InputAccessoryView` component, and don't set a `nativeID`. For an example, look at [InputAccessoryViewExample.js](https://github.com/facebook/react-native/blob/master/RNTester/js/InputAccessoryViewExample.js).

### 查看Props

* [`backgroundColor`](inputaccessoryview.md#backgroundcolor)
* [`nativeID`](inputaccessoryview.md#nativeid)
* [`style`](inputaccessoryview.md#style)

---

# 文档

## Props

### `backgroundColor`

| 类型               | 必填 |
| ------------------ | ---- |
| [color](colors.md) | 否   |

---

### `nativeID`

An ID which is used to associate this `InputAccessoryView` to specified TextInput(s).

| 类型   | 必填 |
| ------ | ---- |
| string | 否   |

---

### `style`

| 类型                         | 必填 |
| ---------------------------- | ---- |
| [style](view-style-props.md) | 否   |

# 已知问题

* [react-native#18997](https://github.com/facebook/react-native/issues/18997): 不支持多行的`TextInput`
* [react-native#20157](https://github.com/facebook/react-native/issues/20157): 不能和底部tab栏一起使用