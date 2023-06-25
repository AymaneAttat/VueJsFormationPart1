<template lang="">
    <div class="card my-3">
        <img class="card-img-top" :src="course.image" :alt="course.title"><!-- <img class="card-img-top" :src="image" :alt="title"> -->
        <div class="card-body">
            <h4 class="card-title">{{course.title}}</h4><!-- <h4 class="card-title">{{title}}</h4> -->
            <p class="card-text">Lorem ipsum dolor sit amet consectetur...</p>
            <button class="btn btn-sm btn-danger" @click="deleteOne(course.id)">Delete</button>
            <button class="btn btn-sm btn-dark ms-1">{{course.category}}</button>
            <div class="my-3">
                <span class="badge rounded-pill bg-primary ms-2" v-for="tag in course.tags">{{tag}}</span>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    props: ['course'],
    //props: ['title', 'image']
    methods: {
        deleteOne(id) {
            //alert('delete')
            this.$emit('delete', id)
        }
    },
}
</script>
<style lang="">
    
</style>