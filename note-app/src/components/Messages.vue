<template>
  <div>
    <h1>{{ message }}</h1>
    <!-- <p>{{ message }}</p> -->
  </div>
</template>
<script>
export default {
  name: "Message",
 props:{
    message:{
      type: String,
      required: true
    }
 }
};
</script>
