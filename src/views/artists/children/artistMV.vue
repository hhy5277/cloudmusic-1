<template>
  <div>
    <mv-list :allMV="allMV"></mv-list>
    <p v-if="allMV.length === 0">该歌手没还没有mv</p>
  </div>
</template>

<script>
  import mvList from '../../../components/mvList'
  export default {
    data () {
      return {
        allMV: []
      }
    },
    components: {
      mvList
    },
    mounted () {
      // 获取歌手 mv
      this.$http.get(`http://localhost:5000/artist/mv?id=${this.$route.params.id}`)
        .then((res) => {
          this.allMV = res.data.mvs
        })
    }
  }
</script>

<style lang="scss" scoped>
  
</style>
