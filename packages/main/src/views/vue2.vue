<template>
  <div>
    <micro-app
      name='appname-vue2'
      :url='url'
      baseroute='/main-vite/app-vue2'
      :data='microAppData'
      @created='handleCreate'
      @beforemount='handleBeforeMount'
      @mounted='handleMount'
      @unmount='handleUnmount'
      @error='handleError'
      @datachange='handleDataChange'
    ></micro-app>
  </div>
</template>

<script lang="ts">
import config from '../config'

export default {
  name: 'vue2',
  data () {
    return {
      url: `${config.vue2}/child/vue2/`,
      microAppData: {msg: '来自基座的数据'}
    }
  },
  methods: {
    handleCreate (): void {
      console.log('child-vue2 创建了')
    },

    handleBeforeMount (): void {
      console.log('child-vue2 即将被渲染')
    },

    handleMount (): void {
      console.log('child-vue2 已经渲染完成')

      setTimeout(() => {
        // @ts-ignore
        this.microAppData = {msg: '来自基座的新数据'}
      }, 2000)
    },

    handleUnmount (): void {
      console.log('child-vue2 卸载了')
    },

    handleError (): void {
      console.log('child-vue2 加载出错了')
    },

    handleDataChange (e: CustomEvent): void {
      console.log('来自子应用 child-vue2 的数据:', e.detail.data)
    },
  }
}
</script>

<style>
</style>
