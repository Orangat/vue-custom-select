# vue-custom-select

    simple, minimalistic autocomplete select dropdown component for Vue apps for you!

* ~4kb (the component size)
* SSR Support
* Zero dependencies
* Minimalistic
* Convenient and easy to use
* Floating placeholder

### Install Via NPM

```bash
$ npm i vue-custom-select
```
### Register it

In your component:

```javascript
import vueCustomSelect from 'vue-custom-select/src/CustomSelect.vue';

export default {
  components: {
     vueCustomSelect
  },
  //...
}
```

Globally:

```javascript
import Vue from 'vue';
import vueCustomSelect from "vue-custom-select/src/CustomSelect.vue";
Vue.component('vue-custom-select', vueCustomSelect);
```

### Use It

```html
<vue-custom-select 
  v-model="selectedOption"
  :data-array="dataArray"
  placeholder="Choose your country">
</vue-custom-select>
```
use v-model to get the selected option, or set standard value

### Data array must be something like this:
```javascript
data () {
    return {
      dataArray: [
        {text: 'First option', value: 'Any'},
        {text: 'Second option', value: 'Any'},
        {text: 'Third option', value: 'Any'},
        {text: 'Fourth option', value: 'Any'},
        {text: 'Fifth option', value: 'Any'},
        {text: 'Sixth option', value: 'Any'}
      ]
    }
  }
```
where the key 'text' will be a title of your options

### And you will get a result:
<img style="width: 500px" src="https://raw.githubusercontent.com/orangat/vue-custom-select/master/custom-select.png">

### Customize CSS
If you don't like styles, you can customize it just using selector /deep/, for example:

```css
.your-wrap-class /deep/ .select-input {
    background: lightblue;
}
```
where "your-wrap-class" it's parent class in your code 

### Available Props:
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

### Github link:
https://github.com/Orangat/vue-custom-select <br>
Fill free to create some issue, if you find some bugs, or want to improve something. <br>
If you have questions, write me 'serg,webdeveloper@gmail.com' 
