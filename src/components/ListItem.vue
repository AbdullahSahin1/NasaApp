<template>
    <div class="card">
        {{ item }}
        <img :src="item.links[0].href">
        <div class="container">
            <h4>{{ item.data[0].title }}</h4>
            <p>{{item.data[0].description }}</p>
            <div class="tags">
                <div class="tag-item" v-for="tag in item.data[0]?.keywods?.slice(0,3)" >
                    {{ tag }}
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  props: {
  },
    name: 'ListItem'
}
</script>
    <style scoped>
    .card{
        border: 2px solid #fc3d21;
        box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.5);
        transition: .5s;
        width:100%;
        border-radius: 16px;
        width: 100%;
    }
    .card > img{
        height: 300px;
        object-fit: fill;
        border-top-left-radius: 16px;
        border-top-right-radius: 16px;
    }
    .card :hover{
        box-shadow:  0 8px 16px 0 rgba(0, 0, 0, 0.8);
    }
    p{
        overflow: hidden;
        text-overflow: ellipsis;
        display: -webkit-box;
        -webkit-box-orient: vertical;
        -webkit-line-clamp: 1;
        color: #fff;
    }
</style>
