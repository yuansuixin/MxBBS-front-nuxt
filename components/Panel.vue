<template>
  <div class="fly-panel fly-column">
    <div class="layui-container">
      <ul class="layui-clear">
        <nuxt-link tag="li" to="/" class="layui-hide-xs">
          <a href="/">首页</a>
        </nuxt-link>
        <nuxt-link
          v-for="(item, index) in lists"
          :key="'panel' + index"
          tag="li"
          :to="item.path"
        >
          <a href="jie/index.html">
            {{ item.name }}
            <span v-if="item.isNew" class="layui-badge-dot"></span>
          </a>
        </nuxt-link>
        <li class="layui-hide-xs layui-hide-sm layui-show-md-inline-block">
          <span class="fly-mid"></span>
        </li>

        <!-- 用户登入后显示 -->
        <template v-if="isLogin">
          <li class="layui-hide-xs layui-hide-sm layui-show-md-inline-block">
            <nuxt-link :to="{ name: 'mypost' }">我发表的贴</nuxt-link>
          </li>
          <li class="layui-hide-xs layui-hide-sm layui-show-md-inline-block">
            <nuxt-link :to="{ name: 'mycollection' }">我收藏的贴</nuxt-link>
          </li>
        </template>
      </ul>

      <div class="fly-column-right layui-hide-xs">
        <span class="fly-search">
          <i class="layui-icon"></i>
        </span>
        <nuxt-link :to="{ name: 'add' }" class="layui-btn">发表新帖</nuxt-link>
      </div>
      <div
        class="layui-hide-sm layui-show-xs-block"
        style="margin-top: -10px; padding-bottom: 10px; text-align: center;"
      >
        <nuxt-link :to="{ name: 'add' }" class="layui-btn">发表新帖</nuxt-link>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Panel',
  data() {
    return {
      lists: [
        {
          name: '提问',
          path: '/index/ask',
          isNew: false
        },
        {
          name: '分享',
          path: '/index/share',
          isNew: true
        },
        {
          name: '讨论',
          path: '/index/discuss',
          isNew: false
        },
        {
          name: '建议',
          path: '/index/advise',
          isNew: false
        },
        {
          name: '公告',
          path: '/index/notice',
          isNew: false
        },
        {
          name: '动态',
          path: '/index/logs',
          isNew: false
        }
      ],
      isLogin: this.$store.state.isLogin
    }
  }
}
</script>

<style lang="scss" scoped></style>
