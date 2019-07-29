<template>
  <div>
    <q-card @click="openCard = true" class="q-mb-sm">
      <q-card-section>
        <div class="text-body2">{{ data.title }}</div>

        <div class="row items-center text-caption text-grey-7 q-pt-xs" v-if="data.duedate">
          <q-icon class="q-mr-xs" name="timer" />
          <span>{{ data.duedate }}</span>
        </div>
      </q-card-section>
    </q-card>

    <q-dialog v-model="openCard">
      <CardModal :data="data" />
    </q-dialog>
  </div>
</template>

<script>
import CardModal from './CardModal'

export default {
  name: 'Card',
  props: ['data'],
  components: {
    CardModal
  },
  data () {
    return {
      openCard: false
    }
  }
}
</script>

<style>
</style>
