<template>
  <Tutorial/>
</template>


<script>


function getMeta($http) {
  return $http.$get('http://6289226c7af826e39e690910.mockapi.io/api/v1/meta/1');
}

export default {
  data() {

     return {
       meta: {}
     }
  },
  async fetch() {
    this.meta = await fetch('https://6289226c7af826e39e690910.mockapi.io/api/v1/meta/1', {
      https: true
    }).then(res => res.json());
  },
  head() {
    console.log(this.meta);
    return {
      title: this.meta.title,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: this.meta.description
        }
      ],
    }

  }
}
</script>
