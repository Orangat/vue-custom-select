# vue-custom-select

    simple, minimalistic autocomplete select dropdown component for Vue apps for you!

### Install Via NPM

```bash
$ npm i vue-custom-select
```
### Register it

In your component:

```javascript
import vueCustomSelect from 'vuecustomselect/src/CustomSelect.vue';

export default {
  components: {
     vueCustomSelect
  },
  //...
}
```

Globally:

```javascript
import vueCustomSelect from "vue-custom-select";
Vue.component('vue-custom-select', vueCustomSelect);
```

### Use It

```html
<vue-custom-select 
  :data-array="dataArray"
  placeholder="Choose your country">
</vue-custom-select>
```
## And you will get result:
<img style="width: 500px" src="https://raw.githubusercontent.com/orangat/vuecustomselect/master/custom-select.png">

### Data array must be something like this:
```javascript
data () {
    return {
      dataArray: [
        {text: 'First option', value: 1},
        {text: 'Second option', value: 2},
        {text: 'Third option', value: 3},
        {text: 'Fourth option', value: 4},
        {text: 'Fifth option', value: 5},
        {text: 'Sixth option', value: 4}
      ]
    }
  }
```
where the key 'text' will be a title of your options

## Available Props:
```javascript
props: {
  // Array list of your elements/options 
  dataArray: {
    type: Array,
    'default': []
  },
  // Set width
  width: {
    type: Number,
    'default': 300
  },
  // Set height
  height: {
    type: Number,
    'default': 60
  },
  // Set custom placeholder
  placeholder: {
    type: String,
    'default': 'Choose an option'
  }
}
```
