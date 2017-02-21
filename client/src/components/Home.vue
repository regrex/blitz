<template>
  <div>
    <div class="vux-demo">
      <h1>Blitz</h1>
    </div>
    <group title="管理">
      <cell title="模板列表" is-link></cell>
      <cell title="卡片列表" is-link></cell>
    </group>
    <router-link class="new-tpl-btn" to="/NewTpl"><x-button plain type="primary" style="border-radius:99px;">New Tpl</x-button></router-link>
  </div>
</template>

<script>
import { Group, Cell, Flexbox, FlexboxItem, XButton, XInput } from 'vux'

export default {
  components: {
    Group,
    Cell,
    Flexbox,
    FlexboxItem,
    XButton,
    XInput
  },
  data () {
    return {
      // note: changing this line won't causes changes
      // with hot-reload because the reloaded component
      // preserves its current state and we are modifying
      // its initial state.
      msg: 'Hello World!'
    }
  }
}
</script>

<style scoped>
.new-tpl-btn {
  display: block;
  margin: 20px 10% 0 10%;
}
</style>
