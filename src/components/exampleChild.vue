<template>
    <div>
        <div>
            <p class="center">Example child</p>
        </div>
        <div>
            <p>Your prop: {{myString}}</p>
        </div>
    </div>
</template>

<script>
export default {
name:"exampleChild",
props:{
    myString:String,
    myArray:Array,
    myObject:Object
}
}
</script>

<style scoped>
div{
    height: 100px;
    width: 100px;
    background-color: aliceblue;
    margin: auto;
}
.center{
    text-align: center;
    padding:25px 0;
}
</style>

