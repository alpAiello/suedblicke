<template>
    <ul id="topicList">
        <li
            v-for="topic in topics.data"
            :id="topic.name"
            :key="topic.id"
            class="listItem"
            v-on:click="e => scaleToTopicpage(e)"
        >
            <NuxtLink :to="'/topics/' + topic.id">
                <svg
                    xmlns="http://www.w3.org/2000/svg"
                    class="h-6 w-6 marker"
                    fill="none"
                    viewBox="0 0 24 24"
                    stroke="currentColor"
                >
                    <path
                        stroke-linecap="round"
                        stroke-linejoin="round"
                        stroke-width="{2}"
                        d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"
                    />
                    <path
                        stroke-linecap="round"
                        stroke-linejoin="round"
                        stroke-width="{2}"
                        d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"
                    />
                </svg>
                <h1>{{ topic.topic_name }}</h1>
                <h2>{{ topic.activist_name }}</h2>
                <h2>{{ topic.location }}</h2>
            </NuxtLink>
        </li>
    </ul>
</template>

<script>
export default {
    async asyncData({ $axios }) {
        const topics = await $axios.$get('http://sandy.uber.space/items/topic')
        return { topics }
    }, methods: {
        scaleToTopicpage(e) {
            console.log(e.currentTarget)
        }
    }
}
</script>
<style>
* {
    color: aliceblue;
}
#topicList {
    display: grid;
    width: 100vw;
    height: 100vh;
    grid-template-columns: 1fr 1fr 1fr;
    grid-template-rows: 1fr 1fr 1fr;
    justify-items: center;
    align-items: center;
}
.marker {
    margin: auto;
}
.listItem {
    display: flex;
    width: 30px;
    height: 30px;
    border: solid rgb(131, 78, 255) 30px;
    border-radius: 300px;
    background-color: rgb(131, 78, 255);
    color: rgb(131, 78, 255);
    overflow: hidden;
    text-align: center;
    justify-content: center;
    align-items: center;
}
.listItem:hover {
    transition: all ease 300ms;
    width: 150px;
    height: 150px;
    border: solid rgb(131, 78, 255) 2px;
    border-radius: 10px;
    background-color: rgb(131, 78, 255);
    color: white;
    cursor: pointer;
}
</style>