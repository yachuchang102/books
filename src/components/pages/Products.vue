<template>
  <div>
 <div class="text-right">
  <button>建立新產品</button>
 </div>
 <table class="table mt-4">
 <thead></thead>
 <tbody>
    <tr v-for="(item, key) in products" :key="item.id">
    <td>{{item.category}}</td>
    <td>{{item.title}}</td>
    </tr>
 </tbody>
 </table>
  </div>
</template>
<script>
export default {
  data (){
    return {
      products: [],
    };
  },
  methods: {
    getProducts() {
        const api = `${process.env.APIPATH}/api/${process.env.CUSTOMPATH}/admin/products`;
        const vm = this;
        this.$http.get(api).then((response) => { 
        console.log(response.data);
        vm.products = response.data.products;
        });
    },
  },
  created() {
    this.getProducts();
  }
}
</script>


