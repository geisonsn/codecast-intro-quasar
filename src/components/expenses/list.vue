<template>
    <div>
        <div class="expense" v-for="expense in list" :key="expense.id">
            <p>{{ expense.date }} - R$ {{ expense.amount }}</p>
            <p>{{ expense.description }}</p>
        </div>
    </div>
</template>

<script>
export default {
    computed: {
        list () {
            return this.$store.state.Expenses.list
        }
    }
}
</script>

<style scoped>
.expense {
    border-bottom: #999 1px solid;
    padding-top: 10px;
}
</style>
