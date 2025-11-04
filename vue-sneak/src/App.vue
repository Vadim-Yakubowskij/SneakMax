<template>
    <div class="app">
        <post-form
            @create="createPost"
        />
        <post-list 
            :posts="posts"
        />
    </div>
</template>

<script>
import PostForm from './components/PostForm.vue';
import PostList from './components/PostList.vue';
export default {
    components:{
        PostForm, PostList
    },
    data(){
        return{
            posts:[
                {id:1, title: 'JS 1', body: 'Описание поста 1'},
                {id:2, title: 'JS 2', body: 'Описание поста 2'},
                {id:3, title: 'JS 3', body: 'Описание поста 3'},
            ],
        }
    },

    methods: {
        createPost(post){
           this.posts.push(post);
        },
        
    }
}
</script>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
.app{
    padding: 20px;
}
form{
    display: flex;
    flex-direction: column;
}
.input{
    width: 100%;
    border: 1px solid teal;
    padding: 10px 15px;
    margin-top: 15px;
}
.btn{
    margin-top: 15px;
    align-self: flex-end;
    padding: 10px 15px;
    background: none;
    color: teal;
    border: 1px solid teal;
}

</style>