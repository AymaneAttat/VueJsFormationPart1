<template lang="">
    <div class="row" v-if="showForm">
        <div class="col-md-6 mx-auto">
            <AddCourse @add="addCourse($event)" />
        </div>
    </div>
    <div class="row">
        <div class="col-md-11">
            <nav aria-label="breadcrumb">
                <slot></slot> 
            </nav>
            <h1>List of courses</h1>
        </div>
        <div class="col-md-1 text-right">
            <!--<slot name="button-right"></slot>-->
            <button @click="displayForm" class="btn btn-sm " :class="{'btn-success': !showForm, 'btn-dark': showForm}">{{showForm ? 'Close' : 'New'}}</button>
        </div>
    </div>
    <div class="row">
        <div class="col-md-4" v-for="course in courses">
            <OneCourse :course="course" @delete="deleteOneCourse($event)" />
            <!-- <OneCourse :title="course.title" :image="course.image" /> -->
        </div>
    </div>
    <teleport to='#alert' v-if="courseDeleted">
        <div class="alert alert-danger text-center">
            <strong>Course is deleted</strong>
        </div>
    </teleport>
    <teleport to='#alert' v-if="courseAdded">
        <div class="alert alert-success text-center">
            <strong>Course is added successfully</strong>
        </div>
    </teleport>
</template>
<script>
    import OneCourse from './OneCourse.vue'
    import AddCourse from './AddCourse.vue'
export default {
    components: {
        OneCourse,
        AddCourse
    },
    data () {
        return {
            courseDeleted: false,
            courseAdded: false,
            showForm: false,
            courses: [
                {
                    id: 1, title: 'Learn Laravel Advanced',category: 'Framewok', tags: [], image: 'https://process.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/resize=width:705/https://www.filepicker.io/api/file/aL2OXWSpTguVo0azLaPb'
                },
                {
                    id: 2, title: 'Learn Laravel Biginners',category: 'Framewok', tags: [], image: 'https://process.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/resize=width:705/https://www.filepicker.io/api/file/WPcaz1wUQA6AltnnGc7l'
                },
                {
                    id: 3, title: 'Learn VueJS 2',category: 'Framewok', tags: [], image: 'https://process.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/resize=width:705/https://www.filepicker.io/api/file/aMuzcOpzR4GX4HR7MNxg'
                },
                {
                    id: 4, title: 'Learn VueJS 3',category: 'Framewok', tags: [], image: 'https://process.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/resize=width:705/https://www.filepicker.io/api/file/k7Fltx5ITbu9LI6VtgTS'
                }
            ]
        }
    },
    methods: {
        deleteOneCourse(id) {
            //alert('delete from parent')
            //alert(id)
            this.courses = this.courses.filter(course => course.id != id);
            this.courseDeleted = true;
            setTimeout(() => {this.courseDeleted = false}, 3000)
        },
        addCourse(course) {
            this.courses.unshift(course);//push: ajoute en fin et unshift: ajoute au debut
            //autre method this.courses = [course, ...this.courses] pour ajouter au debut
            // this.courses = [...this.courses, course] pour ajouter au fin
            this.showForm = false;
            this.courseAdded = true;
            setTimeout(() => {this.courseAdded = false}, 3000)
        },
        displayForm() {
            this.showForm = !this.showForm;
        }
    },
}
</script>
<style scoped>
    h1{
        color: brown;
    }
</style>
