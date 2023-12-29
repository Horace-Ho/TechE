<script setup>
  import { ref } from 'vue'
</script>

<template>
  <el-skeleton :rows="5" animated class="skeleton"/>

  <el-skeleton style="width: 240px">
    <template #template>
      <el-skeleton-item variant="image" style="width: 240px; height: 240px" />
      <div style="padding: 14px">
        <el-skeleton-item variant="p" style="width: 50%" />
        <div
            style="
            display: flex;
            align-items: center;
          "
        >
          <el-skeleton-item variant="text" style="margin-right: 16px" />
          <el-skeleton-item variant="text" style="width: 30%" />
        </div>
      </div>
    </template>
  </el-skeleton>

  <el-skeleton :rows="3" animated class="skeleton"/>
  <el-skeleton :rows="3" animated class="skeleton"/>
  <el-skeleton :rows="3" animated class="skeleton"/>
</template>

<style scoped>
  .skeleton{
    margin: 20px 0;
  }
</style>
