<template>
  <q-card class="no-shadow bg-indigo-1" style="max-width: 380px">
    <q-card-section>
      <div class="row items-center no-wrap">
        <div class="col">
          <div
            @click="editTitle = true"
            class="text-subtitle1 text-weight-medium"
            v-if="!editTitle"
          >{{ data.title }}</div>
          <!-- Edit title -->
          <q-form @reset="cancelNewTitle" @submit="saveTitle" v-else>
            <div class="row items-center no-wrap">
              <div class="col q-mr-sm">
                <q-input autofocus dense outlined v-model="newTitle" />
              </div>
              <div class="col-auto">
                <q-btn color="primary" dense flat icon="close" type="reset" />
                <q-btn color="primary" dense flat icon="done" type="submit" />
              </div>
            </div>
          </q-form>
        </div>
        <div class="col-auto" v-if="!editTitle">
          <q-btn @click="deleteList(data)" color="primary" dense flat icon="delete_outline" />
          <q-btn @click="newCard(data)" color="primary" dense flat icon="playlist_add" />
        </div>
      </div>
    </q-card-section>
    <q-card-section v-if="data.cards.length > 0">
      <draggable group="cards">
        <Card :data="card" :key="card.id" v-for="card in data.cards" />
      </draggable>
    </q-card-section>
  </q-card>
</template>

<script>
import draggable from 'vuedraggable'
import Card from './Card.vue'

export default {
  name: 'List',
  props: ['data'],
  components: {
    draggable,
    Card
  },
  data () {
    return {
      editTitle: false,
      newTitle: this.data.title
    }
  },
  methods: {
    saveTitle () {
      this.data.title = this.newTitle
      this.editTitle = false
    },
    cancelNewTitle () {
      this.newTitle = this.data.title
      this.editTitle = false
    },
    newCard (list) {
      list.cards.push({
        id: list.cards.length,
        date: new Date().toLocaleDateString('fi-FI'),
        title: 'New #' + Math.floor(Math.random() * 100),
        description:
          'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse sit amet odio erat.'
      })
    },
    deleteList () {
      this.$emit('delete-list', this.data.id)
    }
  }
}
</script>

<style scoped>
</style>
