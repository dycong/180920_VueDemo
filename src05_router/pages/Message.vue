<template>
  <div>
    <ul>
      <li v-for="m in messages" :key="m.id">
        <router-link :to="`/home/message/detail/${m.id}`">{{m.title}}</router-link>
        &nbsp;<button @click="$router.push(`/home/message/detail/${m.id}`)">push查看</button>
        &nbsp;<button @click="$router.replace(`/home/message/detail/${m.id}`)">replace查看</button>
      </li>
    </ul>
    <button @click="$router.back()">回退</button>
    <hr>
    <router-view/>
  </div>
</template>

<script>
  export default {
    data () {
      return {
        messages: []
      }
    },

    mounted () {
      // 模拟发异步ajax请求获取数据
      setTimeout(() => {
        const messages = [
          {id: 1, title: 'message001'},
          {id: 3, title: 'message003'},
          {id: 5, title: 'message005'},
        ]
        // 更新状态数据
        this.messages = messages
      }, 1000)
    }
  }
</script>

<style scoped>

</style>
