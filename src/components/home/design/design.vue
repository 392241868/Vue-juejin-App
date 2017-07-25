<template>
  <div>
    <newslist ref="newslist"></newslist>
  </div>
</template>

<script>
  import {ERR_OK} from 'api/config'
  import newslist from 'base/newslist/newslist'

  export default {
    data() {
        return {
          find: {
            type: Object
          },
        };
    },
    props: {

    },
    created() {
      this.$http.get('./api/find').then((response) => {
          response = response.body;
          if (response.errno === ERR_OK) {
            this.find = response.data;
          }
      });
    },
    methods: {

    },
    components: {
      newslist
    }
  }
</script>

<style>

</style>
