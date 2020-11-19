<template>
  <div class="web-toast" v-if="current" ref="toast">
    <dl>
      <dt>
        <img :src="current.url" />
      </dt>
      <dd>
        <p>{{ text }}</p>
      </dd>
    </dl>
  </div>
</template>
<script>
export default {
  name: "lx-tips",
  computed: {
    text: function() {
      return this.current && this.current.name + this.current.info;
    },
  },
  data: function() {
    return {
      list: [
        {
          name: "张三",
          url:
            "https://assets.gitlab-static.net/uploads/-/system/user/avatar/6358963/avatar.png?width=23",
          info: "刚刚浏览过",
        },
        {
          name: "李四",
          url:
            "https://assets.gitlab-static.net/uploads/-/system/user/avatar/6358963/avatar.png?width=23",
          info: "购买了此商品",
        },
        {
          name: "赵武",
          url:
            "https://assets.gitlab-static.net/uploads/-/system/user/avatar/6358963/avatar.png?width=23",
          info: "刚刚浏览过",
        },
        {
          name: "LiLi",
          url:
            "https://assets.gitlab-static.net/uploads/-/system/user/avatar/6358963/avatar.png?width=23",
          info: "购买了此商品",
        },
        {
          name: "aaa",
          url:
            "https://assets.gitlab-static.net/uploads/-/system/user/avatar/6358963/avatar.png?width=23",
          info: "刚刚浏览过",
        },
        {
          name: "bbb",
          url:
            "https://assets.gitlab-static.net/uploads/-/system/user/avatar/6358963/avatar.png?width=23",
          info: "购买了此商品",
        },
        {
          name: "ccc",
          url:
            "https://assets.gitlab-static.net/uploads/-/system/user/avatar/6358963/avatar.png?width=23",
          info: "刚刚浏览过",
        },
        {
          name: "ddd",
          url:
            "https://assets.gitlab-static.net/uploads/-/system/user/avatar/6358963/avatar.png?width=23",
          info: "购买了此商品",
        },
        {
          name: "eee",
          url:
            "https://assets.gitlab-static.net/uploads/-/system/user/avatar/6358963/avatar.png?width=23",
          info: "刚刚浏览过",
        },
        {
          name: "fff",
          url:
            "https://assets.gitlab-static.net/uploads/-/system/user/avatar/6358963/avatar.png?width=23",
          info: "购买了此商品",
        },
      ],
      current: null,
    };
  },
  methods: {
    initToast() {
      const idx = Math.floor(Math.random() * 10);
      this.current = arr[idx];
      var el = this.$refs.toast;
      el.classList.add("fadeIn");
      el.classList.remove("fadeIn");
      el.classList.add("fadeOut");
      el.addEventListener("animationend", function() {});
    },
  },
  mounted: function() {
    setInterval(() => {}, 4000);
  },
};
</script>

<style>
.web-toast {
  position: fixed;
  background: rgba(0, 0, 0, 0.7);
  color: #fff;
  font-size: 14px;
  line-height: 1;
  padding: 4px 10px;
  border-radius: 20px;
  left: 20px;
  top: 20px;
  z-index: 9999;
  white-space: nowrap;
}

.web-toast dl {
  display: flex;
  height: 24px;
  align-items: center;
  margin: 0;
}

.web-toast dl dt {
  width: 16px;
  height: 16px;
  margin-right: 8px;
  border-radius: 50%;
  overflow: hidden;
}

.web-toast dl dt img {
  width: 16px;
  height: 16px;
}

.web-toast dl dd {
  margin: 0;
  font-size: 12px;
}

.fadeOut {
  animation: fadeOut 3.2s;
}

.fadeIn {
  animation: fadeIn 0.5s;
}

@keyframes fadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

@keyframes fadeOut {
  0% {
    opacity: 1;
  }
  60% {
    opacity: 0.9;
  }
  100% {
    opacity: 0;
  }
}
</style>
