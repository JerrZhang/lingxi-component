<template>
  <div v-if="current">
    <div class="web-toast" ref="toast">
      <dl>
        <dt>
          <img :src="current.avatar" />
        </dt>
        <dd>
          <p>{{ text }}</p>
        </dd>
      </dl>
    </div>
  </div>
</template>
<script>
export default {
  name: "lx-tips",
  props: {
    remoteUrl: {
      default: "https://devproxy.getlingxi.com/ybc/api/order-users/latest-list",
      desc: "远程服务地址",
    },
    suffixText: {
      default: "已抢先购买",
      desc: "后缀文案",
    },
    duration: {
      default: "4",
      desc: "动画显示周期（秒）",
    },
  },
  computed: {
    text: function() {
      return this.current && this.current.nickname + " " + this.suffixText;
    },
  },
  data: function() {
    return {
      list: [
        {
          avatar:
            "https://assets.gitlab-static.net/uploads/-/system/user/avatar/6358963/avatar.png?width=23",
          nickname: "张三",
        },
      ],
      current: null,
      timer: null,
    };
  },
  methods: {
    initToast() {
      const idx = Math.floor(Math.random() * this.list.length);
      this.current = this.list[idx];
      if (!this.current) {
        return;
      }
      setTimeout(() => {
        var el = this.$refs.toast;
        console.log(this.$refs);
        el.classList.add("fadeIn");
        el.classList.remove("fadeIn");
        el.classList.add("fadeOut");
        el.addEventListener("animationend", () => {
          this.current = null;
          el.classList.remove("fadeOut");
        });
      });
    },
    fetchUserInfo: function() {
      if (!this.remoteUrl) {
        return;
      }
      var xhr = new XMLHttpRequest();
      xhr.open("get", this.remoteUrl);
      var self = this;
      xhr.onreadystatechange = function() {
        console.log(xhr.readyState);
        if (xhr.readyState === 4) {
          self.list = JSON.parse(xhr.responseText)["paidUsers"];
        }
      };
      xhr.send(null);
    },
  },
  created: function() {
    this.fetchUserInfo();
  },
  mounted: function() {
    this.timer = setInterval(() => {
      this.initToast();
    }, +this.duration * 1000);
  },
  beforeDestroy: function() {
    clearInterval(this.timer);
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
