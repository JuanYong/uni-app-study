<template>
<uni-shadow-root class="vant-tab-index"><view v-if="animated || inited" class="custom-class utils.bem('tab__pane', { active, inactive: !active }) }}" :style="(animated || active ? '' : 'display: none;')+' '+(width ? 'width:' + width + 'px;' : '')">
  <slot></slot>
</view></uni-shadow-root>
</template>
<wxs src="../wxs/utils.wxs" module="utils"></wxs>
<script>

global['__wxRoute'] = 'vant/tab/index'
import { VantComponent } from '../common/component';
VantComponent({
  relation: {
    name: 'tabs',
    type: 'ancestor'
  },
  props: {
    dot: Boolean,
    info: null,
    title: String,
    disabled: Boolean,
    titleStyle: String
  },
  data: {
    width: null,
    inited: false,
    active: false,
    animated: false
  },
  watch: {
    title: 'update',
    disabled: 'update',
    dot: 'update',
    info: 'update',
    titleStyle: 'update'
  },
  methods: {
    update: function update() {
      var parent = this.getRelationNodes('../tabs/index')[0];

      if (parent) {
        parent.updateTabs();
      }
    }
  }
});
export default global['__wxComponents']['vant/tab/index']
</script>
<style platform="mp-weixin">
@import '../common/index.css';.van-tab__pane{box-sizing:border-box;overflow-y:auto}.van-tab__pane--active{height:auto}.van-tab__pane--inactive{height:0;overflow:visible}
</style>