<template>
  <div class="container">
    <zk-auto-form viewApi="Api/Recharge/GetRechargeView" />
    <zk-auto-form viewApi="api/users/getregform" />
  </div>
</template>

<script>
  import zkAutoForm from '@/components/core/zk-auto-form'

  export default {
    components: {
      zkAutoForm
    },
    data () {
      return {
        clientType: ''
      }
    },
    mounted () {
      this.ApiGet()
    },
    methods: {
      async ApiGet () {
      }
    }
  }
</script>

<style scoped lang="less">
</style>
