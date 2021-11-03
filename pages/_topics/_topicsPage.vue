<template>
    <div>
        <NuxtLink to="/">back</NuxtLink>
        <h1>{{ topic.topic_name }}</h1>
        <h2>{{ topic.activist_name }}</h2>
        <p>{{ topic.location }}</p>
        <div v-html="topic.activist_text"></div>
        <a :href="assetsUrl + topic.material" target="_blank">download material</a>
        <audio :src="assetsUrl + topic.podcast" controls></audio>
        <video :src="assetsUrl + topic.video" controls></video>
        <p>{{ topic.taging }}</p>
    </div>
</template>
<script>
export default {
    async asyncData({ $axios, params }) {
        const topicId = await params.topicsPage
        const topics = await $axios.$get('http://sandy.uber.space/items/topic')
        const topic = topics.data.filter(topic => { return topicId === topic.id })[0]
        const assetsUrl = "https://sandy.uber.space/assets/"
        return {
            assetsUrl,
            topics,
            topicId,
            topic,
        }
    },
}
</script>
<style>
</style>
            
            
            
            
            
            
            
            
            
            
            