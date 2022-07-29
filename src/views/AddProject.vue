<template>
    <h1>Add Project</h1>
  <form>
        <label for="">Project Title</label>
        <input type="text">
        <label for="">Project Detail</label>
        <input type="text">
        <button>Add Project</button>
  </form>
</template>

<script>
export default {

}
</script>

<style>
form{
    background: white;
    padding: 20px;
    border-radius: 10px;
}
label{
    display: block;
    color:#aaa;
    text-transform: uppercase;
    font-size: 14px;
    font-weight: bold;
    letter-spacing: 1px;
    margin: 20px 0 10px 0;
}
input{
    width: 100%;
    padding: 10px;
    border: 0;
    border-bottom: 1px solid #aaa;
    box-sizing: border-box;
    
}
textarea{
    border: 1px solid #aaa;
    padding: 10px;
    width: 100%;
    box-sizing:border-box;
    height: 100px;
}
form button{
    font-size: 15px;
    display: block;
    margin:20px auto 0;
    background: #00ce89;
    color:white;
    padding: 12px;
    border: none;
    border-radius: 8px;
}
</style>