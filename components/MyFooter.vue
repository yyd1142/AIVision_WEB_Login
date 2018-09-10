<template>
  <div class="MyFooter">
    <div class="item">
      <span class="text">设为首页</span> | <span class="text">收藏网页</span> | <span class="text">关于我们</span><br>
      <div class="beian">Cpopyriht @2018 Reftail.com</div>
    </div>
  </div>
</template>

<script>
  export default {
    name: "MyFooter",
    props: {
      languageDatas: Object,
      language: String,
    },
  }
</script>

<style lang="less">
  .MyFooter {
    width: 100%;
    height: 110px;
    display: flex;
    display: -webkit-flex;
    align-items: center;
    justify-content: center;
    .item {
      line-height: 28px;
      .text {
        font-size: 16px;
        cursor: pointer;
        color: #333;
        &:hover {
          text-decoration: underline;
          color: #666;
        }
      }
      .beian {
        color: #8c939d;
        font-size: 14px;
      }
    }
  }
</style>
