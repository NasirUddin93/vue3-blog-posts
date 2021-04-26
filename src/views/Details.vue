<template>
    <div>
        <div v-if="error">{{error}}</div>
        <div v-if="post" class="post">
            <h3>{{post.title}}</h3>
            <p>{{post.body}}</p>
            <p class="pre"></p>
        </div>
    </div>
</template>

<script>
import getPost from '../composables/getPost';
export default {
    props:['id'],
    setup(props){
        const {post,error,load} = getPost(props.id)
        load()
        return {post,error}
    }
};
</script>

<style>
.post{
    min-width: 1200px;
    margin: 0 auto;
}
.post p{
    color: #444;
    line-height: 1.5em;
    margin-top: 40px;
}
</style>