<template>
    <div class="division">
        <div>Le prix total : </div>
        <div>{{prix_total}} DH</div>
    </div>
</template>
<script>
export default {
  props: ['product'],
    computed: {
      prix_total() {
        return  this.$store.getters.SomePrixTotal
      }
    }
}
</script>

<style>
  .division {
        background-color: #eb8755;
        color: #1f0e0e;
        padding: 10px;
        font-size: 20px;
        font-weight: bold;
        text-align: center;
        margin-top: 126px;
    }
    div:first-child {
        margin-bottom: 10px;
    }
</style>