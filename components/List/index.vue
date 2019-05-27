<template>
  <a-list
    class="main-list"
    itemLayout="vertical"
    size="large"
    :pagination="pagination"
    :dataSource="listData"
  >
    <div slot="footer">人家是有底线的...</div>
    <a-list-item slot="renderItem" slot-scope="item" key="item.title">
      <template slot="actions" v-for="{type, text} in actions">
        <span :key="type">
          <a-icon :type="type" style="margin-right: 8px" />
          {{text}}
        </span>
      </template>
      <img slot="extra" height="100" alt="logo" src="../../assets/piece-bird.png" />
      <a-list-item-meta
        :description="item.description"
      >
        <a slot="title" :href="item.href">{{item.title}}</a>
        <a-avatar slot="avatar" :src="item.avatar" />
      </a-list-item-meta>
      {{item.content}}
    </a-list-item>
  </a-list>
</template>
<script>
const listData = []
for (let i = 0; i < 23; i++) {
  listData.push({
    href: 'https://vue.ant.design/',
    title: `我所有的向往`,
    avatar: '#####',
    description: '以梦为酒，敬为了梦想执着的人',
  })
}

export default {
  data () {
    return {
      listData,
      pagination: {
        onChange: (page) => {
          console.log(page);
        },
        pageSize: 5,
      },
      actions: [
        { type: 'heart', text: '156' },
        { type: 'like-o', text: '156' },
        { type: 'message', text: '2' },
      ],
    }
  },
}
</script>
<style>
.main-list {
  margin-bottom: 10px;
}
.ant-list-item:hover {
  background: rgb(212, 192, 238)
;
}
</style>
