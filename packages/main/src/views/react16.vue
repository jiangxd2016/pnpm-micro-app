<template>
  <div>
    <micro-app
      name='appname-react16'
      :url='url'
      baseroute='/main-vite/app-react16'
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
  name: 'react16',
  data () {
    return {
      url: `${config.react16}/child/react16/`,
      microAppData: {msg: '来自基座的数据'}
    }
  },
  methods: {
    handleCreate (): void {
      console.log('child-react16 创建了')
    },

    handleBeforeMount (): void {
      console.log('child-react16 即将被渲染')
    },

    handleMount (): void {
      console.log('child-react16 已经渲染完成')

      setTimeout(() => {
        // @ts-ignore
        this.microAppData = {msg: '来自基座的新数据'}
      }, 2000)
    },

    handleUnmount (): void {
      console.log('child-react16 卸载了')
    },

    handleError (): void {
      console.log('child-react16 加载出错了')
    },

    handleDataChange (e: CustomEvent): void {
      console.log('来自子应用 child-react16 的数据:', e.detail.data)
    },
  }
}
</script>

<style>
</style>
