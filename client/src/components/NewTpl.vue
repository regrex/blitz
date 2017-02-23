<template>
  <div>
    <h1>新建模板</h1>
    <step v-model="newTplStep" class="new-tpl-step" background-color='#fbf9fe'>
      <step-item v-for="step in stepConf" :title="step.title" :description="step.desp"></step-item>
    </step>
    <div class="step1-wrap" v-if="newTplStep === 0">
      <group title="基础设置">
        <x-input title="标题" name="pageTitle" placeholder="请输入页面标题"></x-input>
      </group>
      <group title="分享设置">
        <x-input title="标题" name="shareTitle" placeholder="请输入分享标题" ></x-input>
        <x-input title="内容" name="shareCnt" placeholder="请输入分享内容"></x-input>
        <x-input title="图片" name="shareImg" placeholder="请输入分享图片"></x-input>
      </group>
    </div>
    <div class="step2-wrap" v-if="newTplStep === 1">
    <x-button class="tpl-last-btn" type="primary" @click.native="showCardList = true">选择卡片</x-button>
      <popup v-model="showCardList" @on-hide="onCardListHide" @on-show="onCardListShow">
        <checker v-model="selectedCard" default-item-class="card-item" selected-item-class="card-item-selected" @on-item-click="showCardList = false">
          <checker-item v-for="card in cardList" :value="card.id">
            <img class="card-thumb" :src="card.thumb" alt="卡片缩率图">
            <p class="card-name">{{card.name}}</p>
          </checker-item>
        </checker>
      </popup>
    </div>
    <div class="step2-wrap" v-if="newTplStep === 2">
      <group title="基础设置">
        <x-input title="标题" name="pageTitle" placeholder="请输入页面标题"></x-input>
      </group>
      <group title="分享设置">
        <x-input title="标题" name="shareTitle" placeholder="请输入分享标题" ></x-input>
        <x-input title="内容" name="shareCnt" placeholder="请输入分享内容"></x-input>
        <x-input title="图片" name="shareImg" placeholder="请输入分享图片"></x-input>
      </group>
    </div>
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
import {
  Group,
  Cell,
  Flexbox,
  FlexboxItem,
  XButton,
  XInput,
  Step,
  StepItem,
  Checker,
  CheckerItem,
  Popup
} from 'vux'

export default {
  components: {
    Group,
    Cell,
    Flexbox,
    FlexboxItem,
    XButton,
    XInput,
    Step,
    StepItem,
    Checker,
    CheckerItem,
    Popup
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
      }],
      showCardList: false,
      selectedCard: 0,
      cardList: [{
        name: '单图',
        thumb: '../../static/card-thumb.png',
        id: 0
      }, {
        name: '左图由文',
        thumb: '../../static/card-thumb.png',
        id: 1
      }]
    }
  },
  methods: {
    nextStep () {
      this.newTplStep++;
    },
    lastStep () {
      this.newTplStep--;
    },
    showCardListPop () {
      this.showCardList = true;
    },
    onCardListHide () {
      console.log('hide');
    },
    onCardListShow () {
      console.log('show');
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
.card-item {
  width: 64px;
  margin: 10px;
  text-align: center;
}
.card-thumb {
  width: 64px;
  height: auto;
}
.card-name {
  text-align: center;
}
</style>
