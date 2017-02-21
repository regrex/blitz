<template>
  <div>
    <h1>新建模板</h1>
    <step v-model="newTplStep" class="new-tpl-step" background-color='#fbf9fe'>
      <step-item v-for="step in stepConf" :title="step.title" :description="step.desp"></step-item>
    </step>
    <group title="基础设置">
      <x-input title="标题" name="pageTitle" placeholder="请输入页面标题"></x-input>
    </group>
    <group title="分享设置">
      <x-input title="标题" name="shareTitle" placeholder="请输入分享标题" ></x-input>
      <x-input title="内容" name="shareCnt" placeholder="请输入分享内容"></x-input>
      <x-input title="图片" name="shareImg" placeholder="请输入分享图片"></x-input>
    </group>
    <flexbox class="btn-group">
      <flexbox-item v-if="newTplStep !== 0" >
        <x-button class="tpl-last-btn" type="primary" @click.native="lastStep">上一步</x-button>
      </flexbox-item>
      <flexbox-item v-if="newTplStep !== stepConf.length - 1">
        <x-button class="tpl-next-btn" type="primary" @click.native="nextStep">下一步</x-button>
      </flexbox-item>
    </flexbox>
  </div>
</template>

<script>
import { Group, Cell, Flexbox, FlexboxItem, XButton, XInput, Step, StepItem } from 'vux'

export default {
  components: {
    Group,
    Cell,
    Flexbox,
    FlexboxItem,
    XButton,
    XInput,
    Step,
    StepItem
  },
  data () {
    return {
      newTplStep: 0,
      stepConf: [{
        title: '设置',
        desp: ''
      }, {
        title: '编辑',
        desp: ''
      }, {
        title: '发布',
        desp: ''
      }]
    }
  },
  methods: {
    nextStep () {
      this.newTplStep++;
    },
    lastStep () {
      this.newTplStep--;
    }
  }
}
</script>

<style scoped>
.new-tpl-step {
  margin: 20px 10px;
}
.btn-group {
  margin: 20px 0;
}
.tpl-last-btn,
.tpl-next-btn {
  border-radius: 21px;
  width: 90%;
}
</style>
