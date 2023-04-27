<template>
<div class="error">
  <p>{{ message }}</p>
</div>
</template>
<script>
export default {
    name:'ErrorView',
    props : {
        message : {
            type: String
        }
    }
}
</script>
<style>
.error {
  background-color: #f8d7da;
  border-color: #f5c6cb;
  color: #721c24;
  padding: 10px;
  border: 1px solid transparent;
  border-radius: 4px;
  margin-bottom: 10px;
}

.error p {
  margin: 0;
  font-size: 14px;
  line-height: 1.5;
}
</style>