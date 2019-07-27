<template>
  <draggable class="row items-start q-gutter-md" v-model="lists">
    <List :data="list" :key="list.id" @delete-list="deleteList" class="col" v-for="list in lists" />

    <q-card class="no-shadow bg-indigo-1 col-auto">
      <q-card-section>
        <!-- New list button -->
        <q-btn @click="showNew = true" color="primary" dense flat icon="add" v-if="!showNew" />

        <!-- New list -->
        <q-form @reset="cancelNewList" @submit="newList" v-else>
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
      </q-card-section>
    </q-card>
  </draggable>
</template>

<script>
import draggable from 'vuedraggable'
import List from './List.vue'

export default {
  name: 'app',
  components: {
    List,
    draggable
  },
  methods: {
    newList () {
      this.lists.push({
        id: this.lists.length,
        title: this.newTitle,
        cards: []
      })
      this.showNew = false
      this.newTitle = ''
    },
    cancelNewList () {
      this.newTitle = ''
      this.showNew = false
    },
    deleteList (e) {
      this.lists.splice(e, 1)
    }
  },
  data () {
    return {
      showNew: false,
      newTitle: '',
      lists: [
        {
          id: 0,
          title: 'Todo',
          cards: [
            {
              id: 0,
              title: 'Account for antimatter modulator',
              description:
                'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse sit amet odio erat.'
            },
            {
              id: 1,
              title: 'Run full diagnostics',
              description:
                'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse sit amet odio erat.',
              duedate: '23.9.2019'
            }
          ]
        },
        {
          id: 1,
          title: 'Doing',
          cards: [
            {
              id: 0,
              title: 'Invert every graviton attractor',
              description:
                'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse sit amet odio erat.',
              duedate: '20.9.2019'
            }
          ]
        },
        {
          id: 2,
          title: 'Review',
          cards: [
            {
              id: 0,
              title: 'Investigate power outages',
              description:
                'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse sit amet odio erat.'
            },
            {
              id: 1,
              title: 'Build the solar panel',
              description:
                'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse sit amet odio erat.',
              duedate: '23.9.2019'
            },
            {
              id: 2,
              title: 'Upduedate documentation and push through channels',
              description:
                'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse sit amet odio erat.'
            },
            {
              id: 3,
              title: 'Recalibrate the anomaly in tachyon catalyst',
              description:
                'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse sit amet odio erat.',
              duedate: '23.9.2019'
            }
          ]
        },
        {
          id: 3,
          title: 'Done',
          cards: [
            {
              id: 0,
              title: 'Add app alert for changed weather events',
              description:
                'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse sit amet odio erat.',
              duedate: '23.9.2019'
            },
            {
              id: 1,
              title: 'Hello world!',
              description:
                'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse sit amet odio erat.'
            }
          ]
        }
      ]
    }
  }
}
</script>
