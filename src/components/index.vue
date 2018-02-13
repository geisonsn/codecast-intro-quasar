<template>
  <q-layout>
    <q-toolbar>

      <q-toolbar-title>
        Despesas em Dinheiro Vivo
      </q-toolbar-title>
    </q-toolbar>

    <div class="container">
      <cc-form></cc-form>
      <hr v-show="list.length > 0"/>
      <cc-list></cc-list> 
    </div>

  </q-layout>
</template>

<script>
import {
  QLayout,
  QToolbar,
  QToolbarTitle,
  QBtn,
  QIcon,
  QList,
  QListHeader,
  QItem,
  QItemSide,
  QItemMain
} from 'quasar'
import CcForm from './expenses/form.vue'
import CcList from './expenses/list.vue'

export default {
  name: 'index',
  components: {
    QLayout,
    QToolbar,
    QToolbarTitle,
    QBtn,
    QIcon,
    QList,
    QListHeader,
    QItem,
    QItemSide,
    QItemMain,
    CcForm,
    CcList
  },
  computed: {
        list () {
            return this.$store.state.Expenses.list
        }
    }
}
</script>

<style scoped>
.container {
  padding: 20px;
}
</style>
