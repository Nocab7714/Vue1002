<template>
  <div>
    <!-- 可以成功渲染資料 -->
    <div>
      成功渲染 products 第一筆陣列資料:
      <p>{{ products[0] }}</p>
    </div>
    <div>
      <!-- 可以成功透過 v-model 綁定資料 -->
      <label for="product01">綁定 v-model 第一筆資料</label>
      <input id="product01" type="text" v-model="products[0]" />
    </div>
    <!-- 會爆錯 Uncaught (in promise) TypeError: Cannot read properties of undefined (reading 'category') -->
    <div>
      <!-- <p>無法渲染 products 第一筆資料的 category 屬性 {{ products[0].category }}</p> -->
    </div>
    <div>
      <!-- 無法透過 v-model 綁定資料 -->
      <!-- <label for="product01">綁定 v-model 第一筆資料</label>
      <input id="product01" type="text" v-model="products[0].category" /> -->
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      products: {}
    }
  },
  methods: {
    getProducts() {
      this.$http
        .get(`https://vue3-course-api.hexschool.io/v2/api/peihanwang-hexschool/products/all`)
        .then((res) => {
          console.log(res)
          this.products = res.data.products
          // console.log(this.products)
        })
        .catch((err) => {
          console.log(err)
        })
    }
  },
  mounted() {
    this.getProducts()
  }
}
</script>
