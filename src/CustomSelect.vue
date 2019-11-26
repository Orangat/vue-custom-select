<template>
  <div class="custom-select" v-bind:style="{'width': `${width}px`, 'height': `${height}px`}">
    <input v-model="inputValue" @focus="showOptions" :class="[{'is-options-open': focused}, {'empty-placeholder': !placeholder}, 'select-input']" type="text">
    <span v-if="placeholder" :class="[{'is-focus': inputValue}, 'placeholder']">{{ placeholder }}</span>
    <transition name="fade" mode="in-out">
      <div v-show="focused" class="options">
        <div v-for="(option, i) in filteredOptions" :key="i" @click="selectOption(option)" class="select-item">{{ option.text }}</div>
      </div>
    </transition>
  </div>
</template>

<script>
  export default {
    props: {
      dataArray: {
        type: Array,
        'default': []
      },
      width: {
        type: Number,
        'default': 300
      },
      height: {
        type: Number,
        'default': 60
      },
      placeholder: {
        type: String,
        'default': 'Choose an option'
      }
    },
    data () {
      return {
        inputValue: '',
        selectValue: null,
        focused: false
      }
    },
    computed: {
      filteredOptions () {
        return this.dataArray.filter(option => {
          if (option.text.toLowerCase().includes(this.inputValue.toLowerCase())) {
            return option
          }
        })
      }
    },
    watch: {
      inputValue (value) {
        if (!value) {
          this.selectValue = null
        }
      }
    },
    mounted () {
      document.documentElement.addEventListener('click', this.outsideClick, false)
      if (this.placeholder.trim() === "") {
        this.placeholder = false
      }
    },
    beforeDestroy () {
      document.documentElement.removeEventListener('click', this.outsideClick, false)
    },
    methods: {
      showOptions () {
        this.inputValue = ''
        this.focused = true
      },
      hideOptions () {
        this.$nextTick(() => {
          this.focused = false
        })
      },
      selectOption (option) {
        this.selectValue = option
        this.inputValue = option.text
        this.hideOptions()
      },
      outsideClick (e) {
        if (!this.$el.contains(e.target)) {
          this.hideOptions()
        }
      }
    }
  }
</script>

<style scoped>
  .custom-select {
    position: relative;
    display: flex;
    align-items: center;
  }

  .select-input {
    border: 1px solid rgba(0,0,0,.2);
    outline: none;
    padding: 20px 15px 4px;
    border-radius: 4px;
    transition: all .3s ease;
    z-index: 1;
    width: 100%;
    height: 100%;
  }

  .select-input.empty-placeholder {
    padding: 5px 15px;
  }

  .select-input:focus, .select-input:valid {
    outline: 0;
  }

  .select-input:focus {
    border-color: #a4d8c2;
  }

  .select-input:focus + .placeholder {
    top: 8px;
    font-size: 12px;
    margin-top: 0;
  }

  .select-input.is-options-open {
    border-radius: 4px 4px 0 0;
    border-bottom-color: rgba(0,0,0,.2);
  }

  .placeholder {
    position: absolute;
    left: 15px;
    font-size: 14px;
    color: #9299a2;
    top: 50%;
    color: rgba(51,51,51,.54);
    pointer-events: none;
    transition: all .3s ease;
    margin-top: -12px;
    z-index: 2;
  }

  .placeholder.is-focus {
    top: 8px;
    font-size: 12px;
    margin-top: 0;
  }

  .options {
    width: 100%;
    position: absolute;
    top: 97%;
    background: #fff;
    border: 1px solid rgba(0,0,0,.2);
    border-radius: 0 0 4px 4px;
    max-height: 50vh;
    overflow: auto;
    transition: all .3s ease;
    z-index: 10;
  }

  .select-item {
    height: 40px;
    line-height: 40px;
    cursor: pointer;
    transition: all .3s ease;
    padding: 0 15px;
  }

  .select-item:hover {
    background: #f4fbf8;
  }

  .fade-enter-active,
  .fade-leave-active {
    transition: all .4s ease;
  }
  .fade-enter,
  .fade-leave-active {
    opacity: 0;
    will-change: opacity;
    transform: translateY(-30px);
  }

</style>
