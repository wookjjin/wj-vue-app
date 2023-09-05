<script setup lang="ts">
import { NCard, NDataTable } from "naive-ui"
import { ref } from 'vue'

function createCols() {
  return [
    {
      title: 'Name',
      key: 'name',
      minWidth: '20vw',
      maxWidth: '50vw'
    },
    {
      title: 'Attrs',
      key: 'attrs',
      children: [
        {
          title: 'Attack',
          key: 'attack',
          children: [
            {
              title: 'Physics Attack',
              key: 'physicsAttack'
            },
            {
              title: 'Magic Attack',
              key: 'magicAttack'
            }
          ]
        },
        {
          title: 'Defend',
          key: 'defend'
        },
        {
          title: 'Speed',
          key: 'speed'
        }
      ]
    }
  ]
}

function createData() {
  return Array.from({ length: 50 }).map((_, i) => {
    return {
      key: i,
      name: `name_${i}`,
      physicsAttack: `physicsAttack_${i}`,
      magicAttack: `magicAttack_${i}`,
      defend: `defend_${i}`,
      speed: `speed_${i}`
    }
  })
}
const data = ref(createData())
const columns = ref(createCols())
const pagination = ref({
  pageSize: 10
})
</script>
<template>
  <n-card title="POC of Table">
    <n-data-table :data="data" :columns="columns" :single-line="false" :pagination="pagination" />
  </n-card>
</template>

<style scoped>
.n-card {
  min-width: 300px;
  max-width: 100vw;
  overflow: auto;
}
</style>