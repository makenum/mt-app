<template>
  <div class="m-menu">
    <dl @mouseleave="leave" class="nav">
      <dt>全部分类</dt>
      <dd v-for="(item, index) in menu" :key="index" @mouseenter="enter">
        <i :class="item.type" />{{ item.name }}<span class="arrow" />
      </dd>
    </dl>
    <div v-if="kind" @mouseenter="sover" @mouseleave="sout" class="detail">
      <template v-for="(item, index) in curdetail.child">
        <div :key="index">
          <h4>{{ item.title }}</h4>
          <span v-for="v in item.child" :key="v">{{ v }}</span>
        </div>
      </template>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      kind: '',
      menu: [
        {
          type: 'food',
          name: '美食',
          child: [
            {
              title: '美食',
              child: ['代金券', '甜点饮品', '火锅', '自助餐', '小吃快餐']
            }
          ]
        },
        {
          type: 'takeout',
          name: '外卖',
          child: [
            {
              title: '外卖',
              child: ['美团外卖', '饿了么外卖']
            }
          ]
        },
        {
          type: 'hotel',
          name: '酒店',
          child: [
            {
              title: '酒店星级',
              child: ['经济型', '舒适/三星', '高端/四星', '豪华/五星']
            }
          ]
        }
      ]
    }
  },
  computed: {
    curdetail() {
      return this.menu.filter((item) => item.type === this.kind)[0]
    }
  },
  methods: {
    leave() {
      this.timer = setTimeout(() => {
        this.kind = ''
      }, 150)
    },
    enter(e) {
      this.kind = e.target.querySelector('i').className
    },
    sover() {
      clearTimeout(this.timer)
    },
    sout() {
      this.kind = ''
    }
  }
}
</script>
<style lang="scss"></style>
