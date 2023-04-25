<template>
    <div>
        <div>le prix que vous devais payées : </div>
        <div>{{test}}</div>
    </div>
</template>
<script>
export default {
  props: ['product'],
    computed: {
      test() {
        return  this.$store.getters.SomePrixTotal
      }
    }
}
</script>