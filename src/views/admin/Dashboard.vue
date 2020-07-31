<template>
  <div>
    <Navbar />
    <router-view :token="token" v-if="checkSuccess"/>
  </div>
</template>

<script>
import Navbar from '../../components/admin/Navbar.vue';

export default {
  name: 'Dashboard',
  components: {
    Navbar,
  },
  data() {
    return {
      token: '',
      checkSuccess: false,
    };
  },
  methods: {
    checkIn() {
      this.token = document.cookie.replace(/(?:(?:^|.*;\s*)token\s*=\s*([^;]*).*$)|^.*$/, '$1');
      // 預設帶入 token
      this.$http.defaults.headers.common.Authorization = `Bearer ${this.token}`;
      const api = `${process.env.VUE_APP_APIPATH}/api/auth/check`;
      this.$http.post(api, {
        api_token: this.token,
      })
        .then(() => {
          this.checkSuccess = true;
        })
        .catch(() => {
          console.log('尚未驗證');
          this.$router.push('/login');
        });
    },
  },
  created() {
    this.checkIn();
  },
};
</script>

<style>

</style>
