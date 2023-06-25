<template lang="">
<form @submit.prevent="newCourse">
    <div class="form-group">
        <label for="Title">Title</label>
        <!-- <input ref="title" id="Title" type="text" class="form-control"> -->
        <input v-model="title" id="Title" type="text" class="form-control">
    </div>
    <div class="form-group">
        <label for="Image">Image url</label>
        <!-- <input ref="image" id="Image" type="text" class="form-control"> -->
        <input v-model="image" id="Image" type="text" class="form-control">
    </div>
    <div class="form-group">
        <label for="category">Category</label>
        <select v-model="category" id="category" class="form-control">
            <option v-for="cat in categories" :value="cat.id">{{cat.name}}</option>
        </select>
    </div>
    <div class="form-check form-check-inline">
        <input v-model="typeOfPayment" class="form-check-input" type="radio" name="typeOfPayment" value="free" checked>
        <label class="form-check-label" for="inlineRadio1">Free</label>
    </div>
    <div class="form-check form-check-inline">
        <input v-model="typeOfPayment" class="form-check-input" type="radio" name="typeOfPayment" value="paying">
        <label class="form-check-label" for="inlineRadio2">Paying</label>
    </div>
    <div class="form-check form-check-inline">
        <input class="form-check-input" type="radio" name="typeOfPayment" value="option3" disabled>
        <label class="form-check-label" for="inlineRadio3">3 (disabled)</label>
    </div>
    <div class="form-check">
      <label class="form-check-label">
        <input type="checkbox" class="form-check-input" v-model="published" checked>
        Published
      </label>
    </div>
    <div class="my-3">
        <h5>Tags</h5>
        <div class="form-check" v-for="tag in tags">
          <label class="form-check-label">
            <input type="checkbox" class="form-check-input" :value="tag" v-model="myTags">
            {{tag}}
          </label>
        </div>
    </div>
    <div class="d-grid mx-auto">
        <!-- <button @click="newCourse" class="btn btn-block btn-warning">Add Cource</button> -->
        <button class="btn btn-block btn-warning">Add Cource</button>
    </div>
</form>
    
    <div class="well">
        <p>Title : {{title}}</p> 
        <p>Image : {{image}}</p>
        <p>Category : {{category}}</p> 
        <p>Type Of Payment : {{typeOfPayment}}</p>
        <p>Published : {{published}}</p> 
        <p>my Tags : {{myTags}}</p> 
    </div>
    
</template>
<script>
export default {
    data() {
        return{
            title: '',
            image: '',
            category: '',
            typeOfPayment: 'free',
            categories: [
                {id: 1, name: 'FrontEnd'}, {id: 2 , name: 'BackEnd'}, {id: 3, name: 'FullStack'}, {id: 4, name: 'Mobile'},
            ],
            published: false,
            tags: ['Framework', 'Frontend', 'Backend', 'Javascript'],
            myTags: []
        }
    },
    methods: {
        newCourse() {
            //let title = this.$refs.title.value;
            //let image = this.$refs.image.value;
            let title = this.title;
            let image = this.image;
            if(title == "" || image == ""){
                return;
            }
            const course = {
                title,
                image,
                category: this.categories.find(category => category.id == this.category).name,
                tags: this.myTags
            }
            this.$emit('add', course)
            //this.$refs.title.value = "";
            //this.$refs.image.value = "";
        }
    },
}
</script>
<style lang="">
</style>
