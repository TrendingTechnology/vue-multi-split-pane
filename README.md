# Vue Multi Split Pane

A component based on Vue.js. Provides unlimited resizable multi pane support. Only provides vertical split for now.

## Demo

[Live Demo](https://vue-multi-split-pane.vercel.app/) | [Codesandbox.io](https://codesandbox.io/s/vue-multi-split-pane-7noiu?file=/src/App.vue)

### Install

```bash
npm i vue-multi-split-pane
```

### Example

```js
import { MultiSplitPane, Pane } from 'vue-multi-split-pane'

export default {
  components: {
    MultiSplitPane,
    Pane
  },
  methods: {
    onPaneCollapsed(index) {
      console.log('onPaneCollapsed', index)
    },
    onPaneExpanded(index) {
      console.log('onPaneExpanded', index)
    }
  }
}
```

```html
<MultiSplitPane
  split="horizontal"
  height="400px"
  width="1000px"
  resizerWidth="30px"
  classes="v-pane-custom"
  @onPaneCollapsed="onPaneCollapsed"
  @onPaneExpanded="onPaneExpanded"
>
  <Pane>
    <template v-slot:resizer>
      resizer slot
    </template>
    <template v-slot:content>
      Content 1
    </template>
  </Pane>
  <Pane>
    <template v-slot:content>
      Content 2
    </template>
  </Pane>
  <Pane>
    <template v-slot:content>
      Content 3
    </template>
  </Pane>
</MultiSplitPane>
```

### Nested Pane Example

```html
<MultiSplitPane
  split="horizontal"
  height="400px"
  width="1000px"
  resizerWidth="30px"
  :nested="true"
  classes="v-pane-custom"
>
  <Pane>
    <template v-slot:content>
      Lorem, ipsum dolor sit amet consectetur adipisicing elit. Consectetur,
      excepturi in dolores accusantium praesentium quidem laborum neque ut ipsum
      veritatis ratione rem, esse totam voluptates ullam nesciunt tempora
      architecto laudantium!
    </template>
  </Pane>
  <Pane classes="paneNested">
    <template v-slot:content>
      <MultiSplitPane
        height="400px"
        resizerWidth="30px"
        classes="v-pane-custom"
      >
        <Pane>
          <template v-slot:content>
            Lorem, ipsum dolor sit amet consectetur adipisicing elit.
            Consectetur, excepturi in dolores accusantium praesentium quidem
            laborum neque ut ipsum veritatis ratione rem, esse totam voluptates
            ullam nesciunt tempora architecto laudantium!
          </template>
        </Pane>
        <Pane>
          <template v-slot:content>
            Lorem, ipsum dolor sit amet consectetur adipisicing elit.
            Consectetur, excepturi in dolores accusantium praesentium quidem
            laborum neque ut ipsum veritatis ratione rem, esse totam voluptates
            ullam nesciunt tempora architecto laudantium!
          </template>
        </Pane>
      </MultiSplitPane>
    </template>
  </Pane>
</MultiSplitPane>
```

## Props

| Prop         | Description                                                                  |        value         | default  |
| :----------- | :--------------------------------------------------------------------------- | :------------------: | :------: |
| split        | Orientation of the MultiSplitPane                                            | vertical, horizontal | vertical |
| width        | Width of the MultiSplitPane                                                  |        String        |   100%   |
| height       | Height of the MultiSplitPane                                                 |        String        |   auto   |
| resizerWidth | Width/height of the resizers. Valid for horizontal and vertical orientation. |        String        |   30px   |
| classes      | Custom class prop. Can be send to MultiSplitPane or Pane                     |        String        |   none   |
| :nested      | Will you use nested MultiSplitPane? Then should be true.                     |       Boolean        |  false   |

## Events

| Event                  | Description                                                         |
| :--------------------- | :------------------------------------------------------------------ |
| onPaneCollapsed(index) | Event will be fired when collapsed any pane. Used on MultiSplitPane |
| onPaneExpanded(index)  | Event will be fired when expanded any pane. Used on MultiSplitPane  |
