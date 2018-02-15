<template>
    <div>
        <div class="expense" v-for="expense in list" :key="expense.id">
            <p>{{ expense.date }} - R$ {{ expense.amount }}</p>
            <p>{{ expense.description }}</p>
            <a href="#" @click.prevent="askRemove(expense)" class="removeLink">remover</a>
        </div>
    </div>
</template>

<script>
import { Dialog } from 'quasar'
export default {
    computed: {
        list () {
            return this.$store.state.Expenses.list
        }
    },
    methods: {
        remove (expense) {
					this.$store.commit('REMOVE_EXPENSE', expense)
				},
				askRemove (expense) {
					let self = this
					Dialog.create({
						title: 'Remover despesa',
						message: 'Confirma a remoção da despesa?',
						buttons: [
								{
									label: 'Não'
								}, 
								{
									label: 'Sim',
									handler () {
										self.remove(expense)
									}
								}
						]
					})
				}
    }
}
</script>

<style scoped>
.expense {
    border-bottom: #999 1px solid;
    padding-top: 10px;
    position: relative;
}
.removeLink {
    color: #c00000;
    position: absolute;
    bottom: 10px;
    right: 0;
    font-size: 0.8em;
}
</style>
