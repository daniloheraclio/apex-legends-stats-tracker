<template>
  <div>
      Profile
  </div>
</template>

<script>
import axios from 'axios';
export default {
    name: 'Profile',
    data() {
        return {
            loading: false,
            error: null,
            profileData: null
        }
    },
    beforeCreate() {
        document.body.className = 'body-bg-ni-image';
    },
    created() {
        this.loading = true;
        try {
            const res = await axios.get(`http://localhost:5000/api/v1/profile/
            ${this.$route.params.platform}/
            ${this.$route.params.gamertag}`);

            this.profileData = res.data.data;
            console.log(this.profileData);

            this.loading = false;
        } catch (err) {
            this.loading = false;
            this.error.res.data.message;
        }
    }
}

</script>

<style>

</style>