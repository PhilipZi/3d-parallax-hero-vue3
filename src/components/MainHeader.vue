<template>
  <div class="hide">
    <nav>
      <img src="../assets/img/logo.png" alt="Travelo" class="logo" />
      <ul>
        <li>
          <a href="#">Login</a>
        </li>
        <li>
          <a href="#">Sign Up</a>
        </li>
        <li class="search">
          <a href="#">
            <font-awesome-icon icon="fa-solid fa-magnifying-glass" />
          </a>
        </li>
        <li class="hamburger">
          <a href="#">
            <div class="bar" />
          </a>
        </li>
      </ul>
    </nav>
  </div>
</template>

<script setup></script>

<style scoped>
.hide {
  position: absolute;
  z-index: 9999;
  width: 100%;
  border-bottom: 1px solid rgba(255, 255, 255, 0, 1);
}
nav {
  max-width: 1400px;
  margin: 0 auto;
  padding: 0 2rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.logo {
  width: 100px;
}

ul {
  display: flex;
  list-style: none;
  align-items: center;
}

ul a {
  text-decoration: none;
  color: #fff;
  padding: 0 1.5rem;
  text-transform: uppercase;
  font-weight: 300;
  font-size: 0.83rem;
}

.search a {
  font-size: 1.05rem;
  padding: 0 3rem;
}

.hamburger {
  padding-left: 1.5rem;
}

.hamburger a {
  width: 37px;
  height: 37px;
  padding: 0;
  border-radius: 50%;
  display: flex;
  cursor: pointer;
  background-color: rgba(115, 115, 115, 0.7);
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  justify-content: center;
  align-items: center;
}

.hamburger .bar {
  position: relative;
  width: 52%;
  height: 1.3px;
  background-color: #fff;
  border-radius: 2px;
}
.hamburger .bar::before,
.hamburger .bar::after {
  content: "";
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  width: 60%;
  height: 100%;
  background-color: inherit;
  border-radius: 2px;
}
.hamburger .bar::before {
  top: -4.7px;
}
.hamburger .bar::after {
  top: 4.7px;
}

@media (max-width: 725px) {
  nav {
    padding: 0 1rem;
  }

  .logo {
    width: 75px;
  }
  ul a {
    font-size: 0.73rem;
    padding: 0 0.9rem;
  }
  .search a {
    font-size: 0.85rem;
    padding: 0 1.8rem;
  }
  .hamburger {
    padding-left: 0.9rem;
  }

  .hamburger a {
    width: 30px;
    height: 30px;
  }
}
</style>
