<template>
    <ul id="topicList">
        <li v-for="topic in topics.data" :key="topic.id" class="listItem">
            <NuxtLink :to="'/topics/' + topic.id">
                <p>{{ topic.activist_name }}</p>
                <p>{{ topic.location }}</p>
                <p>{{ topic.topic_name }}</p>
            </NuxtLink>
        </li>
    </ul>
</template>

<script>
export default {
    async asyncData({ $axios }) {
        const topics = await $axios.$get('http://sandy.uber.space/items/topic')
        return { topics }
    }
}
</script>
<style>
#topicList {
    display: grid;
    width: 100vw;
    height: 100vh;
    grid-template-columns: 1fr 1fr 1fr;
    grid-template-rows: 1fr 1fr 1fr;
    justify-items: center;
    align-items: center;
}
.listItem {
    display: flex;
    width: 30px;
    height: 30px;
    border: solid rgb(131, 78, 255) 2px;
    border-radius: 300px;
    background-color: rgb(131, 78, 255);
    color: rgb(131, 78, 255);
    overflow: hidden;
    text-align: center;
    justify-content: center;
    align-items: center;
}
.listItem:hover {
    transition: all ease 1s;
    width: 150px;
    height: 150px;
    border: solid rgb(131, 78, 255) 2px;
    border-radius: 10px;
    background-color: rgb(131, 78, 255);
    color: white;
    cursor: pointer;
}
</style>