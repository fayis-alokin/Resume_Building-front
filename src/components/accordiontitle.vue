<template>
    <div class="row1">
        <div class="main-heading">
            <h3>Resumes</h3>
        </div>
        <div class="line"></div>
        <div class="backlink">
            <a href="">Back to home</a>
        </div>
        <div class="subheading">
            <h5>Create Resume Content</h5>
        </div>
    </div>
</template>

<script>
export default{
    name : 'SubHeading'
}
</script>

<style>
.row1{
    padding: 20px;
    background-color: rgb(221, 209, 209);
}

.line{
    width: 100%;
    height: 1px;
    margin-top: 10px;
    margin-bottom: 10px;
}
.backlink a{
    text-decoration: none;
    color: blue;
}
</style>