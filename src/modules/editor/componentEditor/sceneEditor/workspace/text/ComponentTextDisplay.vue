<template>
  <div v-html="component.props.html" :style="style"></div>
</template>

<script lang="ts">
  /**
   * create by 给力叔 2017/9/10
   * 专门用于展示文本
   */
  import {ComponentText, GLS_COMPONENT_TEXT} from "../../../../core/display/text/ComponentText";
  import Vue from 'vue'
  import {Component, Input} from 'angular2-decorators-for-vue'
  import {Color} from "../../../../common/colorPicker/Color";
  import {Project} from "../../../../core/project/Project";

  @Component({
    name: GLS_COMPONENT_TEXT,
    components: {}
  } as any)
  export default class ComponentTextDisplay extends Vue {
    @Input() component: ComponentText;
    @Input() project: Project;

    //todo 这个样式应该可以弄成通用的，下次看看
    get style() {
      let style = this.component.style;
      let result:any = {} as any;
      if(style.color){
        result.color = Color.toRGBA(style.color);
      }
      result.lineHeight = style.lineHeight * 100 * 3 + '%';
      return result;
    }
  }
</script>

<style scoped lang="scss">

</style>
