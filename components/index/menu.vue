<template>
  <div class="m-menu">
    <dl
      class="nav"
      @mouseleave="mouseleave"
    >
      <dt>全部分类</dt>
      <dd
        @mouseenter="enter"
        v-for="(item, index) in menu"
        :key="index"
      >
        <i :class="item.type" />{{ item.name }}<span class="arrow" />
      </dd>
    </dl>

    <div
      class="detail"
      v-if="kind"
      @mouseenter="sover"
      @mouseleave="sout"
    >
      <template v-for="(item, index) in curdetail.child">
        <h4 :key="index">{{ item.title }}</h4>
        <span
          v-for="(child, index) in item.child"
          :key="index"
        >{{
          child
        }}</span>
      </template>
    </div>
  </div>
</template>


<script>
export default {
  data () {
    return {
      kind: "",
      menu: [
        {
          type: "food",
          name: "美食",
          child: [
            {
              title: "美食",
              child: ["1111", "2222", "33333"]
            }
          ]
        },
        {
          type: "takeout",
          name: "外卖",
          child: [
            {
              title: "外卖",
              child: ["美团外卖"]
            }
          ]
        },
        {
          type: "hotel",
          name: "酒店",
          child: [
            {
              title: "酒店星级",
              child: ["1111", "2222", "33333"]
            }
          ]
        }
      ]
    };
  },
  computed: {
    curdetail () {
      return this.menu.filter(item => item.type === this.kind)[0];
    }
  },
  methods: {
    mouseleave () {
      let self = this;
      console.log(self);
      self._timer = setTimeout(() => {
        self.kind = "";
      }, 150);
    },
    enter (e) {
      this.kind = e.target.querySelector('i').className
      console.log(this.kind);
      
    },
    sover(){
      clearTimeout(this._timer)
    },
    sout(){
      this.kind=''
      
    }
  }
};
</script>

<style lang="scss">
@import "@/assets/css/index/index.scss";
</style>
