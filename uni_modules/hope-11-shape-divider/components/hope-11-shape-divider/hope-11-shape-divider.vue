<template>
  <view class="container">
    <slot></slot>
    <view class="shape-divider" :style="shapeDividerStyle">
      <view
        :style="{width: `calc(${this.width > 100 ? this.width : 100}% + 1.3rpx)`, height: `${height}rpx`, backgroundImage: `url(${svgImage})`, transform: (flip && canFlip) ? 'rotateY(180deg)' : ''}">
      </view>
    </view>
  </view>
</template>
<script>
  import shapeOptions from './shape-options'
  import shapePathMap from './shape-path-map'
  import svg2DataUrl from './svg'

  export default {
    props: {
      shape: {
        type: String,
        default: 'waves',
        validator: (value) => {
          return Object.keys(shapePathMap).includes(value)
        }
      },
      color: {
        type: String,
        default: '#fff',
      },
      width: {
        type: [Number, String],
        default: 100,
      },
      height: {
        type: [Number, String],
        default: 100,
      },
      flip: {
        type: Boolean,
        default: false,
      },
      invert: {
        type: Boolean,
        default: false,
      },
      position: {
        type: String,
        default: 'top',
      },
    },

    data() {
      return {
        shapeOptions,
        shapePathMap
      }
    },

    computed: {
      svgImage() {
        let shape = this.shape
        
        // 如果不存在该形状，则默认为waves
        if (!shapePathMap[this.shape]) {
          shape = 'waves'
        }
        
        // 如果设置了invert，且存在invert形状，则使用invert形状
        if (this.invert && shapePathMap[shape + '-invert']) {
          shape += '-invert'
        }

        const svg = `
          <svg
            xmlns='http://www.w3.org/2000/svg' viewBox='0 0 1200 120'
            preserveAspectRatio='none'>
              ${
                shapePathMap[shape].map((el, index) => (
                  `<path
                    key='${index}'
                    d='${el.path}'
                    style='${'fill:' + this.color}'
                    opacity='${el.opacity}'>
                  </path>`
                ))
              }
          </svg>
        `
        
        return svg2DataUrl(svg)
      },
      
      shapeDividerStyle() {
        switch (this.position) {
          case 'top':
            return {
              top: 0,
                transform: (this.invert && shapePathMap[this.shape + '-invert']) ? 'rotate(180deg)' : 'none',
            }
          case 'bottom':
            return {
              bottom: 0,
                transform: (this.invert && shapePathMap[this.shape + '-invert']) ? 'none' : 'rotate(180deg)',
            }
        }
      },
      
      canFlip() {
        return this.shapeOptions.filter(item => item.value === this.shape)[0].canFlip
      }
    }
  }
</script>
<style scoped>
  .container {
    position: relative;
    overflow: hidden;
    display: flex;
  }

  .shape-divider {
    position: absolute;
    left: 0;
    width: 100%;
    line-height: 0;
    overflow: hidden;
  }
</style>