<script>
import { mapActions, mapState } from "pinia";
import { useUserStore } from "../stores/user";

export default {
  name: "NavbarComponent",
  computed: {
    ...mapState(useUserStore, ["isLogin", "username", "userBill"]),
  },
  methods: {
    ...mapActions(useUserStore, ["logoutUser", "fetchEachUserBill"]),
  },
  created() {},
};
</script>

<template>
  <!-- Navbar Page -->
  <nav class="navbar navbar-expand-lg bg-light">
    <div class="container-fluid">
      <div class="container-fluid">
        <RouterLink to="/" class="navbar-brand">
          <img
            src="../../public/image/neighborhud.jpg"
            alt="Logo"
            width="30"
            height="24"
            class="d-inline-block align-text-top"
          />
          NeighborHud
        </RouterLink>
      </div>
      <div class="navbar-brand">
        <a v-if="isLogin" class="nav-link disabled" aria-current="page" href="#"
          >Hello, <span style="color: tomato">{{ username }}</span
          >!</a
        >
      </div>
      <div class="collapse navbar-collapse" id="navbarSupportedContent">
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li class="nav-item" v-if="isLogin === true">
            <RouterLink to="/" class="nav-link active" aria-current="page"
              >Home</RouterLink
            >
          </li>
          <li class="nav-item" v-if="isLogin === false">
            <RouterLink to="/register" class="nav-link">Register</RouterLink>
          </li>
          <li class="nav-item" v-if="isLogin === false">
            <RouterLink to="/login" class="nav-link">Login</RouterLink>
          </li>
          <li class="nav-item" v-if="isLogin === true">
            <RouterLink to="/bill" class="nav-link">MyBills</RouterLink>
          </li>
          <li class="nav-item" v-if="isLogin === true">
            <a class="nav-link" @click="logoutUser" style="cursor: pointer"
              >Logout</a
            >
          </li>
        </ul>
      </div>
    </div>
  </nav>
  <!-- End of Navbar Page -->
</template>
