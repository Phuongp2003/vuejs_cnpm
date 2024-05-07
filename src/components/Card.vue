<script setup>
</script>


<template>
    <div class="card card-cover h-100 overflow-hidden text-bg-dark rounded-4 shadow-lg"
        :style="{ 'background-image': 'url(' + backgroundImage + ')' }">
        <div class="d-flex flex-column h-100 p-5 pb-3 text-white text-shadow-1 card-content">
            <h3 class="pt-5 mt-5 mb-4 display-6 lh-1 fw-bold"> {{ title }} </h3>
            <ul class="d-flex list-unstyled mt-auto">
                <li class="me-auto">
                    <img :src="icon" alt="Bootstrap" width="32" height="32"
                        class="rounded-circle border border-white" />
                </li>
                <li class="d-flex align-items-center me-3">
                    <small>{{ tool }}</small>
                </li>
            </ul>
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
    name: 'Card',
    props: {
        title: {
            type: String
        },
        tool: {
            type: String
        },
        backgroundImage: {
            type: String
        },
        icon: {
            type: String
        }
    }
};
</script>
