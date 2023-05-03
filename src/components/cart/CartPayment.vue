<template>
  <div class="division">
    <el-popover
      placement="top-start"
      title="PRIX TOTAL EN EURO "
      :width="200"
      trigger="hover"
      :content="popoverContent"
    >
      <template #reference>
        
        <el-button class="m-2"> Prix Total : {{prix_total}} dh</el-button>
      </template>
    </el-popover>
  </div>
</template>

<script>
export default {
  props: ['product'],
  data() {
    return {
      popoverContent: this.$store.getters.SomePrixTotal / 10 + " $",
    };
  },
  computed: {
    prix_total() {
      return this.$store.getters.SomePrixTotal;
    },
  },
  watch: {
    prix_total() {
      this.popoverContent = this.$store.getters.SomePrixTotal;
    },
  },
};
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


</style>
