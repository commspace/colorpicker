a Vue3.x based color picker component. 

English | [中文](README.zh_CN.md)

## Features

- Supports 3 CSS background color modes: `solid`, `linear-gradient` and `radial-gradient`.
- Supports color opacity(alpha) adjustment.
- Supports gradient bar control, easily drag/add/delete the control points.
- The EyeDropper can quickly pick any color from your screen. （supports Google Chrome version 95+）
- Supports live preview.

<div style="width:268px;height:347px">
<video src="https://user-images.githubusercontent.com/20314549/180185437-259e668f-03ec-45ba-bb5a-bf7bd99973e2.mov" type="video/mp4" style="width:100%;height:100%;object-fill:fill" autoplay loop controls="false">
</video>
</div>

## Installation

```bash
npm i @mcistudio/vue-colorpicker
```

### How to Use

#### Global Registration
main.js
```javascript

import ColorPicker from '@mcistudio/vue-colorpicker'
import '@mcistudio/vue-colorpicker/style.css'
createApp(App)
  .use(router)
  .use(ColorPicker)
  .mount("#app");
```
##### OR

#### Local Registration
HelloWorld.vue
```vue
<script setup>
import ColorPicker from '@mcistudio/vue-colorpicker'
import '@mcistudio/vue-colorpicker/dist/style.css'

<template>
  <ColorPicker></ColorPicker>
</template>

</script>
```

#### demo
HelloWorld.vue
```vue
<template>
  <ColorPicker mode="mode" :degree="degree" :gradients="grad" @colorChanged="triggerChanged" />
</template>

<script setup>
import ColorPicker from '@mcisutdio/vue-colorpicker'
import '@mcisutdio/vue-colorpicker/dist/style.css'
import { ref } from 'vue'
const mode = ref('linear')
const degree = ref(90)
const grad = ref([
  { id: 0, percent: 10, color: { r: 255, g: 10, b: 20, a: 1 } },
  { id: 1, percent: 100, color: { r: 59, g: 50, b: 240, a: 1 } },
])
function triggerChanged(color) {
  console.log('current color:', color)
}
</script>
```



### Props

| Prop Name | Description                         | Type       | Accepted Values         | Default                                                      | Required |
| --------- | ----------------------------------- | ---------- | ----------------------- | ------------------------------------------------------------ | -------- |
| mode      | color mode                          | String     | solid / linear / radial | solid                                                        | No       |
| degree    | drgee value in Linear-gradient mode | Number     | -                       | 90                                                           | No       |
| color     | rgba color value in solid mode      | String     | -                       | { r: 0, g: 0, b: 0, a: 1 }                                   | No       |
| gradients | gradient list<br />                 | JSON Array | -                       | [{ percent: 0, color: { r: 255, g: 255, b: 255, a: 1 } }{ percent: 100, color: { r: 0, g: 0, b: 0, a: 1 } }] | No       |



### Events

| event Name   | Description | Parameters |
| ------------ | ----------- | ---------- |
| colorChanged |             | returnValue|

###### `returnValue` examples:

**Solid Mode**
```JSON
{
    "mode": "solid",
    "color": {
        "r": 0,
        "g": 0,
        "b": 0,
        "a": 1
    },
    "css": "background-color:rgba(0,0,0,1)"
}
```

**Linear Mode**
```JSON
{
    "mode": "solid",
    "color": {
        "r": 0,
        "g": 0,
        "b": 0,
        "a": 1
    },
    "css": "background-color:rgba(0,0,0,1)"
}
```

**Radial Mode**
```JSON
{
    "mode": "radial",
    "color": [
        {
            "percent": 0,
            "color": {
                "r": 255,
                "g": 255,
                "b": 255,
                "a": 1
            }
        },
        {
            "percent": 100,
            "color": {
                "r": 0,
                "g": 0,
                "b": 0,
                "a": 1
            }
        }
    ],
    "css": "background-image:radial-gradient(rgba(255,255,255,1) 0%,rgba(0,0,0,1) 100%)"
}
```