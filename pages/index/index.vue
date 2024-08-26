<template>
  <view class="content">
    <view class="wrapper">
      <view class="title">基础使用</view>
      <ShapeDivider>
        <image :src="image4" mode="aspectFill" class="image"></image>
      </ShapeDivider>
    </view>
    <view class="wrapper">
      <view class="title">设置宽高</view>
      <ShapeDivider :width="200" :height="300">
        <image :src="image4" mode="aspectFill" class="image"></image>
      </ShapeDivider>
    </view>
    <view class="wrapper">
      <view class="title">设置形状及位置</view>
      <ShapeDivider shape="waves-opacity" position="bottom">
        <image :src="image4" mode="aspectFill" class="image"></image>
      </ShapeDivider>
    </view>
    <view class="wrapper">
      <view class="title">设置翻转</view>
      <ShapeDivider shape="waves-opacity" position="bottom" flip>
        <image :src="image4" mode="aspectFill" class="image"></image>
      </ShapeDivider>
    </view>
    <view class="wrapper">
      <view class="title">设置倒转</view>
      <ShapeDivider shape="waves" position="bottom" invert>
        <image :src="image4" mode="aspectFill" class="image"></image>
      </ShapeDivider>
    </view>
    <view class="wrapper">
      <view class="title">设置颜色</view>
      <ShapeDivider shape="waves" position="bottom" invert color="rgba(255, 255, 255, 0.8)">
        <image :src="image4" mode="aspectFill" class="image"></image>
      </ShapeDivider>
    </view>
  </view>
</template>

<script>
  import ShapeDivider from '@/uni_modules/hope-11-shape-divider/components/hope-11-shape-divider/hope-11-shape-divider.vue'
  export default {
    components: {
      ShapeDivider
    },
    data() {
      return {
        image1: 'https://images.unsplash.com/photo-1721893484306-23d5379b5d9f?q=80&w=750&h=400',
        image2: 'https://images.unsplash.com/photo-1723640654445-c68052085a90?q=80&w=750&h=400',
        image3: 'https://images.unsplash.com/photo-1719090024488-a8e83d65bb06?q=80&w=750&h=400',
        image4: 'https://images.unsplash.com/photo-1722440814495-3d2d3107a7de?q=80&w=750&h=400',
        image5: 'https://images.unsplash.com/photo-1720174595774-2b5b4cb19d47?q=80&w=750&h=400',
        image6: 'https://images.unsplash.com/photo-1722459154931-74de2a3acccc?q=80&w=750&h=400',
        image7: 'https://images.unsplash.com/photo-1722459157013-e3a8db100218?q=80&w=750&h=400',
        image8: 'https://images.unsplash.com/photo-1720600335872-f3ed672e7429?q=80&w=750&h=400',
      }
    },
    onLoad() {

    },
    methods: {

    }
  }
</script>

<style lang="scss" scoped>
  .content {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;

    .wrapper {
      margin: 20px 0;

      .title {
        margin-bottom: 10px;
        font-weight: bold;
        display: flex;
        justify-content: center;
        align-items: center;
      }

      .value {
        margin-top: 10px;
        display: flex;
        justify-content: center;
        align-items: center;
      }
    }
  }

  .image {
    width: 750rpx;
    height: 400rpx;
  }
</style>