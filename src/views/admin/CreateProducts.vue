<template>
  <div class="mt-5">
    <div class="text-right mt-5">
      <button type="button" class="btn btn-primary" data-toggle="modal"
        @click="openModal('new')">建立新的產品
      </button>
    </div>
    <div class="mt-3">
      <table class="table">
        <thead>
          <tr>
            <th scope="col" width="120">分類</th>
            <th scope="col">產品名稱</th>
            <th scope="col" class="text-center" width="70">原價</th>
            <th scope="col" class="text-center" width="70">售價</th>
            <th scope="col" class="text-center" width="100">是否啟用</th>
            <th scope="col" class="text-center" width="130">編輯</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="item in products" :key="item.id">
            <th scope="row">{{item.category}}</th>
            <td>{{item.title}}</td>
            <td>${{item.origin_price}}</td>
            <td class="text-danger">
              <span v-if="item.price===item.origin_price">${{item.price}}</span>
              <span v-else class="text-danger">${{item.price}}</span>
            </td>
            <td>
              <span v-if="item.enabled" class="text-success">啟用</span>
              <span v-else>不啟用</span>
            </td>
            <td class="d-flex">
              <button type="button" class="btn btn-sm btn-outline-primary mr-1"
                data-toggle="modal" @click="openModal('edit',item)">編輯</button>
              <button type="button" class="btn btn-sm btn-outline-danger mr-1"
                data-toggle="modal" @click="openModal('del',item)">刪除</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CreateProducts',
  props: ['token'],
  data() {
    return {
      products: [],
      tempProduct: {
        imageUrl: [],
      },
      pagination: {},
      tempOptions: {},
      status: {
        fileUploading: false,
      },
      isNew: true,
    };
  },
  methods: {
    getProducts() {
      const vm = this;
      const api = `${process.env.VUE_APP_APIPATH}/api/${process.env.VUE_APP_UUID}/admin/ec/products`;
      vm.$http.get(api)
        .then((res) => {
          vm.products = res.data.data;
          vm.pagination = res.data.meta.pagination;
        });
    },
    openModal() {
    },
  },
  created() {
    this.getProducts();
  },
};
</script>

<style>

</style>
