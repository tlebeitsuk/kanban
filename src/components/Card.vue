<template>
  <q-card class="q-mb-sm">
    <q-card-section>
      <div class="text-body2">{{ data.title }}</div>
      <div class="text-caption" v-if="data.duedate">{{ data.duedate }}</div>
    </q-card-section>
  </q-card>
</template>

<script>
export default {
  name: 'Card',
  props: ['data'],
  data () {
    return {}
  }
}
</script>

<style>
</style>
