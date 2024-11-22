<script setup lang="ts">
  import {ref} from 'vue'

  const codeList = ref([
    {
      code: '',
      type: 'Vue组件'
    }
  ])

</script>

<template>
  <a-layout style="height: 100%;">
    <a-layout-header style="text-align: center; background-color: #9bb3e9">
      <h1>- VUE2组件分析 -</h1>
    </a-layout-header>
    <a-layout-content style="padding: 24px; display: flex; justify-content: center; overflow: auto;">
      <div class="scroll-container">
        <!--输入框，1+n，某个VUE组件以及相关的子组件、utils、api等-->
        <div class="block-container">
          <h3>组件代码</h3>
          <a-form>
            <a-form-item class="line-element" v-for="(item, index) in codeList">
              <a-textarea :rows="8" v-model:value="item.code" :key="index"/>
              <div class="line-footer">{{ item.type }}</div>
            </a-form-item>
            <div class="btn-group">
              <a-button style="width: 100%; max-width: 240px" type="primary" ghost>增加代码块</a-button>
              <a-button style="width: 100%; max-width: 240px" type="primary">开始分析</a-button>
            </div>
          </a-form>
        </div>
        <!--操作链路-->
        <div class="block-container">
          <h3>视图链路</h3>
        </div>
        <!--树整体分析-->
        <div class="block-container">
          <h3>总体复杂度</h3>
        </div>
      </div>
    </a-layout-content>
    <!--TODO: 标签栏，管理各个VUE组件缓存-->

  </a-layout>
</template>

<style scoped>
  h1{
    color: #fff;
    font-weight: bold;
    font-size: 16px;
  }
  .scroll-container {
    width: 100%;
    height: calc(100vh - 44px);
    overflow-y: auto;
    max-width: 1200px;
    min-width: 600px;

    .block-container {
      margin: 8px 8px 16px 8px ;
      min-height: 32px;
      background-color: #f6f6f6aa;
      border-radius: 8px;
      box-shadow: 0 0 8px #00000022;
      backdrop-filter: blur(8px);
      display: flex;
      flex-direction: column;
      width: calc(100% - 16px);
      padding: 16px 12px;
      align-items: stretch;
      .line-element {
        margin: 8px 0;
        .line-footer {
          color: #666666;
          margin: 4px 0;
          width: 100%;
          text-align: end;
        }
      }
      .btn-group {
        display: flex;
        width: 100%;
        justify-content: space-around;
      }
    }
  }

</style>