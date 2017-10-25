## Waterfall

### Install

#### Global registration

```js
import Vue from 'vue';
import { Waterfall } from 'vant';

Vue.use(Waterfall);
```

#### Local registration
If you just watch to use `Waterfall` in a component, you can register the directive in the component. 

```js
import { Waterfall } from 'vant';

export default {
  directives: {
    WaterfallLower: Waterfall('lower'),
    WaterfallUpper: Waterfall('upper')
  }
};
```

### Usage

<script>
import { Waterfall } from 'packages';

export default {
  data() {
    return {
      list: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9],
      disabled: false
    };
  },

  directives: {
    WaterfallLower: Waterfall('lower')
  },

  methods: {
    loadMore() {
      this.disabled = true;
      setTimeout(() => {
        for (let i = 0; i < 5; i ++) {
          this.list.push(this.list.length);
        }
        this.disabled = false;
      }, 200);
    }
  }
};
</script>

#### Basic Usage

:::demo Basic Usage
```html
<p class="page-desc">This list will load items will scroll to bottom.</p>
<ul
  v-waterfall-lower="loadMore"
  waterfall-disabled="disabled"
  waterfall-offset="400">
  <li v-for="item in list">{{ item }}</li>
</ul>
```

```js
export default {
  data() {
    return {
      list: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9],
      disabled: false
    };
  },

  directives: {
    WaterfallLower: Waterfall('lower')
  },

  methods: {
    loadMore() {
      this.disabled = true;
      setTimeout(() => {
        for (let i = 0; i < 5; i ++) {
          this.list.push(this.list.length);
        }
        this.disabled = false;
      }, 200);
    }
  }
};
```
:::

### API

| Attribute | Description | Type | Default | Accepted Values |
|-----------|-----------|-----------|-------------|-------------|
| v-waterfall-lower | Function to trigger when scroll to bottom | `Function` | - | - |
| v-waterfall-upper | Function to trigger when scroll to top | `Function` | - | - |
| waterfall-disabled | Key of the property to control disable status in instance | `String` | - | - |
| waterfall-offset | Offset to trigger callback function | `Number` | `300` | - |