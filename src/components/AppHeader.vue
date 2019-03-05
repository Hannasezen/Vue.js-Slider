<template>
  <div class="header">
    <nav class="header__nav">
      <ul class="header__catalog-links">
        <li class="header__catalog-link">
          <a href="#">Women<span class="icon-keyboard_arrow_down"></span></a>
        </li>
        <li class="header__catalog-link">
          <a href="#">Men<span class="icon-keyboard_arrow_down"></span></a>
        </li>
        <li class="header__catalog-link">
          <a href="#">Kids<span class="icon-keyboard_arrow_down"></span></a>
        </li>
        <li class="header__catalog-link">
          <a href="#">Sale<span class="icon-keyboard_arrow_down"></span></a>
        </li>
      </ul>
      <div class="header__logo">
        <a href="#">LOGO</a>
      </div>
      <ul class="header__links">
        <li class="header__link"><a href="#">Sign UP</a></li>
        <li class="header__link"><a href="#">Account</a></li>
        <li class="header__link"><a href="#">Help<span class="icon-keyboard_arrow_down"></span></a></li>
        <li class="header__link header__link-cart"><a href="#"><span class="icon-shopping-cart"></span></a></li>
      </ul>
    </nav>
  </div>
</template>

<script>
export default {
  name: "AppHeader"
}
</script>

<style scoped>
ul {
  list-style: none;
}
.header {
  position: fixed;
  top: 0;
  left: 0;
  z-index: 2;
  display: flex;
  flex-direction: column;
  justify-content: center;
  width: 100%;
  min-height: 150px;
  padding: 0 2%;
  font-size: 16px;
  text-transform: uppercase;
  background-color: transparent;
  color: rgb(255, 255, 255);
  transition: background-color ease 0.3s;
}
.header:hover {
  background-color: rgb(255, 255, 255);
  color: rgb(0, 0, 0);
}
a {
  color: inherit;
}
.header__nav {
  display: flex;
  justify-content: space-between;
}
.header__catalog-links,
.header__links {
  display: flex;
  flex-grow: 1;
  align-items: center;
}
.header__catalog-links {
  display: flex;
  justify-content: flex-start;
}
.header__logo {
  flex-grow: 1;
}
.header__links {
  display: flex;
  justify-content: flex-end;
}
.header__link,
.header__catalog-link {
  white-space: nowrap;
  letter-spacing: 2px;
  font-weight: 700;
}
.header__catalog-link {
  margin-right: 4%;
}
.header__catalog-link a,
.header__link a {
  display: flex;
  align-items: center;
  position: relative;
  padding: 10px 0;
  border-bottom: 2px solid rgba(0, 0, 0, 0);
  transition: border-color ease 0.3s;
}
.header__catalog-link a:hover,
.header__link a:hover {
  border-color: rgb(0, 0, 0);
}
.icon-keyboard_arrow_down {
  margin-left: 6px;
  font-size: 30px;
  line-height: 0;
}
.header__link {
  margin-left: 4%;
}
.icon-shopping-cart {
  font-size: 30px;
  padding: 5px 0;
}
</style>
