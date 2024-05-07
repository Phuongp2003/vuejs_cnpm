<script setup>
import { ref, watchEffect } from 'vue'
const props = defineProps({
    projectName: String
});
const API_URL = `https://api.github.com/repos/${props.projectName}/commits?per_page=5&sha=`
const branches = ['main']

const currentBranch = ref(branches[0])
const commits = ref(null)

watchEffect(async () => {
    // this effect will run immediately and then
    // re-run whenever currentBranch.value changes
    const url = `${API_URL}${currentBranch.value} `
    commits.value = await (await fetch(url)).json()
    console.log(commits.value)
})

function truncate(v) {
    const newline = v.indexOf('\n')
    return newline > 0 ? v.slice(0, newline) : v
}

function formatDate(v) {
    return v.replace(/T|Z/g, ' ')
}
</script>

<template>
    <div class="py-5 container">
        <h1 class="text-success">Các thay đổi cuối cùng của {{ projectName }} </h1>
        <template v-for="branch in branches" v-show="branches.length > 1">
            <input type="radio" :id="branch" :value="branch" name="branch" v-model="currentBranch"
                v-show="branches.length > 1">
        </template>
        <div v-if="commits" style="padding: 0 20px;">
            <ul>
                <li v-for="{ html_url, sha, author, commit } in commits">
                    <a :href="html_url" target="_blank" class="commit">{{ sha.slice(0, 7) }}</a>
                    - <span class="message">{{ truncate(commit.message) }}</span><br>
                    Người thay đổi: <span class="author">
                        <a :href="author.html_url" target="_blank">{{ commit.author.name }}</a>
                    </span> <br>
                    Thời gian: <span class="date">{{ formatDate(commit.author.date) }}</span>
                </li>
            </ul>
        </div>
        <div v-else>Loading...</div>
    </div>
</template>

<style>
* {
    color: white
}

a {
    text-decoration: none;
    color: #42b883;
}

li {
    line-height: 1.5em;
}

.author,
.date {
    font-weight: bold;
}
</style>
