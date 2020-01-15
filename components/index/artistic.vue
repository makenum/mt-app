<template>
  <section class="m-istyle">
    <dl>
      <dt>有格调</dt>
      <dd
        v-for="(item, index) in tabList"
        :key="index"
        :kind="item.type"
        :class="{ active: kind === item.type }"
        @mouseenter="enter"
      >
        {{ item.name }}
      </dd>
    </dl>
    <ul class="ibody">
      <li v-for="item in cur" :key="item.title">
        <el-card :body-style="{ padding: '0px' }" shadow="never">
          <img :src="item.img" class="image" />
          <ul class="cbody">
            <li class="title">{{ item.title }}</li>
            <li class="pos">
              <span>{{ item.pos }}</span>
            </li>
            <li class="price">
              ￥<em>{{ item.price }}</em>
              <span>/起</span>
            </li>
          </ul>
        </el-card>
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  data() {
    return {
      kind: 'all',
      tabList: [
        {
          type: 'all',
          name: '全部'
        },
        {
          type: 'part',
          name: '约会聚餐'
        },
        {
          type: 'spa',
          name: '丽人SPA'
        },
        {
          type: 'movie',
          name: '电影演出'
        },
        {
          type: 'travel',
          name: '品质出游'
        }
      ],
      list: {
        all: [
          {
            title: '端午节畅玩特价酒店抢订中',
            img:
              'http://p0.meituan.net/codeman/00c8bc1c25fbcc6d0651b29a2057a8c1560658.png',
            pos: '北京路',
            price: 60
          }
        ],
        part: [
          {
            title: '端午节畅玩特价酒店抢订中',
            img:
              'http://p0.meituan.net/codeman/00c8bc1c25fbcc6d0651b29a2057a8c1560658.png',
            pos: '北京路',
            price: 70
          }
        ],
        spa: [
          {
            title: '端午节畅玩特价酒店抢订中',
            img:
              'http://p0.meituan.net/codeman/00c8bc1c25fbcc6d0651b29a2057a8c1560658.png',
            pos: '北京路',
            price: 80
          }
        ],
        movie: [
          {
            title: '端午节畅玩特价酒店抢订中',
            img:
              'http://p0.meituan.net/codeman/00c8bc1c25fbcc6d0651b29a2057a8c1560658.png',
            pos: '北京路',
            price: 90
          }
        ],
        travel: [
          {
            title: '端午节畅玩特价酒店抢订中',
            img:
              'http://p0.meituan.net/codeman/00c8bc1c25fbcc6d0651b29a2057a8c1560658.png',
            pos: '北京路',
            price: 100
          }
        ]
      }
    }
  },
  computed: {
    cur() {
      return this.list[this.kind]
    }
  },
  methods: {
    enter(e) {
      this.kind = e.target.attributes.kind.value
    }
  }
}
</script>
<style lang="scss">
@import '@/assets/css/index/artistic.scss';
</style>
