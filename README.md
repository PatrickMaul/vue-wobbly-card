# vue-wobbly-card
### Inspired by [baby_wolf_codes](https://www.instagram.com/baby_wolf_codes/)
#### [GitHub - Repository](https://github.com/PatrickMaul/vue-wobbly-card)
---
<br>

This card creates a simple but very beautiful effect.
The card begins to lift off the screen in the opposite direction to the mouse pointer.

In other words, at the point where the mouse pointer is, the card is pushed back a little, while the opposite corner is lifted a little.

## Installation
### NPM
````
npm i vue-wobbly-card
````

## Usage
 ````html
<template>
    <vwc> Hello, World </vwc>
</template>

<script>
import vwc from "vue-wobbly-card";

export default {
  name: "Example",
  components: {
    vwc,
  },
};
</script>
````

<!-- ### Props

| Prop | Type | Default | Description |
| --- | --- | --- | --- |
| `shaky_card_id` | String | Random | **Required** for card movement.|
| `shakiness` | Number | 3 | **Required** Possible value between 1-6, more or less will set `shakiness` to 0.| -->
### Events
You should perform all events inside the `vue-wobbly-card` element.

## Version History
### 1.1.0
Propper Import
### 1.0.1
Test
### 1.0.0
Publish v1