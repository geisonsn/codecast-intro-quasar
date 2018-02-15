<template>
    <div>
        <div class="expense" v-for="expense in list" :key="expense.id" @click="toggle(expense)">
            <p :class="{ done: expense.done }">{{ expense.date }} - R$ {{ expense.amount }}</p>
            <p :class="{ done: expense.done }">{{ expense.description }}</p>
            <a href="#" @click.prevent="askRemove(expense)" class="removeLink">remover</a>
        </div>
    </div>
</template>

<script>
import { Dialog } from 'quasar'
import { setDone } from '../../persistence'
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
				},
				toggle (expense) {
					expense.done = !expense.done
					setDone(expense)
				}
    }
}
</script>

<style scoped>
.done {
	text-decoration: line-through;
	color: #ccc;
}
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
