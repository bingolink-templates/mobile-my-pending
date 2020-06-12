<template>
  <div ref="wrap">
    <!-- 热门话题 -->
    <div class="my-pending">
      <div class="my-pending-title flex">
        <text class="f28 fw5 c0">我的待办</text>
        <text class="f24 c153 fw4 pl20 pt10 pb10" @click="myPengdingMoreEvent">全部</text>
      </div>
      <div class="my-pending-content flex">
        <div v-for="(item, index) in myPengdingArr" :key='index' @click='myPengdingUserEvent'>
          <text class="c0 f36 tc">{{index+8}}</text>
          <text class="f26 c102 fw4 mt10">{{item}}</text>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        myPengdingArr: ['日程', '待办', '项目', '邮件']
      }
    },
    methods: {
      // 更多
      myPengdingMoreEvent() {
        this.$alert()
      },
      // 常用联系人
      myPengdingUserEvent() {
        this.$alert()
      },
      broadcastWidgetHeight() {
        let _params = this.$getPageParams();
        setTimeout(() => {
          dom.getComponentRect(this.$refs.wrap, (ret) => {
            var channel = new BroadcastChannel('WidgetsMessage')
            channel.postMessage({
              widgetHeight: ret.size.height,
              id: _params.id
            });
            channel.close();
          });
        }, 100)
      }
    },
    mounted() {
      this.broadcastWidgetHeight()
    }
  }
</script>

<style lang="css" src="../css/common.css"></style>
<style>
  .main {}

  .my-pending {
    background-color: #fff;
  }

  .my-pending-title {
    height: 40px;
    margin: 18px 23px 20px 25px;
  }

  .my-pending-content {
    margin: 13px 62px 32px 62px;
  }
</style>