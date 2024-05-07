<script setup>
import Card from './Card.vue'
</script>


<template>
    <div class="container px-4 py-5" id="custom-cards" data-bs-theme="dark">
        <h2 class="pb-2 border-bottom text-success">{{ title }}</h2>
        <div class="row row-cols-1 row-cols-lg-3 align-items-stretch g-4 py-5">
            <div class="col" v-for="card in cards">
                <Card :title="card.name" :tool="card.tool" :backgroundImage="card.image" :icon="card.icon"
                    @click="sendDataToParent(card.id)" />
            </div>
        </div>
    </div>
</template>

<style scoped>
.card-content {
    background: linear-gradient(rgba(0, 0, 0, 0) 30%, rgba(0, 0, 0, 0.6) 80%);
}
</style>

<script>
export default {
    name: 'Cards',
    props: {
        cards: [
            {
                name: String,
                tool: String,
                image: String,
                icon: String,
                id: Number
            }
        ],
        title: String
    },
    methods: {
        sendDataToParent(value) {
            this.$emit('cpage', value);
        },
    },
};
</script>
