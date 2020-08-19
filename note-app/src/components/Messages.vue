<template>
  <div>
    <h1>Message componet!!- {{ message }}</h1>
    <!-- <p>{{ message }}</p> -->
  </div>
</template>
<script>
export default {
 props:{
    message:{
      type: String,
      required: true
    }
 }
};
</script>
